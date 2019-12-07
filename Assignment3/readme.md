# Base model Accuracy

Epoch 50/50
390/390 [==============================] - 7s 18ms/step - loss: 0.3446 - acc: 0.8847 - val_loss: 0.5766 - val_acc: 0.8278
Model took 356.55 seconds to train

# My approach
I mainly used depthwise convolution with batch normalization and dropuot as suggested. I tried with stride 2 but results were not good, so stuck to 1.

With learning rate of 0.003 and drop out of 0.01, my training accuracy went up to 92%, however my validation accuracy was stuck at 74. I played around with various combinations of these values but results were almost the same.

As time was running out my last try was with learning rate 0.003 and drop out of 0.3, training accuracy went down to 81 while validation accuracy was 78.76. So submitting the same below.

# My model (Total params: 97,579)
dropout_rate = 0.3
model = Sequential()
model.add(BatchNormalization(input_shape=(32, 32, 3)))
#layer 1 
model.add(SeparableConv2D(64, (3, 3), input_shape=(32, 32, 3), strides=1)) # output channel size: 30 receptive field: 3
model.add(Activation('relu'))
model.add(BatchNormalization())
model.add(Dropout(dropout_rate))

#layer 2
model.add(SeparableConv2D(128, (3, 3))) # output channel size: 28 receptive field: 5
model.add(Activation('relu'))
model.add(BatchNormalization())
model.add(Dropout(dropout_rate))

#layer 3
model.add(SeparableConv2D(256, (3, 3))) # output channel size: 26 receptive field: 7
model.add(Activation('relu'))
model.add(BatchNormalization())
model.add(Dropout(dropout_rate))

#layer 4
model.add(SeparableConv2D(10, (1, 1))) # output channel size: 26 receptive field: 7 
model.add(Activation('relu'))


#layer 5
model.add(SeparableConv2D(64, (3, 3))) # output channel size: 24 receptive field: 9
model.add(Activation('relu'))
model.add(BatchNormalization())
model.add(Dropout(dropout_rate))

#layer 6
model.add(SeparableConv2D(128, (3, 3))) # output channel size: 22 receptive field: 11
model.add(Activation('relu'))
model.add(BatchNormalization())
model.add(Dropout(dropout_rate))

#layer 7
model.add(SeparableConv2D(256, (3, 3))) # output channel size: 20 receptive field: 13
model.add(Activation('relu'))
model.add(BatchNormalization())
model.add(Dropout(dropout_rate))

#layer 8
model.add(SeparableConv2D(10, (1, 1))) # output channel size: 20 receptive field: 13
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2,2))) # output channel size: 10 receptive field: 14

model.add(SeparableConv2D(10, (10, 10))) # output channel size: 1 receptive field: 32
model.add(Flatten())
model.add(Activation('softmax'))

#Compile the model

from keras.optimizers import Adam
from keras.callbacks import LearningRateScheduler
def scheduler(epoch, lr):
  return round(0.003 * 1/(1 + 0.319 * epoch), 10)
model.compile(loss='categorical_crossentropy', optimizer=Adam(lr=0.003), metrics=['accuracy'])

# Execution log

