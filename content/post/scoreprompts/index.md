---
title: ScorePrompts - Explaining Music Scores with Large Language Models
subtitle: A grounded pipeline for turning symbolic music analysis into readable multi-level explanations.

# Summary for listings and search engines
summary: ScorePrompts combines symbolic music analysis, chunked score schemata, and a three-stage LLM pipeline to generate grounded explanations of MusicXML scores.

projects: []

date: "2026-04-08T00:00:00Z"
lastmod: "2026-04-08T00:00:00Z"

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

Large language models are getting increasingly good at talking *about* music, but they are still only as useful as the evidence we give them. Symbolic scores are dense, highly structured objects: they contain local events, larger formal patterns, and lots of contextual information that can easily get lost if we simply dump notation into a prompt and hope for the best.

That is the motivation behind **ScorePrompts**. The project is designed to analyze a score first, organize the results into a compact grounded schema, and only then ask a language model to explain what is happening. The goal is not just to generate polished prose, but to generate explanations that stay tied to musical evidence.

You can try the live demo on [Hugging Face Spaces](https://huggingface.co/spaces/manoskary/scoreprompts), and the code lives in the [ScorePrompts GitHub repository](https://github.com/manoskary/scoreprompts).

## What ScorePrompts does

At a high level, ScorePrompts takes a symbolic score in MusicXML, runs a stack of music-analysis tools on it, and turns the result into natural-language descriptions at different levels of detail.

The interactive demo is intentionally simple:

- Upload a `.musicxml`, `.xml`, or `.mxl` file.
- Choose a model endpoint for text generation.
- Run the symbolic analysis and text-generation pipeline.
- Inspect the note, beat, and bar tables.
- Read three text outputs: `coarse`, `detailed`, and `expert`.
- Download the structured outputs as CSV and JSON files.

This makes the interface approachable, but behind it there is a fairly deliberate research pipeline.

## From score to grounded schema

The first stage of ScorePrompts is not language generation at all. It is symbolic analysis.

For each uploaded score, the system extracts several complementary views:

- **AnalysisGNN** provides note-level predictions such as harmonic labels, cadence information, local key, phrase and section cues, and other symbolic descriptors.
- **Beat and bar builders** aggregate those note-level predictions into beat-wise and measure-wise tables.
- **AlgoMus texture descriptors** provide bar-level texture summaries.
- **jSymbolic** contributes global descriptors.
- **Metadata extraction** adds score-level context when it is available.

These outputs are then reduced into a chunked JSON schema. Instead of sending raw tables directly to the language model, ScorePrompts packages a consecutive range of measures together with:

- note, beat, and bar fields
- score-level metadata and global features
- embedded codebooks for categorical values
- dense note arrays aligned with explicit field lists

This schema design matters a lot. It keeps each chunk self-contained and token-efficient while preserving alignment between the musical evidence and the text-generation step.

## A three-stage LLM protocol

One of the most interesting parts of ScorePrompts is that it does not ask the model to jump straight from score data to a finished essay.

Instead, it uses a three-stage protocol:

1. **Compiler**: turns a schema chunk into grounded, measure-level facts.
2. **Planner**: combines those facts with global metadata to build a canonical plan of sections, tonal motion, cadences, and salient events.
3. **Writer**: converts the plan into three outputs with different levels of detail: `coarse`, `detailed`, and `expert`.

This decomposition helps in two ways. First, it makes the reasoning path more inspectable. Second, it gives the pipeline a chance to validate intermediate outputs before they become polished language.

In the codebase, these JSON outputs are validated with Pydantic schemas, and the compiler stage is additionally checked for grounding against the available musical evidence. That makes ScorePrompts much more interesting to me than a generic "score captioning" demo: the project is trying to make symbolic music explanation **structured, inspectable, and reproducible**.

## Why the demo is useful

The Gradio demo is not just a nice wrapper around the pipeline. It is a useful research instrument in its own right.

It gives a quick way to:

- test how different scores behave under the same analysis stack
- inspect intermediate note, beat, and bar tables
- compare generated descriptions across abstraction levels
- debug grounding issues before scaling up to batch runs

For responsiveness, the public-facing demo focuses on the **first chunk** of a score by default. That design choice keeps the interaction fast while still showing the full path from score upload to structured analysis to generated explanation. If you want to cover more measures, the interface exposes controls such as the bars-per-chunk setting.

## More than a demo: a dataset and pipeline

ScorePrompts is also a dataset-building pipeline.

The repository is set up to build a reproducible corpus pairing symbolic scores with:

- note-, beat-, bar-, and global-level analyses
- chunked schemata stored as JSONL
- multi-stage LLM artifacts
- multi-tier natural-language descriptions

That makes it useful for more than one application. I see it as infrastructure for:

- grounded music description
- analysis-to-text generation
- educational music explanation
- alignment-aware symbolic music generation
- research on how LLMs can talk about structure in music without drifting away from evidence

This is one of the reasons I like the project: it treats explanation not just as UI copy, but as a data and modeling problem.

## Current limitations

ScorePrompts is promising, but it is also important to be honest about what it depends on.

- The quality of the final text depends on the fidelity of the upstream symbolic analyses.
- Missing or weak metadata limits what the writer stage can say reliably.
- The chunked design improves tractability, but it also means that long-range structure has to be reconstructed carefully.
- The interactive demo is only a preview of the full batch pipeline.

Those limitations are not accidental edge cases; they are part of the research problem. In my view, that is what makes ScorePrompts interesting: it pushes toward explanations that are not only fluent, but also auditable.

## Closing thoughts

ScorePrompts sits at a point that I find especially exciting right now: between symbolic music analysis, dataset construction, and language-model interfaces. It is a practical demo, but it is also a way of asking a deeper question:

**What would it take for language models to explain music scores in a way that remains grounded in musical structure?**

That is the question ScorePrompts is built around. If you would like to explore it yourself, you can start with the [live demo](https://huggingface.co/spaces/manoskary/scoreprompts) or browse the implementation in the [GitHub repository](https://github.com/manoskary/scoreprompts).

```bash
conda activate analysisgnn
python apps/prompt_gradio.py
```

I expect this line of work to keep evolving, especially as the dataset side becomes richer and the connection between symbolic evidence and generated prose becomes easier to inspect, validate, and compare.
