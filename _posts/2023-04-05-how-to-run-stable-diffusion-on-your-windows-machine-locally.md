---
layout: post
title: How to Run Stable Diffusion on Your Windows Machine Locally
date: 2023-04-05 11:36 +0800
image: stablediffprev.jpg
img_path: /assets/img/
categories: [technology]
tags: [prompting, artificial intelligence, chatgpt, image models, transformers, text to image generation, stable diffusion]
---

> Disclaimer: This tutorial is generated with the help of chatgpt. 

Are you looking for a way to run stable diffusion, a powerful AI tool for image generation, and computer vision, on your Windows machine? Look no further! In this tutorial, we will guide you through the steps to set up and run stable diffusion locally.

## Prerequisites
This tutorial requires you to use WSL2 with ubuntu, you can read my previous blog on how I setup my development environment [here]( https://paulfernandez.dev/posts/setting-up-web-development-environment-on-windows/.)

## System Requirements
In addition to the prerequisites, we recommend that you have the following system requirements to ensure optimal performance of stable diffusion:

- Recommended NVIDIA graphics card with at least 6GB of RAM
- At least 10GB of storage space

## Installing Necessary Services

You need to install wget, git, python and python3-venv before starting. If you have done this already, you can skip to the next part

```
sudo apt install wget git python3 python3-venv
```

## Running Stable Diffusion
Once you have completed the prerequisites, you can proceed with the following steps:

Open the Command Prompt or PowerShell on your Windows machine and run the following command to download the stable diffusion webui.sh script:

```
bash <(wget -qO- https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh)
```

This command will download the webui.sh script from the GitHub repository and save it to your current directory.

Once the download is complete, you can run the stable diffusion by executing the following command:

```
./webui.sh
```

This command will start the stable diffusion server and you can access it via localhost:7860. You can now use stable diffusion to generate images.

In conclusion, running stable diffusion on your Windows machine locally can be a great way to perform AI tasks without relying on external services. By following the steps outlined in this tutorial, you can quickly set up and run stable diffusion on your machine and take advantage of its powerful capabilities for image generation, midjourney, and computer vision.