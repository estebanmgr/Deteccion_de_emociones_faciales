# Deteccion_de_emociones_faciales

En este proyecto creé y entrené una red neuronal para la detección de emociones faciales, para esto utilizé la transferencia de conocimientos de una red neuronal pre entrenada y la modifiqué para que se ajustara al caso de estudio. Esto puede ser de utilidad para las personas que deseen subir una foto y detectar emociones de las personas que aparecen en ella, también puede servir como base para utilizarlo en algun filtro de alguna red social.

Logré que el modelo predijese con una precisión del 85% en 15 epocas gracias a la transferencia de conocimiento de un modelo pre entrenado de la librería de keras.preprocessing y ajustandola muy poco, para la mayoría de los casos este porcentaje de acierto será más que necesario para detectar las emociones. El nombre de la red utilizada fue la de "MobileNetV2".

## Recursos y códiigo utilizado 
**Versión de Python:** 3.7  
**Versión de Tensorflow:** 2.5.0  
**Paquetes:** pandas, numpy, sklearn, matplotlib, seaborn, tensorflow, keras, cv2.

# Explicación de datos utilizados
El dataset consta de 35887 imagenes divididas en 7 categorías y a su vez dividido en conjunto de entrenamiento y evaluación (28709 y 7178 imagenes respectivamente)

Las 7 cateorías son las siguientes:
Angry (958 para test y 3995 para train)
Disgust (111 para test y 436 para train)
Fear (1024 para test y 4097 para train)
Happy (1774 para test y 7215 para train)
Neutral (1233 para test y 4965 para train)
Sad (1247 para test y 4830 para train)
Surprise (831 para test y 3171 para train)
![alt text](https://github.com/estebanmgr/Deteccion_de_emociones_faciales/blob/main/Im%C3%A1genes/PrivateTest_1161501.jpg "Imagn de test 1")
![alt text](https://github.com/estebanmgr/Deteccion_de_emociones_faciales/blob/main/Im%C3%A1genes/PrivateTest_1769758.jpg "Imagn de test 2")
![alt text](https://github.com/estebanmgr/Deteccion_de_emociones_faciales/blob/main/Im%C3%A1genes/PrivateTest_2352334.jpg "Imagn de test 3")
![alt text](https://github.com/estebanmgr/Deteccion_de_emociones_faciales/blob/main/Im%C3%A1genes/PrivateTest_1791924.jpg "Imagn de test 3")

## Trabajando con las imagenes
Cada imagen esta compuesta por 48x48 pixeles y a color, como trabajaremos la transferencia de conocimiento de una red neuronal pre entrenada necesitamos reescalar dicha imagen a 224x224 pixeles mínimo.

Luego se procedió a aumentar la cantidad de imagenes a utilizar por el algoritmo aplicando la función de preprocesing del paquete de keras que te permite generar nuevas imagenes a partir de las ya existentes haciendo ciertas modificaciones a las orgiinales, en nuestro caso optamos por la modificación de los parametros "zoom" y "horizontal flip".

## Creando el modelo
Para esta ocasión trabajé la transferencia de conocimientos de una red neuronal pre entrenada haciendo ciertos ajustes a algunas capas ocultas y a la capa de salida para que pasara de tener 2 neuronas a 7 (una por cada emoción a detectar)

Luego entrené la red neuronal por 25 epocas (en lotes de 10 en 10 epocas por vez) utilizando el GPU de Google Colab, de esta manera no se consumen tantos recursos del ordenador, obteniendo una precisión de la red neuronal del 85%, porcentaje más que suficiente para la detección de la mayoría de emociones faciales.

## Utilizando el modelo
Para evaluar el modelo utilizamos imagenes descargadas de internet, de modo que nos aseguramos que la red no las ha visto antes.
![alt text](https://github.com/estebanmgr/Deteccion_de_emociones_faciales/blob/main/Im%C3%A1genes/Angry.jfif "Angry")
![alt text](https://github.com/estebanmgr/Deteccion_de_emociones_faciales/blob/main/Im%C3%A1genes/Fear.jfif "Fear")

y por último utilizamos el módulo de CV2 y haarcascade_frontalfacepara que nos permita acceder a la camara web de nuestro ordenador y poder detectar en tiempo real las emociones detectadas en los fotogramas que la camara captaba.
![alt text](https://github.com/estebanmgr/Deteccion_de_emociones_faciales/blob/main/Im%C3%A1genes/Realtime%20Felicidad.PNG "Real time felicidad")
![alt text](https://github.com/estebanmgr/Deteccion_de_emociones_faciales/blob/main/Im%C3%A1genes/Realtime%20neutral.PNG "Real time neutral")

## Area de mejora a futuro
* La red neuronal necesitaría entrenarse un poco más para poder obtener un mayor porcentaje de precisión, con un poco más de tiempo utilizando el GPU de Google Colab debería de quedar mejor entrenado el modelo.
* Modificar el código de haarcascade para que, ya que detecta multiples caras, el algoritmo sea capaz de detectar las emociones de todas las caras que detecta.
* Aplicar la misma modificación anterior para que cuando se detecte en la camara del ordenador más de una cara, el modelo sea capaz de detectar las emociones de todas las caras que detecte.




