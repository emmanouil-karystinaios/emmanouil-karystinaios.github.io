---
title: "EngravingGNN: A Hybrid Graph Neural Network for End‐to‐End Piano Score Engraving"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here 
# and it will be replaced with their full name and linked to their profile.
authors:
- admin
- Francesco Foscarin
- Gerhard Widmer

# Author notes (optional)
-- author_notes:
- ""
- ""

date: "2025-09-01T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2025-09-01T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In Proceedings of the International Conference on Technologies for Music Notation and Representation (TENOR), Beijing
publication_short: In *TENOR*

abstract: This paper focuses on automatic music engraving, i.e., the creation of a humanly-readable musical score from musical content. This step is fundamental for all applications that include a human player, but it remains a mostly unexplored topic in symbolic music processing. In this work, we formalize the problem as a collection of interdependent subtasks, and propose a unified graph neural network (GNN) framework that targets the case of piano music and quantized symbolic input. Our method employs a multi-task GNN to jointly predict voice connections, staff assignments, pitch spelling, key signature, stem direction, octave shifts, and clef signs. A dedicated postprocessing pipeline generates print-ready MusicXML/MEI outputs. Comprehensive evaluation on two diverse piano corpora (J-Pop and DCML Romantic) demonstrates that our unified model achieves good accuracy across all subtasks, compared to existing systems that only specialize in specific subtasks. These results indicate that a shared GNN encoder with lightweight task-specific decoders in a multi-task setting offers a scalable and effective solution for automatic music engraving.

# Summary. An optional shortened abstract.
summary:  This paper focuses on automatic music engraving, i.e., the creation of a humanly-readable musical score from musical content. This step is fundamental for all applications that include a human player, but it remains a mostly unexplored topic in symbolic music processing. In this work, we formalize the problem as a collection of interdependent subtasks, and propose a unified graph neural network (GNN) framework that targets the case of piano music and quantized symbolic input. Our method employs a multi-task GNN to jointly predict voice connections, staff assignments, pitch spelling, key signature, stem direction, octave shifts, and clef signs. A dedicated postprocessing pipeline generates print-ready MusicXML/MEI outputs. Comprehensive evaluation on two diverse piano corpora (J-Pop and DCML Romantic) demonstrates that our unified model achieves good accuracy across all subtasks, compared to existing systems that only specialize in specific subtasks. These results indicate that a shared GNN encoder with lightweight task-specific decoders in a multi-task setting offers a scalable and effective solution for automatic music engraving.

tags: []

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
# links:
# - name: HAL
#   url: https://hal.archives-ouvertes.fr/hal-03031287/document

url_pdf: ''
url_code: ''
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

