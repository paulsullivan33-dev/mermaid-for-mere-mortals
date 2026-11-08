# Styling and themes

Outcome: you can colour individual
nodes, define a reusable style class,
and set a whole-diagram theme — and
you know, from chapter 1's rule, where
styling must stop.

## Style one node

A `style` line after the flowchart
body recolours one node by ID. From
`flowchart-styled.mmd`, the lending
flow with its start, success, and
detour picked out:

```text
flowchart TD
    A[Reader asks for a book] --> B{Is it on the shelf?}
    B -->|Yes| C[Check the book out]
    B -->|No| D[Place a hold]
    C --> E[Reader takes the book home]
    style A fill:#dbeafe,stroke:#1d4ed8,stroke-width:2px
    style C fill:#dcfce7,stroke:#15803d,stroke-width:2px
    style D fill:#fef9c3,stroke:#a16207,stroke-width:2px
```

`fill` is the inside colour, `stroke`
the border colour, both written as hex
values. The rendered SVG shows exactly
those three nodes coloured and the
rest in the default theme. The
information rule applies with full
force: the green on "check the book
out" says "the happy path" only
because this chapter says so in words.
Colour that is never explained in text
is decoration, and decoration that
looks like meaning is worse than none.

## A class of nodes

When several nodes share a style,
define it once with `classDef` and
apply it with `class`:

```text
    classDef ending fill:#fee2e2,stroke:#b91c1c
    class E ending
```

The same file uses both mechanisms —
direct `style` lines for one-offs, a
named class for a category — which is
the ordinary pattern: classes for
meanings that repeat ("every ending",
"every warning"), direct styles for a
single emphasis.

## The whole diagram: themes

A **theme** recolours everything at
once — background, lines, text, the
default node fills. Themes are set in
**configuration**, and the portable
way to carry configuration with the
diagram is a frontmatter block at the
very top of the source. From
`flowchart-themed.mmd`, rendered in
the lab with the theme applied:

```text
---
config:
  theme: forest
---
flowchart LR
    A[Request arrives] --> B[Host checks the playlist]
    B --> C[Song is queued]
    C --> D[Song plays on air]
```

The theme names the lab's version
accepts — read from `mmdc --help`
itself, not from memory — are
`default`, `forest`, `dark`, `neutral`,
and `base`, plus a newer set: `neo`,
`neo-dark`, and the `redux` family
(`redux`, `redux-dark`, `redux-color`,
`redux-dark-color`). The transcript
(`mermaid-lab/transcripts/t05-themes.txt`)
records the full list as this build
prints it. The classic five are the
ones this guide uses; the newer names
are listed so the help text holds no
surprises. Compare `flowchart-themed.svg`
with the same flow rendered under the
default theme and the difference is
entirely in palette — same words, same
arrows, same layout. That is the
healthy relationship between theme and
diagram, and the chapter's point:
a theme change that changes what a
diagram *says* has gone wrong.

## Where styling stops

Three honest boundaries. First,
styling syntax is flowchart grammar —
sequence and the other families take
themes, but not per-node `style` lines
of this form. Second, there is still
no per-node positioning: colour is
yours, placement is the engine's
(chapters 2 and 14). Third, a theme
chosen for one output can fail in
another — a dark theme on a printed
page, a light theme on a dark slide.
Render to the medium the reader will
actually use, and check that render.

Check: add a `classDef` for decision
diamonds to the basic lending flow,
apply it to node `B`, render, and
confirm only the diamond changed
colour. Then switch the file's theme
to `dark` in frontmatter and render
again. If the words and arrows are
unchanged in both renders, styling
stayed in its place — and you have
this chapter.
