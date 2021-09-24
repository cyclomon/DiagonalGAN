# DiagonalGAN
## Official Pytorch Implementation of "Diagonal Attention and Style-based GAN for Content-Style Disentanglement in Image Generation and Translation" (ICCV 2021)
Link : [Arxiv](https://arxiv.org/abs/2103.16146)

### Abstract
One of the important research topics in image generative models is to disentangle the spatial contents and styles for their separate control. Although StyleGAN can generate content feature vectors from random noises, the resulting spatial content control is primarily intended for minor spatial variations, and the disentanglement of global content and styles is by no means complete. Inspired by a mathematical understanding of normalization and attention, here we present a novel hierarchical adaptive Diagonal spatial ATtention (DAT) layers to separately manipulate the spatial contents from styles in a hierarchical manner. Using DAT and AdaIN, our method enables coarse-to-fine level disentanglement of spatial contents and styles. In addition, our generator can be easily integrated into the GAN inversion framework so that the content and style of translated images from multi-domain image translation tasks can be flexibly controlled. By using various datasets, we confirm that the proposed method not only outperforms the existing models in disentanglement scores, but also provides more flexible control over spatial features in the generated images.


![Models9](https://user-images.githubusercontent.com/88644048/130436052-f9c213b3-a3f4-403f-84b9-9ccdad8c8970.png)

### Environment Settings
Python 3.6.7 +
Pytorch 1.5.0 +

### Dataset
For faster training, we recommend .jpg file format.
[CelebA-HQ](https://drive.google.com/drive/folders/0B4qLcYyJmiz0TXY1NG02bzZVRGs?resourcekey=0-arAVTUfW9KRhN-irJchVKQ)
[AFHQ](https://github.com/clovaai/stargan-v2)

Unzip the files and put the folder into data directory (./data/Celeb , ./data/afhq)

### Train
