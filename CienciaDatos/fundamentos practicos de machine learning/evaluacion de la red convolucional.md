# Evaluación de la red convolucional

predicted_label = np.argmax(predictions[i]), en este caso en predictions[i] nos retorna un array con las probabilidades de pertenecer a cada uno de los labels, es decir, la probabilidad de que sea cada prenda(bastaria que lo multipliques por 100 para sacar el porcentaje), por lo que la prediccion viene a ser la probabilidad maxima en ese array lo cual lo obtenemos con np.argmax que nos dara el index del valor maximo del array, entonces ya tendriamos el indice de la prediccion y bastaria con obtener el nombre de la prenda usando ese index en la lista de los nombres:(class_names[predicted_label])

Les adjunto la copia de mí código tiene una variante que hace más legible el código.

```
import tensorflow as tf
import numpy as np
import matplotlib.pyplot as plt

from tensorflow import keras

fashion_mnist = keras.datasets.fashion_mnist

(train_images, train_labels), (test_images, test_labels) = fashion_mnist.load_data()

train_images.shape

class_name = ['T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat', 'Sandal', 'Shirt', 'Sneaker', 'Bag', 'Ankle boot']

plt.figure()
plt.imshow(train_images[100])
plt.grid(True)

train_images = train_images / 255.0
test_images = test_images / 255.0

%matplotlib inline

plt.figure(figsize=(10, 10))
for i in range(25):
  plt.subplot(5, 5, i + 1)
  plt.xticks([])
  plt.yticks([])

  plt.grid(False)

  plt.imshow(train_images[i], cmap=plt.cm.binary)
  plt.xlabel(class_name[train_labels[i]])

model = keras.Sequential([
                          keras.layers.Flatten(input_shape=(28, 28)),
                          keras.layers.Dense(128, activation=tf.nn.relu),
                          keras.layers.Dense(10, activation=tf.nn.softmax)
])

model.compile(
    optimizer=tf.train.AdamOptimizer(), 
    loss = 'sparse_categorical_crossentropy',
    metrics = ['accuracy']
)

model.fit(train_images, train_labels, epochs=5)

test_loss, test_acc = model.evaluate(test_images, test_labels)

print('')
print('Loss:', test_loss)
print('Accuracy:', test_acc)

predictions = model.predict(test_images)

%matplotlib inline

plt.figure(figsize=(10, 10))
for i in range(25):
  plt.subplot(5, 5, i + 1)
  plt.xticks([])
  plt.yticks([])

  plt.grid(False)

  plt.imshow(test_images[i], cmap=plt.cm.binary)

  predicted_label = np.argmax(predictions[i])
  true_label = test_labels[i]
  
  if predicted_label == true_label:
    color = 'yellow'
  else:
    color = 'red' 

  etiqueta = class_name[predicted_label] + '(' + class_name[true_label] + ')'
  plt.xlabel(etiqueta).set_color(color)

```