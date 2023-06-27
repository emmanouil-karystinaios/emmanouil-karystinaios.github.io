---
title: "Automatic Note-Level Score-to-Performance Alignments in the ASAP Dataset"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here 
# and it will be replaced with their full name and linked to their profile.
authors:
- Silvan Peter 
- Carlos Cancino-Chacón
- Francesco Foscarin
- Andrew Philip McLeod
- Florian Henkel
- admin
- Gerhard Widmer

# Author notes (optional)
-- author_notes:
- ""
- ""

date: "2023-06-26T00:00:00Z"
doi: "10.5334/tismir.149"

# Schedule page publish date (NOT publication's date).
publishDate: "2023-06-26T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["2"]

# Publication name and optional abbreviated publication name.
publication: In *Transactions of the International Society for Music Information Retrieval*
publication_short: In *TISMIR*

abstract: "Several MIR applications require fine-grained note alignments between MIDI performances and their musical scores for training and evaluation. However, large and high-quality datasets with this kind of data are not available, and their manual creation is a very time-consuming task that can only be performed by field experts. In this paper, we evaluate state-of-the-art automatic note alignment models applied to dataset generation. We increase the accuracy and reliability of the produced alignments with models that flexibly leverage existing annotations such as beat or measure alignments. We thoroughly evaluate these segment-constrained models and use the best to create note alignments for the ASAP dataset, a large dataset of solo piano MIDI performances beat-aligned to MusicXML scores. The resulting note alignments are manually checked and publicly available at: https://github.com/CPJKU/asap-dataset. The contributions of this paper are four-fold: (1) we extend the ASAP dataset with reliable note alignments, thus creating (n)ASAP, the largest available fully note-aligned dataset, comprising more than 7 M annotated notes and close to 100 hours of music; (2) we design, evaluate, and publish segment-constrained models for note alignments that flexibly leverage existing annotations and significantly outperform automatic models; (3) we design, evaluate, and publish unconstrained automatic models for note alignment that produce results on par with the state of the art; (4) we introduce Parangonada, a web-interface for visualizing and correcting alignment annotations."

# Summary. An optional shortened abstract.
summary:  This paper introduces the (n)-ASAP dataset, a dataset with note level alignment annotations.

tags: []

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
# links:
# - name: HAL
#   url: https://hal.archives-ouvertes.fr/hal-03031287/document

url_pdf: 'https://transactions.ismir.net/articles/10.5334/tismir.149'
url_code: 'https://github.com/CPJKU/asap-dataset'
url_dataset: 
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: ''
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects:
- []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---

