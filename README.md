import tensorflow as tf
import numpy as np

from tensorflow.keras.layers import Dense, Flatten
from tensorflow.keras.models import Sequential
from tensorflow.keras.callbacks import ModelCheckpoint

fashion_mnist = tf.keras.datasets.fashion_mnist
(x_train, y_train), (x_valid, y_valid) = fashion_mnist.load_data()

  
x_train = x_train / 255.0
x_valid = x_valid / 255.0

tf.keras.backend.set_floatx('float64')

x = Flatten(input_shape=(28, 28))
print(x(x_train).shape)

model = Sequential([
    # Flatten으로 shape 펼치기
    Flatten(input_shape=(28, 28)),
    # Dense Layer
    Dense(1024, activation='relu'),
    Dense(512, activation='relu'),
    Dense(256, activation='relu'),
    Dense(128, activation='relu'),
    Dense(64, activation='relu'),
    # Classification을 위한 Softmax
    Dense(10, activation='softmax'),
])

model.summary()

model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['acc'])
checkpoint_path = "my_checkpoint.ckpt"
checkpoint = ModelCheckpoint(filepath=checkpoint_path,
                             save_weights_only=True,
                             save_best_only=True,
                             monitor='val_loss',
                             verbose=1)
model.fit(x_train, y_train,
                    validation_data=(x_valid, y_valid),
                    epochs=20,
                    callbacks=[checkpoint],
                   )
# checkpoint 를 저장한 파일명을 입력합니다.
model.load_weights(checkpoint_path)

"""## 학습한 후 검증하고 싶다면?"""

model.evaluate(x_valid, y_valid) 

