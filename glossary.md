# Glossary

The terms, collected in one place.
Each is defined the way this guide
uses it.

**Activation** — In a sequence diagram,
the bar on a participant's lifeline
showing it is busy handling a request;
switched on by `->>+` or `activate`,
off by `-->>-` or `deactivate`.

**Cardinality** — In class and ER
diagrams, how many of each side a
relationship allows: one, many, zero
or more — written `"1"`, `"*"`, or in
the ER symbols such as `||--o{`.

**Diagram as code** — A diagram whose
source is plain text and whose picture
is generated from that text on demand,
so it can be diffed, reviewed, and
versioned like code.

**Direction** — The way a flowchart
flows, set by the letters after
`flowchart`: `TD`/`TB` down, `LR`
across, `RL` back across, `BT` up.

**Edge** — An arrow (or plain line)
between two nodes in a flowchart;
carries an optional label such as
`|Yes|`.

**Entity** — In an ER diagram, a table
of the database being described, with
its columns listed in a block.

**Frontmatter** — A configuration
block at the very top of a diagram
source, between `---` lines, carrying
settings such as the theme with the
diagram itself.

**Layout engine** — The part of
Mermaid that decides where each
element sits in the picture, given
what connects to what. Automatic, and
not adjustable per node.

**mmdc** — The command of the
mermaid-cli tool: a text source file
in, an SVG or PNG image file out,
drawn by a headless Chromium.

**Node** — One box in a flowchart,
named by an ID (`A`) and shown with a
label (`[Ask for the book]`); its
brackets choose its shape.

**Parser** — The part of Mermaid that
reads a source and checks it against
the grammar of its diagram type. No
parse, no picture.

**Participant** — One column of a
sequence diagram: a person (`actor`)
or a system (`participant`) exchanging
messages over time.

**PNG** — A bitmap image format:
fixed resolution, sized by settings,
for places that cannot take SVG.

**Renderer** — The part of Mermaid
that draws the laid-out diagram into
an image, most often SVG or PNG.

**State** — In a state diagram, one
condition a thing can be in
(`OnShelf`, `OnLoan`); arrows between
states are transitions, labelled with
the event that causes them.

**Subgraph** — A named box around a
group of flowchart nodes, grouping a
stage of a process and keeping it
together in the layout.

**SVG** — A text-based vector image
format: sharp at any size, the
default output of `mmdc` and the
format themes style most fully.

**Theme** — A named palette applied
to a whole diagram at once — the
classic five are `default`, `forest`,
`dark`, `neutral`, `base`, and the
lab's version adds `neo` and the
`redux` family — set in configuration,
frontmatter, or with `mmdc -t`.

Check: pick any three terms and use
each in a sentence about a diagram
you have rendered. If the sentences
hold, the vocabulary of the guide is
yours.
