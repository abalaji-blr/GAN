# CycleGAN for Faces Dataset

* Faces Dataset Location: <https://susanqq.github.io/UTKFace/>

* Original CycleGAN Implementation in PyTorch is available at <https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix>

* [My Keras Implementation](./CycleGAN_Faces_v2.ipynb)

### Discriminator

For Discriminator:

- Use PatchGAN - only penalizes the structure at the scale of patches.
- PatchGAN classifies the NxN patch is real or fake
- They have fewer parameters than the full image discriminator
- PatchGAN are used in [Image to Image translation](https://arxiv.org/pdf/1611.07004.pdf)

### Generator

Generator can be one of the following two things:

```
 * Encoder : Decoder combo (UNet - uses skip connections)
 or
 * Encoder : Transformer : Decoder (Uses Residual blocks)
```

The Encoder shrinks the input image. Uses Conv layers (with strides:2).

The Transformer uses residual blocks

The Decoder expands the image with transpose Conv.

Note: each layer will use **LeakyReLU and InstanceNormalization**

#### Resnet block

Original paper uses **reflection padding**. Let's use **same** padding for simplicity.

### Some FAQs

* What is Instance Normalization?

* What is Reflection padding?

  In the case of reflection padding, instead of zero values, the values obtained by the reflection of the image will be set. This will help in better texture identification.

  

## Results



### Young to Old

![y2o](./group_images/y2o.png)



#### Reconstructed images



![plot_19](./young_to_old/plot_19.png)

![plot_18](./young_to_old/plot_18.png)

![plot_15](./young_to_old/plot_15.png)

### Old to Young

![o2y](./group_images/o2y.png)

### Reconstructed Images

![plot_65](./old_to_young/plot_65.png)

![plot_76](./old_to_young/plot_76.png)

![plot_83](./old_to_young/plot_83.png)

