# What Mermaid is

By the end of this chapter you can say,
in one sentence, what Mermaid does —
and state the one rule that governs
every diagram you will ever write
with it.

## The picture you keep redrawing

Think of the last flowchart you made in
a drawing tool. You dragged boxes onto
a canvas, nudged them into line, drew
arrows that snapped to the wrong edge,
and saved a picture. Then the process
changed. You opened the picture, moved
one box, watched three arrows tangle,
re-exported the image, and replaced it
in the document — and the old picture,
the one in the email thread and the
printed handout, still shows the old
process. Worse, nobody can answer the
simplest review question — *what
changed between these two versions?* —
because pictures do not diff. Two
images sit side by side and a person
hunts for the difference by eye.

**Mermaid** removes the canvas. You
write a diagram as plain text — a list
of boxes and arrows in words — and a
program renders that text into a
picture whenever you need one:

```text
flowchart TD
    A[Reader asks for a book] --> B{Is it on the shelf?}
    B -->|Yes| C[Check the book out]
    B -->|No| D[Place a hold]
```

That text is a **diagram as code**:
the source is text, the picture is an
output. Text can be stored in version
control, reviewed line by line,
searched, and changed with an ordinary
editor. When the process changes, you
edit one line and render again. The
difference between two versions is a
text difference, readable at a glance.

## The rule: the text is the diagram

Everything in this guide follows from
one fact, so it comes first:

> **The text is the diagram — the
> picture is a printout.** If the words
> and arrows do not say it, no amount
> of styling will, and anyone who can
> read the source can fix the diagram.

The picture Mermaid draws is a
rendering, regenerated from the text
every time. It is not the work; the
text is the work. A beautiful render
of the wrong arrows is still the wrong
diagram, and a plain render of the
right words is a good diagram that
happens to be plain. Later chapters
return to this rule where it bites:
when styling tempts you to fix meaning
with colour (chapter 6), when the
automatic layout puts a box somewhere
you did not expect and the honest fix
is to change the text, not to drag the
box (chapter 14), and when a diagram
is reviewed — the reviewer reads the
source, because the source is what
will still be true next month.

The rule has a friendly side. Because
the source is readable, a diagram
never becomes a locked picture that
only its author's drawing tool can
open. A colleague who has never used
Mermaid can read the flowchart above
and correct it. That is the test this
guide keeps applying: if the words and
arrows do not say it, the diagram does
not say it either.

## What Mermaid draws

Mermaid is a free, open-source
JavaScript library. One text syntax
covers a family of diagram types —
flowcharts, sequence diagrams, class
diagrams, state diagrams, entity
relationship diagrams, Gantt charts,
pie charts, user journeys, git graphs,
and more. Chapter 2 lists the family
as the version in this guide's lab
actually carries it; chapters 5 to 9
teach each established type with an
example the lab rendered for real.

Mermaid runs in three places, and this
guide covers all three honestly.
Inside web pages and Markdown
renderers — GitHub and MkDocs Material
both draw a fenced `mermaid` code block
as a diagram (chapter 10). Inside an
editor or a documentation build, as a
library your own page loads. And from
the command line, with the official
**mermaid-cli** tool, whose command is
`mmdc`, which turns a text file into
an SVG or PNG image file you can keep
(chapter 11). The lab behind this
guide used the command-line route,
because it leaves evidence: a source
file in, an image file out, and a
transcript between them.

Check: read the flowchart at the top
of this chapter aloud as sentences —
"a reader asks for a book; is it on
the shelf; if yes, check the book
out" — and then say the rule once. If
the sentences make sense without the
picture, you have understood the only
idea the rest of the guide needs.
