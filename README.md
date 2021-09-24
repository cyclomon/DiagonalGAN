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

Download Link:
[CelebA-HQ](https://drive.google.com/drive/folders/0B4qLcYyJmiz0TXY1NG02bzZVRGs?resourcekey=0-arAVTUfW9KRhN-irJchVKQ) / 
[AFHQ](https://github.com/clovaai/stargan-v2)

Unzip the files and put the folder into the data directory (```./data/Celeb/data1024``` , ```./data/afhq```)

To train the multidomain Diagonal GAN, run 

```
./data/Celeb/Celeb_proc.py 
```
After download the CelebA-HQ dataset to save males / females images in different folders.

We randomly selected 1000 images as validation set for each domain (1000 males / 1000 females).

Save validation files into ```./data/Celeb/val/males``` , ```./data/Celeb/val/females```

### Train Basic Diagonal GAN
For full-resolution CelebA-HQ training,

```
python train.py --datapath ./data/Celeb/data1024 --sched --max_size 1024 --loss r1
```

For full-resolution AFHQ training,

```
python train.py --datapath ./data/afhq --sched --max_size 512 --loss r1
```
### Train Multidomain Diagonal GAN
For training multidomain (Males/ Females) models, run

```
python train_multidomain.py --datapath ./data/Celeb/mult --sched --max_size 256
```

### Train IDInvert on pre-trained Multidomain Diagonal GAN
For training IDInvert on  pre-trained model,
```
python train_idinvert.py --ckpt $MODEL_PATH$ 
```

or you can download the pre-trained Multidomain model. 

Save the model in ```./checkpoint/train_mult/CelebAHQ_mult.model```

and set ```$MODEL_PATH$``` as above.

### Additional latent code optimization ( for inference )
For further optimize the latent codes, 

```
python train_idinvert_opt.py --ckpt $MODEL_PATH$ --enc_ckpt $ENC_MODEL_PATH$
```

```MODEL_PATH``` is pre-trained multidomain model directory, and

```ENC_MODEL_PATH``` is IDInvert encoder model directory.

You can download pre-trained IDInvert encoder models.

We also provide optimized latent codes. 

