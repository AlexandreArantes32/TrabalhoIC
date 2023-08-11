# Day-to-Night utilizando CycleGAN
Trabalho de Inteligência Computacional feito no GoogleColab utilizando o modelo CycleGAN para transformar imagens de dia para noite e virse-versa.
Todos os resultados e datasets estão mantidos em um Drive.

## Compilação
Para compilar o projeto é necessário executar os comandos do arquivo `executável_principal.ipynb`.

1. O código irá acessar o Drive e procurar pela pasta do modelo, caso não exista, o repositório em questão será clonado.
```shell
!git clone https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix
```
<em>OBS.: este é o repositório do modelo utilizado (CycleGAN), sem treinamento prévio.</em>

2. Após clonar o repositório, mova a pasta `checkpoints` para dentro do arquivo criado `pytorch-CycleGAN-and-pix2pix`.

```shell
cd /content/drive/MyDrive/TrabalhoIC/pytorch-CycleGAN-and-pix2pix/checkpoints/day_night

# Este é o arquivo que mantém as últimas épocas do treinamento (195 e 200),
# além de <strong>dados técnicos como um log da loss</strong> de todas as épocas do treinamento.
```

3. Agora é possível colocar qualquer imagem de entrada e o modelo irá realizar a transformação para noite/dia.
* Coloque a imagem de teste em na pasta `testA` ou `testB` dependendo do caso (dia ou noite).
```shell
cd /content/drive/MyDrive/TrabalhoIC/datasets/day_night
```
* Execute o código do arquivo do Colab (`executável_principal.ipynb`) no tópico `Definindo os parâmetros de teste`.
```shell
#[...]
!python test.py --dataroot $dataset_path --name $night_to_da --model test --no_dropout --preprocess scale_width --load_size $load_size --crop_size $crop_size
```
<em>OBS.: os resultados de teste estarão localizados na pasta `./checkpoints`.</em>

## Observações
* Os resultados do modelo durante o treinamento/teste, além de vídeos gerados com este, estão todos no Drive.
  
```shell
cd /content/drive/MyDrive/TrabalhoIC/pytorch-CycleGAN-and-pix2pix/checkpoints/day_night/web/images
```

* Os resultados técnicos (métricas) do modelo durante o treinamento/teste, além dos parâmetros utilizados, estão localizados na pasta `./checkpoints/day_night`.
```shell
cd /content/drive/MyDrive/TrabalhoIC/pytorch-CycleGAN-and-pix2pix/checkpoints/day_night/
!ls
# train_opt.txt
# test_opt.txt
# loss_log.txt
```

* O dataset (dia/noite) utilizado para fazer o treinamento/teste está na pasta raiz do Drive.
```shell
cd /content/drive/MyDrive/TrabalhoIC/dataset
```
