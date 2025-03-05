---
title: Language Models for Music Medicine Generation
subtitle: A novel model for generating music for music therapy purposes 

# Summary for listings and search engines
summary: This research introduces a novel model for generating music for music therapy purposes, named *Language Models for Music Medicine Generation*. The paper explores how AI-driven music can support mental health by guiding listeners through emotional transitions using generative music designed to align with established therapeutic principles. 

# Link this post with a project
projects: []

# Date published
date: "2024-11-11T00:00:00Z"

# Date updated
lastmod: "2024-11-11T00:00:00Z"

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Use math
math: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 'Language Models for Music Medicine Generation'
  focal_point: ""
  placement: 2
  preview_only: false

authors:
- admin

tags:
- Academic

categories:
- Large Language Models
- Music Medicine
- Generation
---


Recent advances in generative AI has reached the music field.
Many generative music models can lead to awesome creations.
But there is one compelling new application that has been left until now unexplored, music therapy. 
This research, originally presented at the ISMIR 2024 Conference as a late breaking demo, introduces a novel model for generating music for music therapy purposes, named *Language Models for Music Medicine Generation*. The paper explores how AI-driven music can support mental health by guiding listeners through emotional transitions using generative music designed to align with established therapeutic principles.


### Background: The Therapeutic Power of Music

Music therapy, recognized since the 19th century, has been scientifically shown to provide significant mental health benefits, such as reducing anxiety and improving mood. While traditional music therapy is conducted by certified professionals, *Music Medicine* offers a new approach: self-administered music interventions that can be beneficial between therapist-guided sessions.

### Model Overview: Fine-Tuning MusicGen for Therapy

To create a therapeutic experience, the researchers fine-tuned MusicGen, a state-of-the-art generative model initially trained on vast amounts of instrumental music, using the MTG-Jamendo dataset annotated with emotion and mood labels. They adapted MusicGen to produce music that aligns with specific emotional states, using a method known as low-rank adaptation (LoRA), which enables efficient fine-tuning without altering the original model’s core weights.

### The Iso Principle and Emotional Transitions

Central to this model is the *iso principle*, a technique in music therapy where music reflecting the listener’s current emotional state gradually shifts to evoke a more desired emotional outcome. The model generates sequences of 30-second audio clips, each crafted to represent an intermediate emotional state between the listener's current mood and their targeted emotional state. These clips are then combined to form a cohesive 15-minute "music medicine" session that smoothly transitions across a spectrum of emotions.

### Methodology: Creating Emotional Continuity

Each audio clip is generated through prompt engineering, where tags define the emotional state, preferred instrument, and genre. To create a seamless experience, the clips are normalized, trimmed, and then overlapped and crossfaded. The model's parameters, such as genre and instrumentation, are adjusted to mirror the emotion distribution in the dataset, adding depth to the experience.

### Results and Performance Evaluation

The team tested three versions of the fine-tuned model—MusicGen-Small, Medium, and Large—each exhibiting varying improvements over the base model in capturing mood. The model's output was evaluated using metrics such as the Contrastive Language-Audio Pretraining (CLAP) score, which measures audio relevance to the intended emotion. Additionally, precision-recall and Hamming scores validated that the music aligned with targeted emotional states.

### Future Directions

This research demonstrates a new frontier in AI-assisted mental health care, with the potential for Music Medicine to serve as a bridge between formal therapy sessions. The team plans to conduct user studies to assess the model's effectiveness and work on more fluid transitions between emotional states for an even more natural experience. As AI continues to evolve, such innovations point to a future where technology enhances well-being through immersive potentially multi-sensor, emotionally resonant interventions.

### Aknowledgements

This work, titled Language Models for Music Medicine Generation, was collaboratively developed by Emmanouil Nikolakakis, Joann Ching, Emmanouil Karystinaios, Gabrielle Sipin, Gerhard Widmer, and Razvan Marinescu. 
