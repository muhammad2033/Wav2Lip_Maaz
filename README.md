🎥 Wav2Lip – Customized & Deployment-Ready Implementation

This repository contains a customized and deployment-friendly implementation of Wav2Lip, a state-of-the-art lip synchronization model originally developed by Rudrabha et al.

The primary purpose of this repository is to adapt the original research codebase for real-world usage, including client demos, web-based testing, and modern Python environments (Python 3.12+).

🔹 Original Work & Credit

This project is based on the original Wav2Lip repository:

Author: Rudrabha et al.

Original Repository: https://github.com/Rudrabha/Wav2Lip

Paper:
A Lip Sync Expert Is All You Need for Speech to Lip Generation
ACM Multimedia 2020

All credit for the model architecture, training methodology, and research contributions belongs to the original authors.

🎯 Purpose of This Repository

The original Wav2Lip implementation is research-oriented.
This repository focuses on making Wav2Lip:

Easier to run in modern environments

Stable for client testing & demos

Suitable for API-based deployment

Compatible with Python 3.12+ and latest dependencies

🔧 Key Modifications & Enhancements

The following non-research modifications were introduced:

✅ Usability Improvements

Simplified inference workflow

Better error handling for invalid inputs

Stable execution for short demo clips

Cleaner structure for backend integration

✅ Deployment Readiness

Compatible with FastAPI / Flask backends

Suitable for Google Colab and cloud servers

Supports CPU and GPU inference

Easier frontend integration for client access

⚠️ The core Wav2Lip model and inference logic remain unchanged.

🧠 System Requirements

Python 3.8+ (Fully tested on Python 3.12)

CUDA (optional, but recommended)

FFmpeg

NVIDIA GPU (for best quality & speed)

📦 Installation

Clone the repository:

git clone https://github.com/muhammad2033/Wav2Lip_Maaz.git
cd Wav2Lip_Maaz
Google Colab File: https://colab.research.google.com/drive/1IOKIKh9RZAu3W4YMWAOi_mqAWND3aXWG

Furthermore, you can run this file.

In addition, I'll be giving you a full guidance regarding this project, "Lip Syncing"

Install dependencies:

pip install -r requirements.txt


Download the pretrained checkpoints and place them in the checkpoints/ directory:

wav2lip.pth

wav2lip_gan.pth (recommended for better quality)

🚀 Inference Example
python inference.py \
--checkpoint_path checkpoints/wav2lip_gan.pth \
--face input.mp4 \
--audio audio.wav \
--pads 0 20 0 0 \
--fps 25 \
--outfile output.mp4

🟢 Best Quality Recommendations

For optimal lip-sync and video quality:

Use front-facing, high-resolution video

Ensure good lighting

Use 16kHz mono audio

Prefer wav2lip_gan.pth

Run inference on GPU

Post-process output using FFmpeg or GFPGAN

🛠️ Python 3.12 & Librosa Compatibility Fix
❗ Issue

Newer versions of librosa do not accept positional arguments in:

librosa.filters.mel()


This causes the following error:

TypeError: mel() takes 0 positional arguments but 2 positional arguments were given

✅ Option 1 – Patch audio.py (Recommended)

Edit _build_mel_basis() in audio.py:

def _build_mel_basis():
    return librosa.filters.mel(
        sr=hp.sample_rate,
        n_fft=hp.n_fft,
        n_mels=hp.num_mels,
        fmin=hp.fmin,
        fmax=hp.fmax
    )

✔ Why this works

Uses keyword arguments instead of positional

Fully compatible with:

Python 3.12+

Latest librosa

CPU & GPU inference

After saving the file, rerun inference.

⚠️ Option 2 – Downgrade Librosa (Not Recommended)
pip uninstall -y librosa
pip install librosa==0.7.0

❌ Limitations

Requires Python ≤ 3.9

Not compatible with Python 3.12

Not suitable for modern deployments

🌐 Client Access & Deployment (Suggested Architecture)
Client Browser
   ↓
Frontend (HTML / Streamlit)
   ↓
Backend API (FastAPI / Flask)
   ↓
Wav2Lip Inference (This Repository)


This setup allows secure and controlled access for clients without exposing the model directly.

⚠️ Limitations

Extreme head movements may reduce accuracy

Singing and exaggerated expressions are not fully supported

Output quality depends heavily on input quality

📜 License & Ethical Use

This repository follows the same license terms as the original Wav2Lip project.
Users must ensure:

Proper attribution to original authors

Ethical and legal use of generated content

No impersonation, misuse, or deceptive applications

👤 Maintainer

Muhammad Maaz
AI / ML Engineer
Customized for client demos, testing, and deployment workflows.

🙏 Acknowledgement

I would like to express my sincere thanks to Rudrabha and the Wav2Lip authors for their exceptional research and open-source contribution.
This work builds upon their foundation with respect, aiming only to improve usability, compatibility, and real-world accessibility.
