# The neighbours

Outcome: you can place Mermaid among
the other ways of drawing diagrams
honestly — which jobs its neighbours
do better, and which of its parts they
leave to you. These tools are
characterised from their own
documentation and reputations here,
not benchmarked; the lab ran Mermaid
only.

## Drawing tools: Visio, Lucidchart, draw.io

The canvas editors are Mermaid's
opposite number. They give you the
thing Mermaid refuses: exact placement
of every box, pixel-level control,
freeform drawing that is not any
diagram grammar at all. For a poster,
an annotated floor plan, a one-off
figure whose arrangement *is* the
content, they are the right tool.
Their costs are chapter 1's costs:
the file is a picture with a project
file behind it, versions do not diff
as text, and review means opening the
editor. Choose a canvas when placement
is the point; choose text when the
diagram will be reviewed and revised
like code.

## Graphviz: the engine's ancestor

**Graphviz** and its DOT language came
first, and Mermaid's flowcharts are
its descendant in spirit: describe
nodes and edges in text, let a layout
engine place them. DOT gives finer
control over layout and a very mature
engine, at the price of a syntax aimed
at graphs alone — no sequence
diagrams, no Gantt, no journey — and a
less forgiving hand for beginners.
Mermaid's layout owes its honesty to
the same bargain: the engine decides,
in both tools. Choose Graphviz for
large, dense graphs where its engine
and controls earn their keep; choose
Mermaid for the family of ordinary
diagrams inside documents.

## PlantUML: the other text family

**PlantUML** is Mermaid's closest
neighbour: diagrams as text, many
families, a long history in software
teams, and a particularly deep UML
offering — class and sequence diagrams
with more of the formal notation than
Mermaid attempts. It renders through a
Java-based server or local install
rather than a JavaScript library, so
its embedding story differs: GitHub
does not render PlantUML fences the
way it renders Mermaid's. Choose
PlantUML where formal UML precision
or an existing PlantUML estate decides
it; choose Mermaid where the diagram
must render inside Markdown with no
extra server.

## D2 and the rest of the text family

**D2** is a newer text-to-diagram
language with its own layout engines
and a polish aimed at software
architecture diagrams. It is
characterised here, not run. The
family resemblance is the point of
naming it: diagram-as-code is now a
category, and the differences among
its members — syntax taste, diagram
families, embedding — are smaller
than the difference all of them share
against the canvas: the text is the
diagram.

## Spreadsheets and slide shapes

A Gantt chart in a spreadsheet and a
flowchart in slide shapes are the
neighbours nobody chose on purpose.
They work until the diagram must
change twice, be reviewed by someone
without the file, or live beside the
code it describes — the three jobs
this guide exists for. Nothing here
mocks them; chapter 12 builds Mermaid
versions of exactly those jobs, and
the comparison makes itself.

Check: name the job — pixel-exact
one-off figure, dense hundred-node
graph, formal UML, diagram inside a
Markdown file — and the neighbour (or
Mermaid) you would pick for each. If
the Markdown job lands on Mermaid for
the embedding reason, you have this
chapter.
