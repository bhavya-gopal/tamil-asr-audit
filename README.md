# Tamil ASR Audit

An audit of Microsoft Azure's Speech-to-Text API comparing performance on Tamil (low-resource) vs. English (high-resource) speech, using Mozilla Common Voice datasets.

## Overview

This project evaluates whether Azure STT exhibits performance disparities across languages and demographic subgroups, measured via Word Error Rate (WER).

**Datasets:**
- **Tamil:** Mozilla Common Voice 17.0 — crowd-sourced scripted speech with age/gender metadata
- **English:** Mozilla Common Voice Spontaneous Speech 1.0 — conversational responses with human transcriptions

Both datasets were filtered to a shared duration range (1.5–10.6s) and stratified-sampled into 100 clips per language across four duration bins.

## Key Findings

| Language | Mean WER |
|----------|----------|
| Tamil    | 0.415    |
| English  | 0.232    |

- Tamil WER was ~1.8x higher than English, consistent with lower representation of Tamil in commercial ASR training data
- Short clips (1.5–3s) had higher WER than medium-length clips, likely due to less acoustic context
- Gender had minimal impact on Tamil WER (female: 0.434, male: 0.379)
- Age subgroup results were inconclusive due to small per-group sample sizes

## Repository Contents

- `main_analysis.ipynb` — the full analysis notebook (data cleaning, API calls, WER computation, and visualization)

> Note: datasets and results are not included due to size and licensing constraints.

## References

- Ardila et al. (2020). [Common Voice: A Massively-Multilingual Speech Corpus](https://arxiv.org/abs/1912.06670). *LREC*.
- Mozilla Data Collective. Common Voice Scripted Speech 17.0 – Tamil / Spontaneous Speech 1.0 – English.
- Microsoft Azure [Speech-to-Text documentation](https://learn.microsoft.com/en-us/azure/ai-services/speech-service/).
- Morris et al. (2004). From WER and RIL to MER and WIL. *INTERSPEECH*.
- Adda et al. (2016). Breaking the unwritten language barrier: The BULB project. *Procedia Computer Science*, 81.
