# The moving parts

Outcome: a map of the four parts inside
every Mermaid diagram — the source, the
parser, the layout engine, and the
renderer — so that when a later chapter
names a behaviour, you know which part
produced it.

## The source

A Mermaid diagram begins as text. The
first line names the **diagram type** —
`flowchart`, `sequenceDiagram`,
`classDiagram`, and so on — and every
line after it adds one element: a box,
an arrow, a message, a relationship.
The source is the diagram (chapter 1's
rule), and it is also the only part
you write by hand. Everything else is
machinery that reads it.

The family the lab's version carries —
read from the installed package itself
(`mermaid-lab/transcripts/t00-version.txt`),
not from memory — includes flowcharts,
sequence, class, state, ER, Gantt,
pie, user journey, and git graph, and
also newer families this guide does
not teach: mindmap, timeline, sankey,
quadrant and XY charts, C4, and more.
Chapters 5 to 9 teach the established
families, each with a lab render.

Two small pieces of machinery can sit
inside the source itself. A
**frontmatter** block at the very top,
between `---` lines, can carry
configuration such as the theme
(chapter 6 renders one for real). And
lines beginning with `%%` are
**comments**: the parser ignores them,
so they are the place to explain a
diagram to its next reader without
changing the picture.

## The parser

The **parser** reads the text and
checks it against the grammar of the
named diagram type. Each family has
its own grammar — the lines that are
legal in a flowchart are not the lines
that are legal in a sequence diagram —
which is why an error in one family
can sound cryptic to a reader of
another (chapter 14). If the text does
not parse, there is no picture: the
renderer reports an error instead.
This guide's lab rendered every example
in the guide from its source file, so
every source in `mermaid-lab/diagrams/`
is one the parser accepted.

## The layout engine

You say what connects to what. You do
not say where anything sits. The
**layout engine** reads the parsed
structure and decides positions: which
box goes above which, how arrows route
around the boxes between them, how
wide the picture becomes. For
flowcharts Mermaid uses an automatic
graph layout; sequence diagrams lay
their participants out in the order
you name them and stack messages in
the order you write them.

This is the part new readers argue
with, and it is not negotiable per
node: there is no syntax for "put this
box here". Chapter 14 treats this as
the tool's first honest limit. The
practical consequence belongs here
too: to change the picture, you change
the text — reorder lines, rename a
node, split one diagram into two —
and let the engine lay it out again.

## The renderer

The **renderer** draws the laid-out
diagram, most often as **SVG** — a
text-based vector image format that
stays sharp at any size and can be
styled with the themes in chapter 6 —
or as **PNG**, a fixed-resolution
bitmap for places that cannot take
SVG. Mermaid is a JavaScript library,
so something must run that JavaScript:
a browser, a Markdown renderer that
embeds one, or the `mmdc` command-line
tool, which drives a headless Chromium
browser behind the scenes. "Rendering
needs a browser engine" is not a
metaphor; chapter 3's install is large
for exactly that reason, and chapter
14 lists it among the limits.

Check: name the four parts in order —
source, parser, layout engine,
renderer — and say which one decides
where a box sits. If you can, later
chapters have somewhere to hang.
