


# 🎙️ Higgs Audio Text-to-Speech Playground

A **Gradio UI** for generating realistic speech from text using the **HiggsAudioServeEngine** and voice cloning capabilities. This app supports multilingual generation, multispeaker dialogues, background music tags, custom reference voices, and advanced sampling options.

---

## 🚀 Features

* 🗣️ **Text-to-Speech (TTS)** using [bosonai/higgs-audio-v2-generation-3B-base](https://huggingface.co/bosonai/higgs-audio-v2-generation-3B-base)
* 🎛️ Interactive **Gradio UI** with predefined templates
* 👥 Voice cloning via reference audio or presets
* 🎵 Background music and sound effects tags support
* 🌐 Multilingual input (e.g., Chinese)
* 🔧 Advanced configuration for sampling (temperature, top-k, top-p, stop strings, etc.)
* 🖥️ Runs on CPU or GPU (CUDA)

---

## 📦 Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/SUP3RMASS1VE/Higgs-Audio-Text-to-Speech.git
   cd Higgs-Audio-Text-to-Speech
   ```

2. **Install dependencies:**

   ```bash
   python -m venv env
   env\Scripts\activate
   pip install uv
   uv pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
   pip install -r requirements.txt
   ```

---

## 🧪 Run the App

```bash
python app.py --device cuda --host 127.0.0.1 --port 7860
```

> Replace `--device cuda` with `--device cpu` if GPU is not available.

---

## 🧰 Command-Line Options

| Argument   | Description                  | Default     |
| ---------- | ---------------------------- | ----------- |
| `--device` | Run on `cpu` or `cuda`       | `cuda`      |
| `--host`   | Host IP for Gradio interface | `127.0.0.1` |
| `--port`   | Port for Gradio interface    | `7860`      |

---

## 🧩 Templates Included

| Template Name                      | Description                                |
| ---------------------------------- | ------------------------------------------ |
| `smart-voice`                      | Default narration with clean scene context |
| `voice-clone`                      | Clone voice from preset or uploaded audio  |
| `multispeaker-voice-description`   | Multiple speakers with tagged instructions |
| `single-speaker-voice-description` | Detailed speaker style in prompt           |
| `single-speaker-bgm`               | Uses `[music start]` / `[music end]` tags  |
| `single-speaker-zh`                | Chinese language input example             |

---

## 🧠 Reference Voice Presets

To use voice cloning, configure the `voice_examples/config.json` and place `.wav` files in the `voice_examples/` directory. Example `config.json`:

```json
{
  "belinda": {
    "transcript": "Hi, I'm Belinda, your voice assistant."
  },
  "josh": {
    "transcript": "Hello, this is Josh speaking."
  }
}
```

---

## 🔍 Tags for Audio Effects

You can enrich your text input with special tags like:

* `[laugh]`, `[music start]`, `[sing end]`, etc.
* Automatically converted into `<SE>` tags internally

Example:

```
[music start] The show is about to begin! [music end]
```

---

## 🧪 Advanced Sampling Settings

Available under "Advanced Parameters" in the UI:

* `Max Completion Tokens`
* `Temperature`, `Top-k`, `Top-p`
* Repetition Avoidance Sampling (`RAS Window Length`, `RAS Max Num Repeat`)
* `Stop Strings`

---

## 🛠️ Developer Notes

* Main engine logic uses `HiggsAudioServeEngine` with `ChatMLSample` message formatting
* CUDA fallback to CPU is supported if GPU is unavailable
* Chinese punctuation is normalized for better phoneme alignment
* Uses `loguru` for logging, `Gradio` for UI, and `torch` for inference

---

## 📸 UI Preview

<img width="1502" height="905" alt="Screenshot 2025-07-28 221301" src="https://github.com/user-attachments/assets/16c54a65-2d7c-4860-a358-0075b55132cc" />

---

## 📄 License

MIT License

---

## 👥 Credits

* Built with ❤️ using [Gradio](https://www.gradio.app/) and [HiggsAudio](https://huggingface.co/bosonai/higgs-audio-v2-generation-3B-base)

---

Let me know if you want a `requirements.txt` or Dockerfile to go with this.

