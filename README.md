# animal_classification_k210
Um classificador de 5 classes de animais usando a plataforma aXeleRate, a placa MaixBit e a rede neural MobileNet.

# Visão Geral
O projeto consiste em treinar uma rede neural(MobileNet) usando nossos próprios dados, nesse caso vou usar um dataset que possui vários tipos de animais, para reduzir o tempo de treinamento usei apenas 5 animais(borboleta, cachorro, cavalo, elefante e gato), o dataset usado pode ser encontrado no [kaggle](https://www.kaggle.com/dskagglemt/animal-classification-mobilenetv2-80). Eu separei o dataset em treino e validação, e dentro dessas duas pastas temos uma pasta para cada animal, esse dataset pode ser encontrado na pasta animal_class.

Com o dataset pronto usei o exemplo de classificação da biblioteca [aXeleRate](https://github.com/AIWintermuteAI/aXeleRate) que basicamente combina algumas arquiteturas de redes neurais, treina elas com base nos dados fornecidos e, mais importante, converte para o modelo que o acelerador de redes neurais(KPU) da placa usa, podendo assim usar esse tipo de modelo na nossa placa, o processo de conversão é algo do tipo: h5 -> TFlite -> kmodel. Os parâmetros de configuração do treinamento e uso estão explicados no github do projeto.

Com o modelo criado usamos a ferramenta [kFlash](http://www.iotneuron.com/2019/09/27/upgrading-the-firmware-on-sipeed-maix-bit/) para gravar o modelo no endereço de memória apropriado. Com isso podemos usar o script em python para testar se o modelo funciona, e após testado podemos [gravar](https://cn.maixpy.sipeed.com/maixpy/en/get_started/get_started_upload_script.html) o script na memória da nossa placa e rodar ela usando um powerbank.

![image](https://user-images.githubusercontent.com/74123993/125169891-ab3f9100-e182-11eb-9ada-3396606ae559.png)

O modelo foi testado com dois gatos na "vida real" e os outros animais foram testados usando imagens da internet(infelizmente não tenho nenhum elefante por aqui):

![image](https://user-images.githubusercontent.com/74123993/125169682-b2b26a80-e181-11eb-83b8-9e0580d45c27.png)

![image](https://user-images.githubusercontent.com/74123993/125169741-eab9ad80-e181-11eb-9884-47fa584e0c94.png)

![image](https://user-images.githubusercontent.com/74123993/125169718-d8d80a80-e181-11eb-8f23-a7cc2d92640c.png)


