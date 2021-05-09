# Multiclass-Segmentation-in-UNet
A segmentation task via UNet architecture of classifying pixels into particularly 3 categories of pixels: Background, foreground and the edges.

Model Features :

- It was trained on 1024 images for 25 epochs and 256 images for validation. 

- I have used dice_coef_loss function which i found performed better than categorical_crossentropy here, it achieved a somewhat okayish validation accuracy of 81%, i think with more model tweaks we can reach upto 85% but not more(reason mentioned in Issues section)

- specifically I have made some last layer modifications to improve performance, changes will be shown in comments

Model Issues :

- I have trained it for 45 epochs and mostly it achieves accuracy around 83% but not more, also the model maybe stops learning after maybe 30-35 epochs(you can see the uploaded plot for 45 epochs). Maybe a change of loss function could trigger a better performance because,  

- I can't test this model with sparse_categorical_crossentropy as a loss function because it needs to pass the masks as a dimension of (1, 256, 256, 1) to the model which is prohibited by the input dimensions(1, 256, 256, 3) for the model but the tensorflow documentation implemetation of this model(link in the References) uses that loss function and is pretty successful, so if anyone can point out my fault, i will be really greatful.
 
- The tensorflow segmentation documentation has this same task as a segmentation example. They have used a pretrained CNN as an encoder, and a few little changes in decoder too in the architecture but have an accuracy of impressive 93-95% , though they have trained on more images and for more epochs

- In the loss function and accuracy graph the validation loss/accuracy though gradually descends/ascends but there have been inconsistent breaks in their graphs which i don't know if is natural but i feel it shouldn't be, if anyone lightens me up on this will be really greatful.

References :

- I used the popular Oxford-IIIT pet dataset : https://www.kaggle.com/tanlikesmath/the-oxfordiiit-pet-dataset

- My code architecture was heavily influenced from here : https://github.com/zhixuhao/unet, https://www.tensorflow.org/tutorials/images/segmentation

- conceptually this page was really helpful : https://glassboxmedicine.com/2020/01/21/segmentation-u-net-mask-r-cnn-and-medical-applications/#:~:text=In%20instance%20segmentation%2C%20each%20pixel,be%20used%20for%20instance%20segmentation.531


Note that as of now github doesn't render notebooks properly so you can take the links of these notebooks(just open the notebooks above abd copy the link in the address bar) and paste it in [nbviewer](https://nbviewer.jupyter.org/) searchbar
