# Implementation of ResNet 50 model

- Implemented 'Identity_block' and 'Convolutional_block' which are two important components of the ResNet-50 model.
- In 'Identity_block', the shape of 'X_shortcut' is the same as the shape of the output of the 'Identity_block' which is 'X'.
- In 'Convolutional_block', 'X_shortcut' passes through a convolutional layer and the dimensions change so as to match the shape of the output of the 'Convolutional_block' but this is a linear transformation as there is no activation function.
- The 'Identity_block' acts as a identity function. The 'Convolutional_block' doesn't exactly act as a identity function as it linearly transforms the 'X_shortcut' but note that this is just linear transformation and there is no non-linear activation function and hence no non-linear transformation.
- Both the 'identity_block' and 'Convolutional_block' facilitates the training of deeper networks by maintaining stronger gradient flows, even when the dimensions change in the case of 'Convolutional_block'.

- The details of the ResNet-50 model are as below :-

- Zero-padding pads the input with a pad of (3,3)
- Stage 1:
  - The 2D Convolution has 64 filters of shape (7,7) and uses a stride of (2,2).
  - BatchNorm is applied to the 'channels' axis of the input.
  - MaxPooling uses a (3,3) window and a (2,2) stride.

- Stage 2:
  - The convolutional block uses three sets of filters of size [64,64,256], "f" is 3, and "s" is 1.
  - The 2 identity blocks use three sets of filters of size [64,64,256], and "f" is 3.

- Stage 3:
  - The convolutional block uses three sets of filters of size [128,128,512], "f" is 3 and "s" is 2.
  - The 3 identity blocks use three sets of filters of size [128,128,512] and "f" is 3.

- Stage 4:
  - The convolutional block uses three sets of filters of size [256, 256, 1024], "f" is 3 and "s" is 2.
  - The 5 identity blocks use three sets of filters of size [256, 256, 1024] and "f" is 3.

- Stage 5:
  - The convolutional block uses three sets of filters of size [512, 512, 2048], "f" is 3 and "s" is 2.
  - The 2 identity blocks use three sets of filters of size [512, 512, 2048] and "f" is 3.

- The 2D Average Pooling uses a window of shape (2,2).
- The 'flatten' layer doesn't have any hyperparameters.
- The Fully Connected (Dense) layer reduces its input to the number of classes using a softmax activation.
