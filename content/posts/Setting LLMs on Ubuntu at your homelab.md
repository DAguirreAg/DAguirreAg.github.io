---
title: 'Setting LLMs on Ubuntu at your homelab'
date: 2024-05-26T18:34:51+02:00
draft: false
tags: ["LLM", "Ubuntu", "Homelab", "On-premise"]
cover:
  image: images/setting_llms_on_ubuntu_at_your_homelab/llm_prompt.png
---

As a private and technical person, it is common to be afraid of the data capturing capabilities of current LLM models. Because of this, I decided to create a small post explaining how to set up your own LLM workspace in your own computer, so you can still can use the latest LLMs without being worried about being spied.

# Basic requirements
Notice that one of the downsides of LLMs is that they require somewhat expensive hardware to run on. The good news is that most modern gaming GPUs (even the gaming ones) are capable of running most of the models. So, if you happen to have one of the latest GPUs, you very likely will be able to run LLMs.

# Installing software

1. Start by installing NVIDIA drivers. For generic use: `sudo ubuntu-drivers install`
2. Restart computer
3. Check that Nvidia drivers are installed by typing the following in terminal: `nvidia-smi`
4. Install CUDA: `sudo apt install nvidia-cuda-toolkit`
5. Check that CUDA installation was succesfull by typing the following in terminal: `nvcc --version`
6. Install Ollama tool by typing: `curl https://ollama.ai/install.sh | sh`

# Running the LLMs

1. Decide which LLM model you want to use ([Check available LLM models here](https://ollama.com/library)). (Note that you may be limited based on the available RAM).
2. Start Ollama server by typing the following in a terminal: `ollama serve`
3. Run the model by typing the following in a terminal: `ollama run {llm-name}` (example: `ollama run llama3`)

# References

* [Running an LLM in Ubuntu Linux](https://www.jeremymorgan.com/blog/generative-ai/run-llm-locally-ubuntu/)
* [Installing NVIDIA drivers on Ubuntu](https://ubuntu.com/server/docs/nvidia-drivers-installation)
* [Ollama GitHub](https://github.com/ollama/ollama)





