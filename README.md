# Style-transfer-using-Pytorch

This repository is about making style transfer project using Pytorch.

Inputs are content and style images and we need to make target image which has content as content image and style as style image.

Here I used pretrained VGG-19 network which has 5 stacks of convolutional layers and ReLU layer. After each stack is MaxPool layer. 
To measure style, we calculate features gram matrix.

Content and target images have similar features from pretrained VGG-19. Style and target images have similar gram matrices of features. 
We calculate losses
$$content loss=\frac{1}{2}\sum(T_c-C_c)^2$$,
where $T_c$ are features from target image from selected layers and $C_c$ are features from content image from selected layers.
$$style loss=a\sum{_i} w_i(T_s,i-S_s,i)^2$$,
where $T_s,i$ is gram matrix of target image of i-th feature and $S_s,i$ is gram matrix of style image of i-th feature.
Total loss is
$$total loss=\alpha *content loss+ \beta*style loss$$.

Here $\alpha=1, \beta=10^6$ and a is in range from 0 to 1 and it is higher for first layers.

To train style transfer I used Adam optimizer with learning rate 0.005 with 10000 epochs. 

Content image is 'jbg.jpg' and style image is 'impresionism.jpg'. In folder style_transfer there are results of target image during training on every 200th epoch.

![Content image](https://github.com/tijanavukovic1/Style-transfer-using-Pytorch/blob/main/bg.jpg?raw=true) + ![Style image](https://github.com/tijanavukovic1/Style-transfer-using-Pytorch/blob/main/impresionism.jpg?raw=true)=

