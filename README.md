# animal_classification_k210
Um classificador de 5 classes de animais usando a plataforma aXeleRate, a placa MaixBit e a rede neural MobileNet.

# Visão Geral
O projeto consiste em treinar uma rede neural(MobileNet) usando nossos próprios dados, nesse caso vou usar um dataset que possui vários tipos de animais, para reduzir o tempo de treinamento usei apenas 5 animais(borboleta, cachorro, cavalo, elefante e gato), o dataset usado pode ser encontrado no [kaggle](https://www.kaggle.com/dskagglemt/animal-classification-mobilenetv2-80). Eu separei o dataset em treino e validação, e dentro dessas duas pastas temos uma pasta para cada animal.

Com o dataset pronto usei o exemplo de classificação da biblioteca [aXeleRate](https://github.com/AIWintermuteAI/aXeleRate) que basicamente combina algumas arquiteturas de redes neurais, treina elas com base nos dados fornecidos e, mais importante, converte para o modelo que o acelerador de redes neurais(KPU) da placa usa, podendo assim usar esse tipo de modelo na nossa placa, o processo de conversão é algo do tipo: h5 -> TFlite -> kmodel. Os parâmetros de configuração do treinamento e uso estão explicados no github do projeto. O treinamento foi feito usando no [Google Colab](https://colab.research.google.com/drive/1KqqEgZtWPoJd-EgjODVSzZZhNa5dr2-6?usp=sharing).

Com o modelo criado usamos a ferramenta [kFlash](http://www.iotneuron.com/2019/09/27/upgrading-the-firmware-on-sipeed-maix-bit/) para gravar o modelo no endereço de memória apropriado. Com isso podemos usar o script em python para testar se o modelo funciona, e após testado podemos [gravar](https://cn.maixpy.sipeed.com/maixpy/en/get_started/get_started_upload_script.html) o script(inference.py) na memória da nossa placa e rodar ela usando um powerbank.

![image](https://user-images.githubusercontent.com/74123993/125169891-ab3f9100-e182-11eb-9ada-3396606ae559.png)

O modelo foi testado com dois gatos na "vida real" e os outros animais foram testados usando imagens da internet(infelizmente não tenho nenhum elefante por aqui):

# Testes

## Gatos na "vida real"

![image](https://user-images.githubusercontent.com/74123993/125169682-b2b26a80-e181-11eb-83b8-9e0580d45c27.png)

![image](https://user-images.githubusercontent.com/74123993/125169741-eab9ad80-e181-11eb-9884-47fa584e0c94.png)

![image](https://user-images.githubusercontent.com/74123993/125169718-d8d80a80-e181-11eb-8f23-a7cc2d92640c.png)

## Fotos de gatos na internet

![image](https://user-images.githubusercontent.com/74123993/125311101-8a557800-e309-11eb-865d-c76432117d28.png)
![image](https://user-images.githubusercontent.com/74123993/125311121-8e819580-e309-11eb-924f-f03160d44da9.png)
![image](https://user-images.githubusercontent.com/74123993/125311080-86295a80-e309-11eb-8345-0ea9593b05dc.png)

## Fotos de borboletas na internet

![image](https://user-images.githubusercontent.com/74123993/125311269-aa853700-e309-11eb-9568-4d6e8707642b.png)
![image](https://user-images.githubusercontent.com/74123993/125311377-bec93400-e309-11eb-8571-d2428c2bf457.png)
![image](https://user-images.githubusercontent.com/74123993/125311336-b83abc80-e309-11eb-85d7-7b83d26d115e.png)


## Fotos de cachorros na internet
![image](https://user-images.githubusercontent.com/74123993/125311238-a2c59280-e309-11eb-8a74-2a429dd02be0.png)
![image](https://user-images.githubusercontent.com/74123993/125311250-a5c08300-e309-11eb-951b-dfdba246272e.png)
![image](https://user-images.githubusercontent.com/74123993/125311225-9fcaa200-e309-11eb-84fb-3de09002c8e1.png)


## Fotos de cavalos na internet

![image](https://user-images.githubusercontent.com/74123993/125311477-d1436d80-e309-11eb-9535-a91cf21f11b3.png)
![image](https://user-images.githubusercontent.com/74123993/125312183-6fcfce80-e30a-11eb-9f05-616051f89b75.png)
![image](https://user-images.githubusercontent.com/74123993/125312164-6cd4de00-e30a-11eb-90d4-5e5b85286903.png)

## Fotos de elefantes na internet

![image](https://user-images.githubusercontent.com/74123993/125311422-c688d880-e309-11eb-9680-7fb738624ef0.png)
![image](https://user-images.githubusercontent.com/74123993/125311453-cc7eb980-e309-11eb-992f-4ab176704de3.png)
![image](https://user-images.githubusercontent.com/74123993/125311436-c983c900-e309-11eb-9086-c6971b2d5ccc.png)


