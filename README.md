# KMHCNet
A Colorization Model Using a UNet++ Architecture Based Autoencoder with ResNet Pretrained Encoder

## Abstract
We propose a novel approach to solving the colorization problem which aims to colorize a gray-scale image by using UNet++ Auto-Encoder where the Encoder is compiled using ResNet. This article also shows the effect of each variant of ResNet as well as InceptionResnetV2 and EfficientNet as potential encoders in the network. To show the advantages of using UNet++, we also created some variants replacing the UNet++ with traditional UNet. Thus our article proposes a deep convolutional network framework called KMHCNet which contains multiple variants of the network each having different combination of architecture, encoder, color-space in which to calculate loss on, embedding used before calculating loss and loss function used. Each variants provides us a different overall network with their own advantages and flaws. In this article we showed the results of 16 variants of the KMHCNet after training them on the same Dataset for differing number of epochs. Experiments have shown that most variants of our proposed network can provide pretty good result. To our best apprehension, no prevailing papers or research studies have mentioned this approach of using a segmentation model with variant encoders and using MS-SSIM as a potential loss function to colorize gray-scale images.

### KMHCNet Variant Structure
|    Variant 	| Architecture 	|           Encoder 	| ColorSpace_for_Loss_Calculation 	|   Loss_Function 	| Embedding 	|
|-------------|---------------|---------------------|-----------------------------------|-------------------|-------------|
|  KMHCNet_1 	|       Unet++ 	|         Resnet152 	|                             LAB 	|         MS-SSIM 	|      None 	|
|  KMHCNet_2 	|       Unet++ 	|          Resnet50 	|                             LAB 	|         MS-SSIM 	|      None 	|
|  KMHCNet_3 	|       Unet++ 	|         Resnet152 	|                             RGB 	|         MS-SSIM 	|      None 	|
|  KMHCNet_4 	|       Unet++ 	|          Resnet34 	|                             LAB 	|         MS-SSIM 	|      None 	|
|  KMHCNet_5 	|       Unet++ 	| Inceptionresnetv2 	|                             LAB 	|         MS-SSIM 	|      None 	|
|  KMHCNet_6 	|       Unet++ 	|          Resnet18 	|                             LAB 	|         MS-SSIM 	|      None 	|
|  KMHCNet_7 	|       Unet++ 	|   Efficientnet-b6 	|                             LAB 	|         MS-SSIM 	|      None 	|
|  KMHCNet_8 	|       Unet++ 	|         Resnet101 	|                             LAB 	|         MS-SSIM 	|      None 	|
|  KMHCNet_9 	|         Unet 	| Inceptionresnetv2 	|                             LAB 	|         MS-SSIM 	|      None 	|
| KMHCNet_10 	|         Unet 	|         Resnet152 	|                             LAB 	|         MS-SSIM 	|      None 	|
| KMHCNet_11 	|       Unet++ 	|         Resnet152 	|                             LAB 	|         MSELoss 	|      None 	|
| KMHCNet_12 	|       Unet++ 	|         Resnet152 	|                             LAB 	| MSELoss+MS-SSIM 	|  Resnet50 	|
| KMHCNet_13 	|       Unet++ 	|          Resnet50 	|                             RGB 	|         MS-SSIM 	|      None 	|
| KMHCNet_14 	|       Unet++ 	|         Resnet152 	|                             LAB 	| MSELoss+MS-SSIM 	|     Vgg16 	|
| KMHCNet_15 	|       Unet++ 	|         Resnet152 	|                             LAB 	|         MSELoss 	|     Vgg16 	|
| KMHCNet_16 	|       Unet++ 	|         Resnet152 	|                             LAB 	|         MSELoss 	|  Resnet50 	|

### KMHCNet Variant Results and Trainable Parameters
|    Variant 	| Test_Accuracy 	| Test_Loss 	| Epochs_Trained 	| Trainable_Parameters 	|
|-------------|-----------------|-------------|-----------------|-----------------------|
|  KMHCNet_1 	|       94.39 % 	|   18.40 % 	|             43 	|              83.62 M 	|
|  KMHCNet_2 	|       94.69 % 	|   16.76 % 	|             39 	|              48.98 M 	|
|  KMHCNet_3 	|       94.07 % 	|    5.93 % 	|             38 	|              83.62 M 	|
|  KMHCNet_4 	|       94.04 % 	|   19.07 % 	|             33 	|              26.07 M 	|
|  KMHCNet_5 	|       95.38 % 	|   14.16 % 	|             27 	|              71.08 M 	|
|  KMHCNet_6 	|       94.93 % 	|   15.69 % 	|             26 	|              15.96 M 	|
|  KMHCNet_7 	|       94.44 % 	|   17.73 % 	|             25 	|              43.33 M 	|
|  KMHCNet_8 	|       95.51 % 	|   13.84 % 	|             23 	|              67.97 M 	|
|  KMHCNet_9 	|       95.17 % 	|   14.60 % 	|             20 	|              62.03 M 	|
| KMHCNet_10 	|       94.75 % 	|   16.06 % 	|             20 	|              67.15 M 	|
| KMHCNet_11 	|       93.03 % 	|   73.45 % 	|             17 	|              83.62 M 	|
| KMHCNet_12 	|       93.39 % 	|   17.24 % 	|             13 	|              83.62 M 	|
| KMHCNet_13 	|       94.32 % 	|    5.68 % 	|             12 	|              48.98 M 	|
| KMHCNet_14 	|       93.73 % 	|   11.12 % 	|             10 	|              83.62 M 	|
| KMHCNet_15 	|       92.85 % 	|    1.47 % 	|             10 	|              83.62 M 	|
| KMHCNet_16 	|       92.68 % 	|   12.54 % 	|              9 	|              83.62 M 	|

### Model Diagram
<img src="https://github.com/clownprincejoker/KMHColorNet/blob/main/Model.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" border="10" />


### Test Sample Output for All Variants
<img src="https://github.com/clownprincejoker/KMHColorNet/blob/main/Results/Test_All.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" border="10" />

### Lagecy Sample Output for All Variants
<img src="https://github.com/clownprincejoker/KMHColorNet/blob/main/Results/Real_All.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" border="10" />

### Validation Accuracy Comparison
<img src="https://github.com/clownprincejoker/KMHColorNet/blob/main/Results/Accuracy_Plot_All.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" border="10" />

### Validation Loss Comparison
<img src="https://github.com/clownprincejoker/KMHColorNet/blob/main/Results/Loss_Plot_All.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" border="10" />

### Test Loss and Accuracy Comparison
<img src="https://github.com/clownprincejoker/KMHColorNet/blob/main/Results/Test_Result_for_All.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" border="10" />
