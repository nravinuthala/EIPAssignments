# Summary
Accuracy: 99.41

No. of parameters: 14608

Epoch No. in which accuracy crossed 99.4: 17

Used bias? : No


# Model Architecture
model.add(Convolution2D(8, 3, 3, activation='relu', use_bias=False, input_shape=(28,28,1))) # 26
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(Convolution2D(16, 3, 3, activation='relu', use_bias=False)) # 24
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(Convolution2D(10, 1, 1, activation='relu', use_bias=False)) # 24
model.add(MaxPooling2D(pool_size=(2, 2))) # 12

model.add(Convolution2D(16, 3, 3, activation='relu', use_bias=False)) # 10
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(Convolution2D(16, 3, 3, activation='relu', use_bias=False)) # 8
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(Convolution2D(32, 3, 3, activation='relu', use_bias=False)) # 6
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(Convolution2D(10, 3, 3, activation='relu', use_bias=False)) # 4
model.add(BatchNormalization())
model.add(Dropout(0.1))

model.add(Convolution2D(10, 4, 4, use_bias=False))
model.add(Flatten())
model.add(Activation('softmax'))

# Model Summary
Model: "sequential_34"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d_238 (Conv2D)          (None, 26, 26, 8)         72        
_________________________________________________________________
batch_normalization_160 (Bat (None, 26, 26, 8)         32        
_________________________________________________________________
dropout_157 (Dropout)        (None, 26, 26, 8)         0         
_________________________________________________________________
conv2d_239 (Conv2D)          (None, 24, 24, 16)        1152      
_________________________________________________________________
batch_normalization_161 (Bat (None, 24, 24, 16)        64        
_________________________________________________________________
dropout_158 (Dropout)        (None, 24, 24, 16)        0         
_________________________________________________________________
conv2d_240 (Conv2D)          (None, 24, 24, 10)        160       
_________________________________________________________________
max_pooling2d_46 (MaxPooling (None, 12, 12, 10)        0         
_________________________________________________________________
conv2d_241 (Conv2D)          (None, 10, 10, 16)        1440      
_________________________________________________________________
batch_normalization_162 (Bat (None, 10, 10, 16)        64        
_________________________________________________________________
dropout_159 (Dropout)        (None, 10, 10, 16)        0         
_________________________________________________________________
conv2d_242 (Conv2D)          (None, 8, 8, 16)          2304      
_________________________________________________________________
batch_normalization_163 (Bat (None, 8, 8, 16)          64        
_________________________________________________________________
dropout_160 (Dropout)        (None, 8, 8, 16)          0         
_________________________________________________________________
conv2d_243 (Conv2D)          (None, 6, 6, 32)          4608      
_________________________________________________________________
batch_normalization_164 (Bat (None, 6, 6, 32)          128       
_________________________________________________________________
dropout_161 (Dropout)        (None, 6, 6, 32)          0         
_________________________________________________________________
conv2d_244 (Conv2D)          (None, 4, 4, 10)          2880      
_________________________________________________________________
batch_normalization_165 (Bat (None, 4, 4, 10)          40        
_________________________________________________________________
dropout_162 (Dropout)        (None, 4, 4, 10)          0         
_________________________________________________________________
conv2d_245 (Conv2D)          (None, 1, 1, 10)          1600      
_________________________________________________________________
flatten_32 (Flatten)         (None, 10)                0         
_________________________________________________________________
activation_32 (Activation)   (None, 10)                0         
=================================================================
Total params: 14,608
Trainable params: 14,412
Non-trainable params: 196

# Model Training Log
Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
60000/60000 [==============================] - 23s 380us/step - loss: 0.2136 - acc: 0.9320 - val_loss: 0.0645 - val_acc: 0.9800
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
60000/60000 [==============================] - 11s 184us/step - loss: 0.0619 - acc: 0.9805 - val_loss: 0.0413 - val_acc: 0.9867
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
60000/60000 [==============================] - 11s 183us/step - loss: 0.0475 - acc: 0.9849 - val_loss: 0.0322 - val_acc: 0.9905
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
60000/60000 [==============================] - 11s 183us/step - loss: 0.0395 - acc: 0.9875 - val_loss: 0.0283 - val_acc: 0.9907
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
60000/60000 [==============================] - 11s 183us/step - loss: 0.0356 - acc: 0.9883 - val_loss: 0.0267 - val_acc: 0.9912
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
60000/60000 [==============================] - 11s 180us/step - loss: 0.0314 - acc: 0.9905 - val_loss: 0.0299 - val_acc: 0.9912
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
60000/60000 [==============================] - 11s 182us/step - loss: 0.0295 - acc: 0.9906 - val_loss: 0.0245 - val_acc: 0.9923
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
60000/60000 [==============================] - 11s 180us/step - loss: 0.0275 - acc: 0.9910 - val_loss: 0.0251 - val_acc: 0.9922
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
60000/60000 [==============================] - 11s 179us/step - loss: 0.0260 - acc: 0.9911 - val_loss: 0.0221 - val_acc: 0.9937
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
60000/60000 [==============================] - 11s 182us/step - loss: 0.0218 - acc: 0.9931 - val_loss: 0.0258 - val_acc: 0.9915
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
60000/60000 [==============================] - 11s 180us/step - loss: 0.0233 - acc: 0.9924 - val_loss: 0.0185 - val_acc: 0.9934
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
60000/60000 [==============================] - 11s 179us/step - loss: 0.0220 - acc: 0.9924 - val_loss: 0.0223 - val_acc: 0.9927
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
60000/60000 [==============================] - 11s 180us/step - loss: 0.0214 - acc: 0.9932 - val_loss: 0.0211 - val_acc: 0.9928
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
60000/60000 [==============================] - 11s 179us/step - loss: 0.0193 - acc: 0.9939 - val_loss: 0.0222 - val_acc: 0.9928
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
60000/60000 [==============================] - 11s 180us/step - loss: 0.0195 - acc: 0.9933 - val_loss: 0.0242 - val_acc: 0.9926
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
60000/60000 [==============================] - 11s 180us/step - loss: 0.0185 - acc: 0.9939 - val_loss: 0.0213 - val_acc: 0.9934
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
60000/60000 [==============================] - 11s 182us/step - loss: 0.0176 - acc: 0.9942 - val_loss: 0.0203 - val_acc: 0.9941
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
60000/60000 [==============================] - 11s 180us/step - loss: 0.0170 - acc: 0.9944 - val_loss: 0.0240 - val_acc: 0.9923
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
60000/60000 [==============================] - 11s 179us/step - loss: 0.0171 - acc: 0.9944 - val_loss: 0.0186 - val_acc: 0.9939
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
60000/60000 [==============================] - 11s 184us/step - loss: 0.0162 - acc: 0.9947 - val_loss: 0.0213 - val_acc: 0.9932
<keras.callbacks.History at 0x7f16851e1710>
