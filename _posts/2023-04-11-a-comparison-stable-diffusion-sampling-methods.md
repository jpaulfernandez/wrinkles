---
layout: post
title: 'A Comparison of 10 Stable Diffusion Sampling Methods'
date: 2023-04-11 16:46 +0800
image: header-img.png
img_path: /assets/img/stablediffusion/
categories: [technology]
tags: [prompting, artificial intelligence, chatgpt, image models, transformers, text to image generation, stable diffusion, dreamshaper]
---

On this blog, I compared different results of different sampling method with increasing sampling steps. 

## Environment

To make sure that we can compare each sampling method as close as possible, we use the same prompt and the same seed for each image generation. I also used EasyNegative embeddings for the textual inversion.

**Prompt**: hyper realistic, front view of a woman wearing dress, in a garden with bright sky smiling for a photograph, 8k, Alasdair McLellan

**Seed**: 808861893
**CFG**: 10

**Model**: [DreamShaper 4 Baked VAE](https://civitai.com/models/4384/dreamshaper)

Stable diffusion is locally hosted in my PC with these specs:
- Nvidia 3070 8gb ram
- Intel i7 10800H
- 32gb Ram
- Ubuntu via WSL2 (OS)

### Sampling Methods

1. Euler a
2. Euler
3. LMS
4. Heun
5. DPM2
6. DPM2 a
7. LMS Karras
8. DPM++ 2M Karras
9. DPM++ SDE Karras
10. DDIM

To begin, I used the same prompt to generate the first image using the Euler a method with 20 steps. Once I obtained the seed from the first image, I used it in the subsequent prompt and increased the number of steps. I then increased the steps by increment of 20 until I reached the 60 steps, then maxed it out to 120.


## Euler a

![Euler a comparison](/euler-a-comparison.png) _Image generated with Euler a, steps from 20, 40, 60, 120_


Euler A (ancestral) is the default sampling method for Stable Diffusion Web UI. It produces high-quality images with fast processing times. However, increasing the number of sampling steps significantly changes the generated image. In this case, by adding the name of Alasdair McLellan to our prompt, we hope that the image generated will mimic the artist's style.

It is worth noting that Euler A sampling method has added a house in the background, even though it was not specified in the prompt. The artist's style only appears at step 60, and we recommend using Euler A for best results with 40-60 step configuration.

## LMS

![LMS comparison](/LMS-comparison.png) _Image generated with LMS, steps from 20, 40, 60, 120_

Linear multi-step (LMS) often produces noise artifacts in lower steps as shown in the first . Despite some parts of the background still having some noise, the hair of the subject is significantly noisier.

However, as we increase the sampling steps beyond 40, there is not much significant difference in the generated images. Although there may be some variation in the accessories, flowers in the background, and dress, ultimately, the image remains the same, unlike the images generated using Euler A.

I recommend using LMS between 40-60 steps for best results.

## DPM2 a

![DPM2 a comparison](/dpm2-a-comparison.png) _Image generated with DPM2 a, steps from 20, 40, 60, 120_

DPM2 A (ancestral) is a fascinating sampling method to use because, like Euler A, the generated images become significantly different the more you increase its sampling steps. It is able to capture the art style specified in the prompt in just 20 steps. Furthermore, it produces dynamic backgrounds, including houses, other people, and a variety of plants and flowers, even though they were not specified in the prompt. It also generates different poses.

Based on this comparison, DPM2 A performs exceptionally well at any sampling steps.

## LMS Karras

![LMS Karras comparison](/lms-karras.png) _Image generated with LMS Karras, steps from 20, 40, 60, 120_

LMS Karras uses a different type of noise to generate image, although it has the same speed as LMS when generating image.

![LMS vs LMS Karras comparison](/lms-vs-lmskarras.png) _Image generated with LMS vs LMS Karras, steps from 20, 40, 60, 120_

Interestingly, LMS Karras produces a more cartoonish image at lower sampling steps compared to LMS, which fails to generate a usable image. However, as we increase the sampling steps to 40 and higher, it converges into the same image. There is little to no significant difference, except for minor variations in the dress accessories and the plants and flowers in the background.

## DPM++ SDE Karras

![DPM++ SDE Karras](/dpm++-sde-karras.png) _Image generated with DPM++ SDE Karras, steps from 20, 40, 60, 120_

We were faithful to the prompt in using DPM++ SDE Karras. We requested Stable Diffusion to copy the style of Alasdair McLellan, a photographer known for his monocrhome style, which is why the generated images have a sepia tone. However, our prompt may be contradictory since we also asked for a bright photo.

It is noteworthy that even without the "ancestral" tag, DPM++ SDE Karras appears to use stochastic sampling as evidenced by the large variation in the generated images. It adds a lot of context in the background, including a fence at 20 steps and even some houses at higher steps.

## Euler, Heun, DPM2, DPM++ 2M Karras, DDIM

![Euler - ddim comparison](/euler-ddim-comparison.png) _Image generated with Euler, Heun, DPM2, DPM++ 2M Karras, DDIM, steps from 20, 40, 60, 120_

Finally, the images generated using Euler, Heun, DPM2, DPM++ 2M Karras, and DDIM do not seem to have any major differences, as seen in the photo above. However, it is worth noting that in the prompt we used, we specified that we wanted a hyper-realistic photo, and we can see that the higher the sampling step, the more photorealistic the image becomes. It should be noted that the models we used specialize in creating a hybrid of photorealistic and digital art images.


## Full Image Comparison

![DPM++ SDE Karras](/sampling-methods-comparison.png) _Full comparison of sampling methods, stable diffusion_

## Few Observations

Here's few observation while I'm doing this comparison. Note that results may vary depending on the environment you're running stable diffusion with, the prompt and the model. 

- Euler a will be the cost efficient sampling method as it's fast but has lesser accuracy.
- LMS is the fastest sampling methods out of these experiment.
- DPM++ SDE Karras is the best when it comes on respecting the prompt.
- Most of the other sampling methods doesn't affect the generated image, it only affects the speed of generating image, but ultimately they converge on the same image after few steps.

## Resources

- [Stable Diffusion Samplers](https://nightcafe.studio/blogs/info/stable-diffusion-samplers)
- [Stable Diffusion Samplers: A comprehensive Guide](https://stable-diffusion-art.com/samplers/)
- [All the different samplers](https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/4384#discussioncomment-4562593)
- [DreamShaper 4 Baked VAE](https://civitai.com/models/4384/dreamshaper)


*This blog is written with the help of gpt3.5 and reviewed by the primary author*





