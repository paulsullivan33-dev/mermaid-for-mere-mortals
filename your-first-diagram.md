# Your first diagram

Outcome: one flowchart, written by
hand, rendered to a real image file by
the real tool, and read back against
its source — the whole loop of this
guide in miniature.

## The source

The lab's first diagram is the library
lending flow from chapter 1, saved as
`mermaid-lab/diagrams/flowchart-basic.mmd`:

```text
flowchart TD
    A[Reader asks for a book] --> B{Is it on the shelf?}
    B -->|Yes| C[Check the book out]
    B -->|No| D[Place a hold]
    C --> E[Reader takes the book home]
    D --> F[Reader is notified when it arrives]
    F --> C
```

Read it as grammar, because that is
all it is:

- `flowchart TD` opens the diagram.
  `TD` is the **direction**: top to
  down. Chapter 5 shows the other
  directions.
- `A`, `B`, `C` are **node IDs** —
  short names the diagram uses to talk
  about each box. They are not shown
  in the picture.
- The words in brackets are the
  **labels** — the text the reader
  sees. `[ ... ]` draws a rectangle;
  `{ ... }` draws a diamond, the
  conventional shape for a question.
- `-->` is an **edge**, an arrow from
  the node on its left to the node on
  its right.
- `|Yes|` on an edge is the edge's own
  **label**, the word printed beside
  the arrow.

A node is defined by its first
mention and reused by its ID after
that. `C` is defined on the `Yes` line
and reused, with no label, on the last
line — same box, second arrow in.

## The render

The command-line tool renders the
source to an image (chapter 11 covers
the tool itself; this is the shape of
every render in the guide):

```text
mmdc -i flowchart-basic.mmd -o flowchart-basic.svg
mmdc -i flowchart-basic.mmd -o flowchart-basic.png
```

The lab ran exactly this pattern for
every diagram in the guide; the
transcript
(`mermaid-lab/transcripts/t01-first-render.txt`)
records the commands, and the SVG and
PNG outputs sit beside the source in
`mermaid-lab/diagrams/`. Open the SVG
and check it against the source, line
by line: a rectangle for asking, a
diamond for the question, two labelled
arrows out of it, and the hold path
curving back into checkout. Six lines
of text, six elements in the picture,
nothing in the picture that is not in
the text. That correspondence — not
the prettiness of the result — is the
success this chapter is after.

## Changing it

Now the diagram-as-code payoff. The
library adds a step: a hold also
reserves the next returned copy. One
line changes:

```text
    D --> F[Reader is notified when it arrives]
```

becomes two ideas, and the render is
re-run. In a drawing tool this change
is a canvas session; here it is a text
edit and the same command again. If
the source is kept in version control,
the change is one readable line in a
diff — the review question from
chapter 1, answered.

Check: render the source yourself and
point at the picture's diamond while
reading the `{Is it on the shelf?}`
line aloud. Then change one label,
render again, and confirm the picture
followed the text. If it did, you have
run the whole loop: text in, picture
out, text is the diagram.