Epoch 1/50
390/390 [==============================] - 46s 117ms/step - loss: 1.6481 - acc: 0.3872 - val_loss: 1.5626 - val_acc: 0.4531
Epoch 2/50
390/390 [==============================] - 42s 108ms/step - loss: 1.2502 - acc: 0.5463 - val_loss: 1.1970 - val_acc: 0.5746
Epoch 3/50
390/390 [==============================] - 42s 109ms/step - loss: 1.0928 - acc: 0.6077 - val_loss: 1.2364 - val_acc: 0.5490
Epoch 4/50
390/390 [==============================] - 42s 108ms/step - loss: 1.0155 - acc: 0.6351 - val_loss: 1.0803 - val_acc: 0.6167
Epoch 5/50
390/390 [==============================] - 42s 108ms/step - loss: 0.9553 - acc: 0.6588 - val_loss: 1.0523 - val_acc: 0.6267
Epoch 6/50
390/390 [==============================] - 42s 109ms/step - loss: 0.9132 - acc: 0.6723 - val_loss: 0.9937 - val_acc: 0.6547
Epoch 7/50
390/390 [==============================] - 42s 109ms/step - loss: 0.8797 - acc: 0.6854 - val_loss: 0.9258 - val_acc: 0.6669
Epoch 8/50
390/390 [==============================] - 42s 108ms/step - loss: 0.8479 - acc: 0.6964 - val_loss: 0.9132 - val_acc: 0.6829
Epoch 9/50
390/390 [==============================] - 42s 108ms/step - loss: 0.8210 - acc: 0.7051 - val_loss: 1.0100 - val_acc: 0.6538
Epoch 10/50
390/390 [==============================] - 42s 108ms/step - loss: 0.7974 - acc: 0.7165 - val_loss: 0.8736 - val_acc: 0.7000
Epoch 11/50
390/390 [==============================] - 42s 108ms/step - loss: 0.7782 - acc: 0.7229 - val_loss: 0.8249 - val_acc: 0.7046
Epoch 12/50
390/390 [==============================] - 42s 108ms/step - loss: 0.7577 - acc: 0.7298 - val_loss: 0.9210 - val_acc: 0.6914
Epoch 13/50
390/390 [==============================] - 42s 108ms/step - loss: 0.7458 - acc: 0.7344 - val_loss: 0.7870 - val_acc: 0.7230
Epoch 14/50
390/390 [==============================] - 42s 108ms/step - loss: 0.7241 - acc: 0.7433 - val_loss: 0.8093 - val_acc: 0.7183
Epoch 15/50
390/390 [==============================] - 42s 108ms/step - loss: 0.7130 - acc: 0.7492 - val_loss: 0.8443 - val_acc: 0.7032
Epoch 16/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6986 - acc: 0.7537 - val_loss: 0.7524 - val_acc: 0.7304
Epoch 17/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6874 - acc: 0.7567 - val_loss: 0.8259 - val_acc: 0.7142
Epoch 18/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6828 - acc: 0.7569 - val_loss: 0.8084 - val_acc: 0.7200
Epoch 19/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6682 - acc: 0.7637 - val_loss: 0.7531 - val_acc: 0.7418
Epoch 20/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6613 - acc: 0.7644 - val_loss: 0.7042 - val_acc: 0.7557
Epoch 21/50
390/390 [==============================] - 42s 109ms/step - loss: 0.6510 - acc: 0.7734 - val_loss: 0.7036 - val_acc: 0.7563
Epoch 22/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6457 - acc: 0.7743 - val_loss: 0.7311 - val_acc: 0.7501
Epoch 23/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6398 - acc: 0.7759 - val_loss: 0.6766 - val_acc: 0.7690
Epoch 24/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6329 - acc: 0.7762 - val_loss: 0.7388 - val_acc: 0.7505
Epoch 25/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6263 - acc: 0.7810 - val_loss: 0.7298 - val_acc: 0.7497
Epoch 26/50
390/390 [==============================] - 42s 109ms/step - loss: 0.6192 - acc: 0.7835 - val_loss: 0.7286 - val_acc: 0.7514
Epoch 27/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6047 - acc: 0.7870 - val_loss: 0.7017 - val_acc: 0.7567
Epoch 28/50
390/390 [==============================] - 42s 108ms/step - loss: 0.6119 - acc: 0.7837 - val_loss: 0.7171 - val_acc: 0.7598
Epoch 29/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5999 - acc: 0.7910 - val_loss: 0.6914 - val_acc: 0.7614
Epoch 30/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5895 - acc: 0.7932 - val_loss: 0.7226 - val_acc: 0.7493
Epoch 31/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5913 - acc: 0.7942 - val_loss: 0.8132 - val_acc: 0.7322
Epoch 32/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5860 - acc: 0.7931 - val_loss: 0.7004 - val_acc: 0.7598
Epoch 33/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5819 - acc: 0.7954 - val_loss: 0.6720 - val_acc: 0.7711
Epoch 34/50
390/390 [==============================] - 42s 109ms/step - loss: 0.5755 - acc: 0.7973 - val_loss: 0.6442 - val_acc: 0.7829
Epoch 35/50
390/390 [==============================] - 42s 109ms/step - loss: 0.5731 - acc: 0.7985 - val_loss: 0.6954 - val_acc: 0.7726
Epoch 36/50
390/390 [==============================] - 42s 109ms/step - loss: 0.5645 - acc: 0.8001 - val_loss: 0.6731 - val_acc: 0.7730
Epoch 37/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5652 - acc: 0.8014 - val_loss: 0.6560 - val_acc: 0.7774
Epoch 38/50
390/390 [==============================] - 42s 109ms/step - loss: 0.5607 - acc: 0.8044 - val_loss: 0.6514 - val_acc: 0.7792
Epoch 39/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5574 - acc: 0.8051 - val_loss: 0.6390 - val_acc: 0.7873
Epoch 40/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5557 - acc: 0.8045 - val_loss: 0.7304 - val_acc: 0.7564
Epoch 41/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5486 - acc: 0.8080 - val_loss: 0.6547 - val_acc: 0.7825
Epoch 42/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5469 - acc: 0.8087 - val_loss: 0.6672 - val_acc: 0.7685
Epoch 43/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5420 - acc: 0.8100 - val_loss: 0.6436 - val_acc: 0.7876
Epoch 44/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5411 - acc: 0.8105 - val_loss: 0.6589 - val_acc: 0.7740
Epoch 45/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5346 - acc: 0.8116 - val_loss: 0.6358 - val_acc: 0.7864
Epoch 46/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5343 - acc: 0.8125 - val_loss: 0.7014 - val_acc: 0.7643
Epoch 47/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5269 - acc: 0.8164 - val_loss: 0.6848 - val_acc: 0.7698
Epoch 48/50
390/390 [==============================] - 42s 109ms/step - loss: 0.5319 - acc: 0.8138 - val_loss: 0.6875 - val_acc: 0.7689
Epoch 49/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5163 - acc: 0.8185 - val_loss: 0.6404 - val_acc: 0.7866
Epoch 50/50
390/390 [==============================] - 42s 108ms/step - loss: 0.5219 - acc: 0.8186 - val_loss: 0.6623 - val_acc: 0.7763
Model took 2116.27 seconds to train

Accuracy on test data is: 77.63
