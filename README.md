# Qwen 3.5 (4B) Uncensored - Colab & Ollama Deployment

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/14q8Nr3IElLgCloYUa0-8DstWFrJAOzYt/view?usp=sharing)

A streamlined Jupyter Notebook designed to effortlessly deploy and run the **Qwen 3.5 4B Uncensored** model on Google Colab. This project leverages the free T4 GPU provided by Colab, uses **Ollama** for highly efficient local model serving, and provides a sleek, shareable web interface using **Gradio**.

---

## Features

* **Free GPU Acceleration:** Configured to automatically detect and utilize Google Colab's T4 GPU for fast, responsive text generation.
* **Uncensored Model:** Runs the `HauhauCS/Qwen3.5-4B-Uncensored-HauhauCS-Aggressive` model (Q4_K_M GGUF format) for unrestricted, highly direct outputs.
* **Ollama Backend:** Seamlessly downloads, builds, and serves the model locally within the Colab environment using Ollama's efficient inference engine.
* **Interactive UI:** Automatically spins up a beautiful `Gradio` chat interface with streaming text responses.
* **Public URL Generation:** Generates a public Gradio link so you can chat with your model from your phone or any other browser outside of Colab.

---

## Tech Stack

* **Environment:** Google Colab
* **LLM Engine:** [Ollama](https://ollama.com/)
* **Model:** Qwen 3.5 4B (Uncensored / Aggressive Tune) via Hugging Face
* **Interface:** [Gradio](https://gradio.app/)

---

## How to Operate

Running this notebook is incredibly simple. Just click the **Open in Colab** button at the top of this page, and follow these steps:

### Step 1: Initialize the Environment
Run the first cell to install the necessary system dependencies. This will install background utilities (like `pciutils` and `curl`), download Ollama, and fetch required Python packages (`huggingface_hub`).

### Step 2: Boot the Server & Link the GPU
Run the second cell. This script explicitly points the environment to Colab's GPU drivers and starts the Ollama server in the background. You should see a success message and a readout from `nvidia-smi` confirming the T4 GPU is active.

### Step 3: Download & Build the Model
Run the third cell. This step handles the heavy lifting:
1. Downloads the quantized `.gguf` model file from Hugging Face.
2. Generates a custom `Modelfile` with optimized parameters (4096 context window, temperature 0.7) and the correct ChatML template.
3. Builds the model directly into Ollama. 
*(Note: This cell takes a minute or two to download the model).*

### Step 4: Launch the Chat Interface
Run the final cell. This script will:
* Refresh the Ollama server to ensure the GPU is perfectly linked.
* Build a `Gradio` chat interface connected to Ollama's API.
* Generate a **public share link** (e.g., `https://xxxx.gradio.live`).
* Enter an infinite loop to keep the Colab environment alive while you chat.

**To Chat:** Click the generated Gradio link in the output of Cell 4. 

### How to Stop
To shut down the server, simply click the **Stop** button on the final cell in Colab. The script will catch the manual interruption and shut down the background processes gracefully.

---

## Disclaimer
This notebook deploys an *uncensored* version of Qwen 3.5. The model has had its safety guardrails removed or altered and may produce content that is aggressive, explicit, or otherwise restricted in standard models. Proceed with discretion.
