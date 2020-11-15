# Style-transfer-using-Pytorch

This repository is about making style transfer project using Pytorch.

Inputs are content and style images and we need to make target image which has content as content image and style as style image.

Here I used pretrained VGG-19 network which has 5 stacks of convolutional layers and ReLU layer. After each stack is MaxPool layer. 
To measure style, we calculate features gram matrix.

Content and target images have similar features from pretrained VGG-19. Style and target images have similar gram matrices of features. 
We calculate losses

<img src="https://render.githubusercontent.com/render/math?math=loss=\frac{1}{2}\sum(T_c-C_c)^2"> ,

where <img src="https://render.githubusercontent.com/render/math?math=T_c"> are features from target image from selected layers and <img src="https://render.githubusercontent.com/render/math?math=C_c"> are features from content image from selected layers.

<img src="https://render.githubusercontent.com/render/math?math=style loss=a\sum{_i} w_i(T_{s,i}-S_{s,i})^2"> ,

where <img src="https://render.githubusercontent.com/render/math?math=T_{s,i}"> is gram matrix of target image of i-th feature and <img src="https://render.githubusercontent.com/render/math?math=S_{s,i}"> is gram matrix of style image of i-th feature.
Total loss is

<img src="https://render.githubusercontent.com/render/math?math=total loss=\alpha *content loss+ \beta*style loss"> ,

<img src="https://render.githubusercontent.com/render/math?math=\alpha=1, \beta=10^6, learning rate=0.005, number of epochs=10000"> 

Content image is 'bg.jpg' and style image is 'impresionism.jpg'. In folder style_transfer there are results of target image during training on every 200th epoch.

![Content image](https://github.com/tijanavukovic1/Style-transfer-using-Pytorch/blob/main/bg.jpg?raw=true) + ![Style image](https://github.com/tijanavukovic1/Style-transfer-using-Pytorch/blob/main/impresionism.jpg?raw=true)=![Target image](https://github.com/tijanavukovic1/Style-transfer-using-Pytorch/blob/main/image_new2399.jpg?raw=true)

