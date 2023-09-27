# Generative Approaches to CIFAR10 Colourization
This repository showcases two approaches to the coulourization task of CIFAR10 images: Auto Encoder U-Net and Conditional GANs. Over the last decade, the process of automatic colorization had been studied thoroughly due to its vast application such as colourization of grayscale images and restoration of aged and/or degraded images. This problem is highly ill-posed due to the extremely large degrees of freedom during the assignment of color information. In this approach, I attempted to fully generalize this procedure using a conditional Deep Convolutional Generative Adversarial Network (DCGAN). The network is trained over a dataset that is publicly available, CIFAR10.

*Important Notes: The GAN architecture uses a U-Net like fully convolutional architecture  (with concatenation of opposite layers) for the generator, and the G loss function is L1 regularized, which produces an effect where the generator is forced to produce results that are similar to the ground truth on the pixel level. This will theoretically preserve the structure of the original images and prevent the generator from assigning arbitrary colors to pixels just to fool the discriminator. The generator takes the grayscaled image as an input, while the discrimator takes either the original image or generated image plus the condition, which is the grayscaled image in this case.

The U-Net architecture used for both the Auto Encoder and generator can be represented with this graph. The gray arrows represent the skip connections from encoder to the mirroring decoder layer.
![Untitled](https://github.com/M4mbo/Generative_Approaches_to_CIFAR10_Colourization/assets/115642529/89e36747-deb9-4ca4-a300-02a4b941312d)

DCGAN Results:

![image](https://github.com/M4mbo/Generative-Colourization-Approaches-to-CIFAR10/assets/115642529/0e01f3af-3d12-4d28-981d-7041f209c4d5)

![image](https://github.com/M4mbo/Generative-Colourization-Approaches-to-CIFAR10/assets/115642529/897686d0-4c8b-4e7b-965e-bad6145c3f76)

Auto Enconder Results:

![image](https://github.com/M4mbo/Generative-Colourization-Approaches-to-CIFAR10/assets/115642529/cfb05896-1caa-4ef1-8ef0-374e7862e5b9)


![image](https://github.com/M4mbo/Generative-Colourization-Approaches-to-CIFAR10/assets/115642529/fd13dc37-20f7-418d-8018-219b2f44c98a)

Results: GAN generated images had a clear visual improvement than those generated by the U-Net. These contained colors that were more vibrant whereas the results from U-Net suffered from a
light hue and phenomenon called "sepia effect". In some cases, the GAN was able to nearly replicate the ground truth. It was even able to colorize reasonably well on one of the images where the ground truth was grayscale. Nonetheless, both models where trained for only 20 epochs, and it appeared that the loss function continued to have a negative gradient for the last epoch, so they probably need more time to converge.
