---
title: Slides
summary: On Performance Similarity and Structure Segmentation.
authors: [Emmanouil Karystinaios]
tags: Department of Computational Perception
categories: []
date: "2021-02-05T00:00:00Z"
slides:
  # Choose a theme from https://github.com/hakimel/reveal.js#theming
  theme: black
  # Choose a code highlighting style (if highlighting enabled in `params.toml`)
  #   Light style: github. Dark style: dracula (default).
  highlight_style: dracula
---

## On Performance Similarity and Structure Segmentation

[Emmanouil Karystinaios](emmanouil-karystinaios.netify.app) | [article](emmanouil-karystinaios.netify.app)

<!-- [Wowchemy](https://wowchemy.com/) | [Documentation](https://owchemy.com/docs/managing-content/#create-slides) -->

---

## Introduction

Our objective is to find a way to quantify similarity of performances for which we have a matched score.
But first, we have to answer the following questions :
- What is performance similarity
- How to measure siilarity in match scores?
- Which similarity metric to use ?
- Why measure performance similarity?
- What elements affect our perception of performance similarity?

---

## Self-Similarity Matrices

The concept of self-similarity matrices is fundamental for
capturing structural properties of music recordings. Generally,
one starts with a feature space L containing the elements of
the feature sequence under consideration as well as with a
similarity measure $f : \mathcal{L} \times \mathcal{L} \to \mathbb{R}$.

---

## Controls

- Next: `Right Arrow` or `Space`
- Previous: `Left Arrow`
- Start: `Home`
- Finish: `End`
- Overview: `Esc`
- Speaker notes: `S`
- Fullscreen: `F`
- Zoom: `Alt + Click`
- [PDF Export](https://github.com/hakimel/reveal.js#pdf-export): `E`

---

## Interval Vectors

**_Definition_**
: An interval vector is an array of natural numbers which summarize the intervals present in a set of pitch classes. There is an equivalence between complementary intervals within the octave for example $2^{nd}$ minor and $7^{nth}$ major intervals, etc.

Examples :
- Any Major chord : $ [0, 0, 1, 1, 1, 0 ] $
- Any Minor chord : $ [0, 0, 1, 1, 1, 0 ] $

---
### Interval Vectors and Cadences

|      **Typical Cadences**			|  			|
|---								|---		|
| $\textrm{V}$ & - & $\textrm{I}$ 	| authentic |
|$\textrm{I}$ & - &  $\textrm{V}$ 	| half 		|
|$\textrm{IV}$ & - & $\textrm{I}$ 	| plagal 	|
|$\textrm{V}$  & - & $\textrm{VI}$ 	| deceptive |


Interval Vectors are commutative, i.e. $\textrm{V} \to \textrm{I} = \textrm{I} \to \textrm{V} $:
- $ (\textrm{V/I})_{maj} = [1, 2, 2, 2, 3, 0] $
- $ (\textrm{V/I})_{min} = [2, 1, 2, 3, 2, 0] $ 


---

## Code Highlighting

Inline code: `variable`

Code block:
```python
porridge = "blueberry"
if porridge == "blueberry":
    print("Eating...")
```

---

For every window $w_i^j$ we compute the interval vector of all notes in thye window/ Therefore, $\textrm{Int\_Vec}(w_i^j)\in \mathbb{N}^6$.
$$
\mathcal(W) = \sum_{i=1}^N\sum_{j=1}^\nu \textrm{Int\_Vec}(w_i^j)
$$
Then, let $\mathcal{X}$ be some matrix decomposition of $\mathcal{W}$. The SSM $\mathcal{S}$ of $\mathcal{X}$ is:
$$ 
\mathcal{S} = \frac{\mathcal{X} \cdot \mathcal{X}}{\| \mathcal{X} \|^2}
$$

---

## Test


\begin{tikzpicture}
  \matrix (m) [matrix of math nodes,row sep=3em,column sep=4em,minimum width=2em]
  {
     F & B \\
      & A \\};
  \path[-stealth]
    (m-1-1) edge node [above] {$\beta$} (m-1-2)
    (m-1-2) edge node [right] {$\rho$} (m-2-2)
    (m-1-1) edge node [left] {$\alpha$} (m-2-2);
\end{tikzpicture}

---

## Fragments

Make content appear incrementally

```
{{%/* fragment */%}} One {{%/* /fragment */%}}
{{%/* fragment */%}} **Two** {{%/* /fragment */%}}
{{%/* fragment */%}} Three {{%/* /fragment */%}}
```

Press `Space` to play!

{{% fragment %}} One {{% /fragment %}}
{{% fragment %}} **Two** {{% /fragment %}}
{{% fragment %}} Three {{% /fragment %}}

---

A fragment can accept two optional parameters:

- `class`: use a custom style (requires definition in custom CSS)
- `weight`: sets the order in which a fragment appears

---

## Speaker Notes

Add speaker notes to your presentation

```markdown
{{%/* speaker_note */%}}
- Only the speaker can read these notes
- Press `S` key to view
{{%/* /speaker_note */%}}
```

Press the `S` key to view the speaker notes!

{{< speaker_note >}}
- Only the speaker can read these notes
- Press `S` key to view
{{< /speaker_note >}}

---

## Themes

- black: Black background, white text, blue links (default)
- white: White background, black text, blue links
- league: Gray background, white text, blue links
- beige: Beige background, dark text, brown links
- sky: Blue background, thin dark text, blue links

---

- night: Black background, thick white text, orange links
- serif: Cappuccino background, gray text, brown links
- simple: White background, black text, blue links
- solarized: Cream-colored background, dark green text, blue links

---

{{< slide background-image="blue_background.jpg" >}}

## Custom Slide

Customize the slide style and background

```markdown
{{</* slide background-image="/media/boards.jpg" */>}}
{{</* slide background-color="#0000FF" */>}}
{{</* slide class="my-style" */>}}
```

---

## Custom CSS Example

Let's make headers navy colored.

Create `assets/css/reveal_custom.css` with:

```css
.reveal section h1,
.reveal section h2,
.reveal section h3 {
  color: navy;
}
```

---

# Questions?

[Ask](https://github.com/wowchemy/wowchemy-hugo-modules/discussions)

[Documentation](https://wowchemy.com/docs/managing-content/#create-slides)
