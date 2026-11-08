# Flowcharts in depth

Outcome: you can build a flowchart
with the common node shapes, the four
directions, labelled and styled edges,
and a subgraph that groups a stage of
a process — each shown in a source the
lab rendered.

## Shapes are punctuation

A node's shape comes from the
brackets around its label. The shape
is punctuation, not decoration: a
diamond conventionally asks a
question, a stadium shape starts or
ends a flow, a database cylinder holds
stored data. The lab's shape tour,
`mermaid-lab/diagrams/flowchart-shapes.mmd`,
renders one of each in a row:

```text
flowchart LR
    A[Rectangle - a step]
    B(Rounded rectangle - an event)
    C([Stadium - a start or end])
    D{Diamond - a decision}
    E[[Subroutine - a named process]]
    F[(Database - stored data)]
    G((Circle - a connector))
    H>Flag - a note]
    A --> B --> C --> D --> E --> F --> G --> H
```

The rendered SVG
(`flowchart-shapes.svg`, beside the
source) shows all eight shapes
distinctly. The full shape list is
longer than any one guide needs; these
eight cover ordinary process diagrams,
and chapter 1's rule applies to the
rest — a shape earns its place when
its meaning is one the reader already
knows, not because it was available.

## Direction

The two letters after `flowchart` set
the flow's direction: `TD` (top to
down; `TB` is the same), `LR` (left to
right), `RL` (right to left), and `BT`
(bottom to top). Direction is a
property of the whole diagram, not of
an edge. The radio request flow in
`flowchart-directions.mmd` reads left
to right, the way a timeline does:

```text
flowchart LR
    Start([Request line opens]) --> Take[Take the request]
    Take --> Check{In the playlist?}
    Check -->|Yes| Queue[Queue the song]
    Check -->|No| Suggest[Suggest an alternative]
    Suggest --> Queue
    Queue --> Play([Song plays])
```

Pick the direction that matches how
the reader will scan: down for a
procedure, across for a timeline or a
pipeline.

## Edges: labels, arrows, and weight

An edge can carry a label (`-->|Yes|`),
end without an arrowhead (`---`), be
dotted for a weaker link (`-.->`), or
be thick for the main path (`==>`).
Use these sparingly and consistently:
one dotted edge meaning "sometimes"
is information; five kinds of arrow
with no key is noise. The lab's
examples stick to plain arrows and
labelled arrows, and that restraint is
deliberate — the text must say it
(chapter 1), and an arrow style nobody
can read says nothing.

## Subgraphs group a stage

A **subgraph** draws a box around a
group of nodes and names the stage
they belong to:

```text
flowchart TD
    subgraph Desk["At the desk"]
        A[Ask for the book] --> B[Search the catalogue]
    end
    subgraph Shelf["At the shelf"]
        C[Fetch the book] --> D[Bring it to the desk]
    end
    B --> C
    D --> E[Check the book out]
```

Edges can cross subgraph boundaries,
as `B --> C` and `D --> E` do. A
subgraph is layout as much as meaning:
the engine keeps the group together,
which makes subgraphs the honest way
to influence a layout you otherwise
do not control (chapter 14) — you are
still changing the text, not dragging
boxes.

Check: take the basic lending flow
from chapter 4, turn it `LR`, and put
the two hold steps in a subgraph named
"Holds". Render it. If the group sits
together and every arrow from chapter
4 survived, you have this chapter.
