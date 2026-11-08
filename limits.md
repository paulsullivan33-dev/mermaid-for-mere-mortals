# Limits

Outcome: the honest boundary of the
tool, in one place — what Mermaid
will not place, will not check, and
cannot render without help — so
nothing in the earlier chapters is
mistaken for a promise.

## Layout is automatic, and not negotiable per node

You say what connects. The engine
decides where it sits. There is no
syntax for moving one box two
centimetres left, and asking for one
is asking Mermaid to be a different
tool (chapter 13 names the tools that
do it). The practical consequences:
small diagrams lay out beautifully
with no effort; large ones sprawl —
a flowchart past a few dozen nodes
becomes a wall that no direction or
subgraph fully tames. The remedies are
all textual, and they are real work:
split the diagram, group with
subgraphs, shorten labels, remove the
detail that belongs in prose. When a
diagram fights its layout through
three revisions, the diagram is
usually two diagrams.

## Each family speaks its own grammar

Flowchart lines are not sequence
lines are not class lines. The syntax
differs per diagram family, knowledge
does not fully transfer between them,
and the errors can be cryptic: a
parser that expected one family's
keyword and met another's reports the
place it gave up, which is not always
the place you went wrong. Chapter 15
turns that into a procedure — one
change at a time, render often — but
it does not make the messages kind.
Budget for it: the second family you
learn costs more than the first
promised.

## The diagram shows the structure you claimed

A Mermaid diagram cannot check itself
against reality. The class diagram
does not read your code, the ER
diagram does not read your database,
the Gantt chart does not read your
calendar, and the flowchart does not
watch your process happen. Every
diagram is a claim, drawn neatly —
and a neat drawing of a stale claim
is more dangerous than a scruffy one,
because it looks maintained. The only
defences are habits: keep diagrams
beside the thing they describe, review
their diffs when the thing changes,
and delete diagrams nobody updates.
Chapter 1's rule cuts both ways:
anyone who can read the source can
fix the diagram — but someone has to.

## Rendering needs a browser engine

Mermaid is JavaScript. Something must
run a browser engine to turn text
into a picture: the reader's browser
on GitHub or a documentation site, or
a headless Chromium behind the `mmdc`
command line — which is why chapter
3's install downloads a browser and
why the CLI needs the `--no-sandbox`
setting in this guide's sandbox. In
places with no browser and no wish
for one — a minimal server, an
offline build — Mermaid diagrams stay
text until they reach a renderer that
has one. The text loses nothing by
waiting; but a workflow that promises
pictures must budget for the engine
that draws them.

## Smaller limits, stated once

Themes restyle a palette, not a
layout, and per-node styling belongs
to flowcharts, not to every family.
Hand-written SVG features — arbitrary
shapes, embedded images placed by
hand — are outside the grammar. And
Mermaid is a moving target: new
diagram families arrive between
versions, renderers ship different
versions (chapter 10), and a source
that renders in the lab's version can
meet an older renderer elsewhere that
has never heard of its diagram type.

Check: state the four limits in one
breath — layout is the engine's,
grammar is per-family, the picture
shows your claim not your system, and
a browser engine does the drawing. If
you can, no chapter in this guide has
oversold you anything.
