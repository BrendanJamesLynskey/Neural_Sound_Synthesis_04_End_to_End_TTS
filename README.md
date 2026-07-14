# Neural Sound Synthesis · Part 4 — End-to-End Text-to-Speech

Part four of the [Neural Sound Synthesis](https://github.com/BrendanJamesLynskey/Neural_Sound_Synthesis) series. How text becomes a talking voice: the text → acoustic-model → mel → vocoder pipeline and the progressive move to end-to-end. Tacotron's attention and why it was fragile, FastSpeech's length regulator that made TTS parallel and robust, and VITS folding text, duration, spectrogram and waveform into one adversarially-trained conditional VAE.

### [Launch App](https://brendanjameslynskey.github.io/Neural_Sound_Synthesis_04_End_to_End_TTS/)

Part of the [DSP & Music](https://github.com/BrendanJamesLynskey/DSP_and_Music) collection.

---

## What's inside

| Section | Content |
|---------|---------|
| **The Pipeline** | text → acoustic model → mel → vocoder; the alignment problem; three answers (attention, duration, MAS) |
| **Tacotron & Attention** | CBHG encoder, autoregressive mel decoder, stop token, content vs **location-sensitive** attention — with a **live attention aligner you can make fail** |
| **FastSpeech** | Non-autoregressive; the **length regulator** expansion; duration predictor (FS1 distilled from an AR teacher, FS2 from forced alignment); pitch/energy variance adaptors — with a **stretchable formant synthesiser** |
| **VITS** | Conditional VAE, normalizing-flow prior, **monotonic alignment search**, stochastic duration, HiFi-GAN decoder + adversarial training; the **ELBO with the flow change-of-variables** — with a **clickable architecture explorer** |
| **Frontier** | Glow-TTS as the MAS/flow link; modern zero-shot/prompt TTS (VALL-E as a token-LM teaser for Part 10) |
| **Timeline** | 2017 → 2023, Tacotron to VALL-E, cross-linked to Parts 3, 5 and 10 |

## Live demos (all synthesised in-browser, no audio files)

1. **Attention alignment animator** — an encoder–decoder attention matrix builds up frame-by-frame; toggle between a healthy monotonic diagonal and a failure mode (stall / skip / collapse) to see what "the model lost alignment" looks like.
2. **Duration-controlled synthesis** — the FastSpeech length regulator: per-phoneme duration sliders expand "hello" into a frame timeline and synthesise an audible utterance (Klatt-style formant resonators) whose timing follows the durations. Stretch a slider to lengthen that sound; a global speaking-rate control scales them all.
3. **VITS architecture explorer** — an interactive block diagram (text encoder → MAS → prior; posterior encoder → z → flow → HiFi-GAN decoder → waveform + discriminators). Hover, click or take the guided tour for explanations of the CVAE + flow + adversarial combination and MAS.

## Technology

Single-file HTML/CSS/JS · Web Audio API · HTML5 Canvas · KaTeX · Palatino + Lucida Console · No external dependencies · No build step
