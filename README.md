# Mandarin_NGSS_Translation_Validator
🚀 Getting Started
1. Prerequisites
Hugging Face Token: Required for the Pyannote 3.1 diarization pipeline. Get one here.

OpenAI API Key: (Optional) Required only if using the Chained Translation method with GPT-4o.

2. Running the Notebook
Open Mandarin_NGSS_Translation_Validator.ipynb in your Jupyter environment.

Input your API keys in the Configuration cell.

Run the Batch Evaluator. A folder selection popup will appear (via tkinter) to help you select your source audio files.

The script will recursively search subfolders and mirror the directory structure in your output folder.

3. Reviewing Results
Open the generated NGSS_Translation_Evaluation.xlsx to conduct your reliability checks. The notebook also generates a Translation_Comparison_Chart.png to help you visualize differences in translation verbosity.

Adding a Troubleshooting section is highly recommended, as CUDA version mismatches and Hugging Face permission issues are the most common "showstoppers" when moving to these 2026-standard models.

Here is the additional text for your README.md.

🛠️ Troubleshooting & Common Issues
1. CUDA & GPU Errors
If you see RuntimeError: CUDA out of memory, try the following:

Reduce Batch Size: In the SenseVoice and Seamless models, lower the batch_size_s or batch_size parameters.

Clear Cache: The notebook includes torch.cuda.empty_cache(), but if a crash occurs, you may need to Restart the Kernel to fully release the VRAM.

Version Mismatch: Ensure your PyTorch version matches your CUDA toolkit (e.g., torch 2.4+ for CUDA 12.4). Use nvidia-smi in your terminal to check your driver version.

2. Hugging Face Access Denied
If the Pyannote diarization fails with a 403 Forbidden error:

Accept Terms: You must manually visit the Pyannote Segmentation 3.0 and Speaker Diarization 3.1 pages and click "Accept" on their respective terms of use.

Token Scope: Ensure your Hugging Face token is set to Read or Write access.

3. FFmpeg Requirements
Both SenseVoice and SeamlessM4T require ffmpeg for audio decoding. If you get a "file not found" error regarding audio processing, install it via:

Ubuntu/Debian: sudo apt install ffmpeg

macOS: brew install ffmpeg

Windows: choco install ffmpeg

4. ModelScope vs. Hugging Face
This notebook uses hub="ms" (ModelScope) for SenseVoice because it is significantly faster for CJK model downloads. If you are behind a firewall that blocks ModelScope, you can switch this to hub="hf", though download speeds for these specific models may be slower.

📂 Project Structure
Plaintext
.
├── Mandarin_NGSS_Translation_Validator.ipynb  # Main Research Notebook
├── README.md                                  # Documentation
├── .env                                       # (Optional) Store HF_TOKEN and OPENAI_KEY
└── requirements.txt                           # List of dependencies

🔬 Research Context
...

📜 License & Attribution
This project is licensed under the MIT License.

Transcription: Alibaba FunASR / SenseVoice

Diarization: Pyannote.audio

Translation: Meta SeamlessM4T v2