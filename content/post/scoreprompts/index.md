---
title: ScorePrompts - Explaining Music Scores with Large Language Models
subtitle: Ask about a passage and follow the answer back to the score.

# Summary for listings and search engines
summary: The ISMIR 2026 Late-Breaking Demo pairs structured music analysis with passage-specific questions, natural-language descriptions, and notation-linked evidence.

projects: []

date: "2026-04-08T00:00:00Z"
lastmod: "2026-11-08T00:00:00Z"

draft: false
featured: false
math: false

image:
  caption: 'ScorePrompts interface and project identity'
  focal_point: ""
  placement: 2
  preview_only: false

authors:
- admin

tags:
- Large Language Models
- Symbolic Music
- Music Analysis
- Hugging Face

categories:
- Music Information Retrieval
- Generative AI
---

You upload a score and ask what changes between measures 14 and 18. A paragraph about the passage can get you started. If it mentions a change of key or a cadence, I want to find that claim in the notation and see what the analysis system actually predicted.

That is the motivation behind **ScorePrompts**. The first version focused on generating descriptions at different levels of detail. The version Gerhard Widmer and I describe in our ISMIR 2026 Late-Breaking Demo also lets you ask about specific passages and inspect the analysis behind the answer. It uses the same score-aligned data for the descriptions, the questions, and the notation view. [Try the live demo](https://huggingface.co/spaces/manoskary/scoreprompts) · [Read the demo paper](https://arxiv.org/abs/2609.13291) · [Browse the code](https://github.com/manoskary/scoreprompts)

## Ask about a passage

After uploading and analyzing a MusicXML score, try asking **“What changes in measures 14–18?”** The question router reads the measure range and looks up the analysis for that passage. A question about a cadence or a change of harmony can bring in finer detail from the beat or note rows. The answer gives you a short explanation, the measures it refers to, and the supporting rows. It also surfaces disagreements or missing information when they matter.

For supported questions, this lookup and response happen without another language-model call. The router works over a score-level index, so a question can span more than one of the chunks used to produce the written descriptions. That matters when a phrase starts near the end of one chunk and resolves in the next. [Question routing in the demo paper](https://arxiv.org/html/2609.13291v1#S3.SS3)

## Follow the answer back to the notation

The Verovio view renders the score with reconstructed Roman numerals. You can go to a measure cited in the answer, select a note, and see its pitch, timing, analytical labels, and available confidence values. The same note identifiers appear in the underlying analysis, so the notation and table refer to the same events.

I find this useful when the measure-level reading smooths over something that matters at beat level. You can inspect the disagreement and decide which interpretation fits the passage. If you want to revise the annotation itself, the [AnalysisGNN post](/post/analysisgnn/) walks through that workflow. [Notation-linked inspection in the demo paper](https://arxiv.org/html/2609.13291v1#S3.SS4)

## How the evidence is built

Partitura loads the symbolic score as note events. AnalysisGNN estimates harmony, key, cadences, phrase and section boundaries, and the role of individual notes. We reconstruct Roman numerals and aggregate predictions at beat and measure level. AlgoMus-derived texture descriptors, jSymbolic-style features computed with music21, and score metadata add context.

The system packages overlapping ranges of measures with explicit field definitions and codebooks for categorical values. The score-level index retains access to all decoded chunks and longer trajectories such as key changes and cadences. A generated description can work with compact data, while the interface can still retrieve the specific analytical rows behind a claim. [Evidence alignment in the demo paper](https://arxiv.org/html/2609.13291v1#S3.SS1)

## From analysis to explanation

We divide description generation into three stages.

1. The **compiler** turns each chunk into structured facts tied to measures.
2. The **planner** combines those facts with piece-level information to organize an account of the score.
3. The **writer** produces coarse, detailed, and expert descriptions from that plan.

The stages operate on the analytical data and follow schemas for their outputs. We check references against the evidence index. If a stage produces malformed structured data, the system can retry or use a deterministic summary. Separating these steps also gives me a way to inspect where a claim came from. If a description puts a cadence in the wrong place, I can check the upstream prediction, the compiled facts, and the text separately. [Constrained generation in the demo paper](https://arxiv.org/html/2609.13291v1#S3.SS2)

## What I use it to explore

The same pipeline can build datasets that pair symbolic scores with structured analyses and descriptions at several levels of detail. In the demo, I’m more interested in what happens when you work through one score. Start with the overview, ask about a passage you know, and check the answer against the notation. The most informative cases are often the ones where the analysis is uncertain or the note and measure views disagree. The language system inherits the quality and coverage of those upstream estimates, which is why I want the intermediate results to stay visible.

[Open ScorePrompts](https://huggingface.co/spaces/manoskary/scoreprompts) · [ISMIR 2026 Late-Breaking Demo entry](/publication/scoreprompts-ismir-2026/)
