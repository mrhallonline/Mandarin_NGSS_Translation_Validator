Installation Guide for Your Machine
1. Create a fresh environment:
It is highly recommended to use a clean Conda environment for this "Next Gen" pipeline to avoid conflicts with your older WhisperX setup.

Bash
conda create -n mandarin-translator-env python=3.11 -y
conda activate mandarin-translator-env

2. Install the dependencies:
Navigate to the folder where you saved the file and run:

Bash
pip install -r requirements.txt

3. Verify GPU Visibility:
Run this quick check in your terminal to ensure the new environment sees your CUDA card:

Bash

python -c "import torch; print(f'CUDA Available: {torch.cuda.is_available()}'); print(f'GPU: {torch.cuda.get_device_name(0)}')"

pip3 install torch torchvision --index-url https://download.pytorch.org/whl/cu128