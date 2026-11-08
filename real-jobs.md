# Real jobs

Outcome: three complete jobs assembled
from the earlier chapters — a process
documented for new staff, a request
line explained to its own listeners,
and a small system's shape kept beside
its description — each one a source in
the lab that rendered for real.

## Job 1: the lending flow, documented

The audience is a new desk volunteer
who will ask "what happens when the
book is not there?" The job is
chapters 4 to 6 assembled: the basic
flow (`flowchart-basic.mmd`), the hold
steps grouped in a subgraph
(`flowchart-subgraph.mmd`), and the
styled copy (`flowchart-styled.mmd`)
for the printed handout, where the
happy path is green because the text
beside it says so. The document keeps
the `.mmd` sources; the handout gets
the PNG. When the library changes its
hold policy, one line of text changes
and both renders are re-run — the
whole job costs an edit, not a redraw.

## Job 2: the request line, explained

The audience is the radio station's
listeners, on a web page about how
requests work. The job is chapter 7's
pair: the sequence (`sequence-radio.mmd`)
for *how a request travels*, and the
left-to-right flow
(`flowchart-directions.mmd`) for *what
happens to it*, ending at "song plays".
The page carries both as Markdown
fences (chapter 10), so the station
volunteer who edits the page edits the
diagrams in the same sitting, in the
same file, with no image tool involved.
The Gantt chart of the Saturday build
(`gantt-radio.mmd`) hangs off the same
page for the volunteers: when things
happen, in the family chapter 9 built
for the question.

## Job 3: the small system, kept honest

The audience is whoever maintains the
library's records next year. The job
is chapter 8's trio kept together in
one document: the class diagram
(`class-library.mmd`) for the nouns,
the state diagram (`state-book.mmd`)
for one book's life, and the ER
diagram (`er-library.mmd`) for the
tables. Kept beside the description
they illustrate — in the same
repository, reviewed in the same
diffs — they are the cheapest accurate
documentation this guide knows how to
make. Left in a drawer, they become
chapter 14's warning with pictures.
The job includes its own maintenance
rule, written into the document:
*when the system changes, the diagram
in this folder changes in the same
commit, or it is deleted.* A diagram
with a deletion rule stays honest
longer than one with only good
intentions.

## What the three jobs share

Each job kept the source as the
deliverable and the picture as a
printout (chapter 1). Each chose its
family by the question being asked —
order, timing, shape — not by habit.
And each one's evidence is the same:
the sources and renders in
`mermaid-lab/diagrams/`, produced by
the commands in the transcripts, open
to anyone who wants to re-run them.

Check: choose one process you explain
to other people more than twice a
year. Write its flowchart from chapter
4's grammar, render it, and put the
source where the explanation lives.
If the next change to that process
would cost you one edited line, the
job is set up the way this chapter
means.
