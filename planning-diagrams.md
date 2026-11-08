# Planning diagrams: Gantt, pie, journey, and git graph

Outcome: four smaller families, each
the right picture for one kind of
question — when things happen, how a
whole divides, how an experience
feels, and how branches of work
merged — each rendered in the lab.

## Gantt: the schedule as bars

A **Gantt chart** draws tasks as bars
against dates. The radio station's
Saturday build, from `gantt-radio.mmd`:

```text
gantt
    title Community radio - Saturday schedule build
    dateFormat YYYY-MM-DD
    section Prep
    Collect requests      :a1, 2026-11-02, 2d
    Check music licences  :a2, after a1, 1d
    section Broadcast
    Morning show          :b1, 2026-11-07, 1d
    Request hour          :b2, after b1, 1d
    section Wrap up
    Log the playlist      :c1, after b2, 1d
```

Each task line gives a name, an ID
(`a1`), a start — a date, or `after`
another task's ID — and a duration
(`2d`, two days). `section` groups the
bars under a heading. The honest
framing matters: this is a picture of
a plan, drawn from the dates in the
text. It is not a project manager —
nothing tracks progress, warns about
overruns, or knows the plan changed
unless someone edits the text.

## Pie: how a whole divides

A **pie chart** is the smallest family
in the guide. From `pie-collection.mmd`:

```text
pie title Library collection by section
    "Fiction" : 420
    "Non-fiction" : 280
    "Children" : 180
    "Reference" : 70
    "Audio" : 50
```

Label, colon, number. The renderer
works out the proportions and the
percentages. A pie shows parts of one
whole and nothing else — no trend, no
comparison between two wholes — and
within that limit it is the fastest
diagram in this guide to write and to
read.

## User journey: how it felt, step by step

A **user journey** diagram scores each
step of an experience. From
`journey-reader.mmd`:

```text
journey
    title A reader borrows a book
    section Find it
      Search the catalogue: 5: Reader
      Walk to the shelf: 3: Reader
      Ask at the desk: 4: Reader, Staff
    section Borrow it
      Check the book out: 5: Reader, Staff
      Carry it home: 4: Reader
```

Each step line carries a score from 1
to 5 and the actors involved. The
render draws a path whose height
follows the scores — the dip at "walk
to the shelf" is the finding, and it
is visible across the room. The score
is someone's judgement written down,
not a measurement; the diagram's job
is to make that judgement discussable.

## Git graph: branches, drawn

A **git graph** draws the shape of a
version history — commits, branches,
merges — the way `git log --graph`
does in text. From
`gitgraph-docs.mmd`:

```text
gitGraph
    commit id: "Draft chapters"
    commit id: "Add diagrams"
    branch review
    checkout review
    commit id: "Fix wording"
    checkout main
    merge review id: "Reviewed"
    commit id: "Publish"
```

This guide uses it to sketch a planned
branching story — in teaching, in a
proposal, in documentation. It draws
the history you describe; it does not
read a real repository, and a graph
drawn from memory can disagree with
the repository exactly the way chapter
14 warns about.

Check: pick the question — when, how
much of the whole, how it felt, or how
the branches went — and name the
family that answers it. Then change
one number in the pie source, render
again, and watch every slice resize.
If it did, you have this chapter.
