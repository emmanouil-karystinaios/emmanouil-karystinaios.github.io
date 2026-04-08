---
title: "Multi-Stage Music Source Restoration with BandSplit-RoFormer Separation and HiFi++ GAN"

authors:
- Tobias Morocutti
- admin
- Jonathan Greif
- Gerhard Widmer

author_notes: []

date: "2026-03-04T00:00:00Z"
doi: "2603.04032"

publishDate: "2026-03-04T00:00:00Z"

publication_types: ["4"]

publication: Technical report for the ICASSP 2026 Music Source Restoration (MSR) Challenge
publication_short: ICASSP MSR Challenge

abstract: Music Source Restoration (MSR) targets recovery of original, unprocessed instrument stems from fully mixed and mastered audio, where production effects and distribution artifacts violate common linear-mixture assumptions. This technical report presents the CP-JKU team's system for the MSR ICASSP Challenge 2025. Our approach decomposes MSR into separation and restoration. First, a single BandSplit-RoFormer separator predicts eight stems plus an auxiliary other stem, and is trained with a three-stage curriculum that progresses from 4-stem warm-start fine-tuning (with LoRA) to 8-stem extension via head expansion. Second, we apply a HiFi++ GAN waveform restorer trained as a generalist and then specialized into eight instrument-specific experts.

summary: A two-stage system for music source restoration that combines BandSplit-RoFormer separation with HiFi++ GAN restoration for recovering clean instrument stems from mixed and mastered audio.

tags:
- Audio Processing
- Music Source Separation
- Restoration

featured: false

url_pdf: 'https://arxiv.org/pdf/2603.04032'
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

image:
  caption: ''
  focal_point: ""
  preview_only: false

projects: []
slides: ""
---
