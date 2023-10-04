# NumpyCNN-OCR
Minimal CNN for OCR from scratch in NumPy, covering architecture, training, backprop, and layer-wise feature visualization.

### Architecture
A simple architecture based on a very popular network called the LeNet (http://ieeexplore.ieee.org/abstract/document/726791/)

Input - 1×28×28
Convolution - k = 5, s = 1, p = 0, 20 filters
ReLU
MAXPooling - k=2, s=2, p=0
Convolution - k = 5, s = 1, p = 0, 50 filters
ReLU
MAXPooling - k=2, s=2, p=0
Fully Connected layer - 500 neurons
ReLU
Loss layer

### Data structures
We define four main data structures to help us implement the Convolutional Neural Network which are explained in the following section. Each layer is defined by a data structure, where the field type determines the type of the layer. This field can take the values of DATA, CONV, POOLING, IP, RELU, LOSS which correspond to data, convolution, max-pooling layers, inner-product/ fully connected, ReLU and Loss layers respectively. The fields in each of the layer will depend on the type of layer.

The input is passed to each layer in a structure with the following fields.
height - height of the feature maps
width - width of the feature maps
channel - number of channels / feature maps
batch size - batch size of the network.
data - stores the actual data being passed between the layers. This is always supposed to be of the size [ height × width × channel, batch size ], with structure changes (im2col) in some parts for computational efficiency.
diff - Stores the gradients with respect to the data, it has the same size as data. Each layer’s parameters are stored in a structure param.
w - weight matrix of the layer
b - bias

param_grad is used to store the gradients coupled at each layer with the following properties:							
w - stores the gradient of the loss with respect to w.
b - stores the gradient of the loss with respect to the bias term.

