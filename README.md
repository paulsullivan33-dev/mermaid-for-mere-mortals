# Mermaid for Mere Mortals

Every team has the diagram problem.
Someone draws the process in a picture
editor, the picture goes into the
document, and then the process changes.
The picture does not. Redrawing it is a
session of dragging boxes and untangling
arrows, so it happens late, or never,
and the document goes on showing a
system that no longer exists. And when
two versions of the picture meet in a
review, nobody can say what changed —
pictures do not diff. **Mermaid** takes
the drawing away: you write the diagram
as plain text, and a program draws the
picture whenever one is needed.

One rule governs everything it does,
and this guide states it in chapter 1
and keeps pointing back to it: **the
text is the diagram — the picture is a
printout.** If the words and arrows do
not say it, no amount of styling will,
and anyone who can read the source can
fix the diagram. The picture is
regenerated from the text every time;
the text is the work, the work is
reviewable, and a change to a diagram
is one readable line in a diff.

The lab behind this guide ran the real
thing: **mermaid-cli 12.2.0** (`mmdc`,
installed with npm on Node v24,
bringing the Mermaid 12.x library and
a headless Chromium to draw with),
against two small fictional fixtures —
a library's book-lending flow and a
community radio station's request
line. Against those fixtures the lab
wrote fifteen diagram sources and
rendered every one of them for real,
to both SVG and PNG: the lending
flowchart in its plain, grouped, and
styled forms; a tour of node shapes; a
themed render whose frontmatter the
renderer obeyed; two sequence diagrams
with activation and notes; class,
state, and ER diagrams of the same
small library; and a Gantt chart, a
pie chart, a user journey, and a git
graph. It measured the CLI as well —
a scale-2 PNG exactly twice the pixels
of the default, a transparent
background, a dark-theme render, a PDF,
and a Markdown file whose diagram
fence the tool extracted and replaced
with an image — and it broke one
diagram on purpose to record what a
parse error actually looks like.

What the lab could not do, it did not
fake. Nothing was pushed to GitHub, so
GitHub's own rendering of Mermaid
fences is described from GitHub's
documentation and labelled
documented-only; the neighbours in
chapter 13 are characterised, not run.
`criteria.md` keeps the full ledger of
what was run and what was only read.

## What this guide covers

- [**What Mermaid is**](what-mermaid-is.md) —
  the picture that never gets redrawn,
  diagram as code, and the one rule
- [**The moving parts**](the-moving-parts.md) —
  the source, the parser, the layout
  engine, and the renderer
- [**Installing Mermaid**](installing-mermaid.md) —
  the npm install, its honest size, the
  version check, and the sandbox fix
- [**Your first diagram**](your-first-diagram.md) —
  one flowchart written by hand,
  rendered, and read back against its
  source
- [**Flowcharts in depth**](flowcharts-in-depth.md) —
  shapes as punctuation, directions,
  edges, and subgraphs
- [**Styling and themes**](styling-and-themes.md) —
  one node, a class of nodes, a whole
  theme — and where styling must stop
- [**Sequence diagrams**](sequence-diagrams.md) —
  who says what to whom, in order, with
  activation and notes
- [**Structure diagrams**](structure-diagrams.md) —
  class, state, and ER diagrams of one
  small library
- [**Planning diagrams**](planning-diagrams.md) —
  Gantt, pie, user journey, and git
  graph, one family per question
- [**Diagrams in Markdown**](diagrams-in-markdown.md) —
  the live fence on GitHub and in
  MkDocs, and when an image file wins
- [**The command line**](the-command-line.md) —
  `mmdc` beyond the basic render:
  backgrounds, scale, themes, PDF, and
  Markdown in, images out
- [**Real jobs**](real-jobs.md) —
  a process documented, a request line
  explained, a small system kept honest
- [**The neighbours**](the-neighbours.md) —
  canvas editors, Graphviz, PlantUML,
  and D2, characterised honestly
- [**Limits**](limits.md) — the layout
  you do not control, the grammar per
  family, the claim that is not the
  system, and the browser engine
- [**Troubleshooting**](troubleshooting.md) —
  the render that fails, the browser
  that will not launch, and the layout
  that is not the one you wanted
- [**Glossary**](glossary.md) — the
  terms, collected in one place

## What it doesn't cover

Formal UML beyond the everyday class
and sequence grammar, the newest
diagram families (mindmap, timeline,
sankey, and the rest are named in
chapter 2 and left to the manual), and
building your own renderer or editor
integration — this guide uses Mermaid
where it already lives: the command
line, Markdown, and documentation
sites. Nothing here draws anyone's
real network or organisation: every
example is one of the two invented
fixtures.

## How to use this guide

Read chapter 1 for the rule and
chapter 2 for the map of parts;
chapter 4 gets a real diagram rendered,
and chapters 5 to 9 teach the families
one question at a time. Chapter 14 is
the one to read before a diagram
matters, not after: the layout is the
engine's, and the picture shows the
structure you claimed. The lab's
diagram sources and their renders live
in `mermaid-lab/diagrams/`, its
Puppeteer config in `mermaid-lab/`,
and every claim's evidence in
`mermaid-lab/transcripts/`; its
distilled commands are
`examples/commands.txt` and its notes
`examples/lab-notes.txt`.

---

## Part of the series

This guide is one of the [For Mere Mortals](https://paulsullivan33-dev.github.io/mere-mortals/) guides: plain-language guides to the tools programmers and makers use.

Related guides:

- [Markdown for Mere Mortals](https://paulsullivan33-dev.github.io/markdown-for-mere-mortals/)
- [Text Processing for Mere Mortals](https://paulsullivan33-dev.github.io/text-processing-for-mere-mortals/)
- [Git for Mere Mortals](https://paulsullivan33-dev.github.io/git-for-mere-mortals/)

## License

The writing in this guide is licensed under [CC BY 4.0](https://github.com/paulsullivan33-dev/mermaid-for-mere-mortals/blob/main/LICENSE). Code examples and lab scripts are licensed under the [MIT License](https://github.com/paulsullivan33-dev/mermaid-for-mere-mortals/blob/main/LICENSE-CODE).
