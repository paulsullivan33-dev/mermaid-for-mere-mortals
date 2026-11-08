# Troubleshooting

Outcome: the failures every Mermaid
user meets once, each with the check
that names it. Every one of these
follows from a behaviour the lab ran
or a limit chapter 14 states, and the
fix is a chapter that already exists —
this page is the index of mishaps.

## "It will not render at all"

A syntax error means no picture: the
parser stops and the renderer reports
an error instead (chapter 2). The
lab's deliberate break is on record
(`mermaid-lab/transcripts/t04-error.txt`):
a missing closing brace on line 2 was
reported as "Parse error on line 3 …
Expecting 'DIAMOND_STOP' … got
'PIPE'", with exit code 1 and no
output file — the reported position is
where the parser gave up, one line
*after* the mistake (chapter 14).
Work small. Comment out half the source
with `%%` lines, render, and narrow
down to the line the parser rejected. The usual first mistakes: a label
containing a character the grammar
reserves, such as an unquoted
parenthesis or semicolon inside node
text; an arrow typed with the wrong
count of dashes; a keyword from the
wrong family. Quote labels, copy arrow
forms from a working example in
`mermaid-lab/diagrams/`, and change
one thing per render.

## "mmdc fails before it even reads my file"

That is the browser engine, not your
diagram. In a sandbox or a container,
Chromium commonly refuses to start
without `--no-sandbox`; the lab's
answer is the Puppeteer config file
from chapter 3, passed with `-p` on
every command (chapter 11). If `mmdc`
cannot be found at all, the install
did not finish or its `node_modules/.bin`
is not where you are standing —
chapter 3's version check
(`mmdc --version`) separates "not
installed" from "installed but the
diagram is wrong" in one command.
Run it first, always.

## "The picture is not the layout I wanted"

It never is, the first time — and
there is no drag handle to fix it
with (chapters 2 and 14). The levers
that exist are textual: change the
direction (`TD` to `LR`), reorder the
lines that define nodes, group a stage
into a subgraph, shorten the longest
labels, or split the diagram in two.
Change one lever, render, look. If
three rounds of levers do not help,
the honest answer is usually the
split.

## "It renders here but not there"

Two renderers, two Mermaid versions.
A newer diagram family — or newer
syntax in an old one — meets an older
renderer and fails there while the
lab's `mmdc` draws it happily
(chapters 10 and 14). The check is
version against version: what the
lab ran is recorded in
`mermaid-lab/transcripts/t00-version.txt`;
what a given site runs is that site's
business. The defences are to stick to
the long-established families for
documents that travel, and to export
an image file (chapter 11) for any
audience whose renderer you do not
control.

## "The PNG is huge or tiny"

PNG is a bitmap: its size is chosen,
not discovered. Set it on purpose —
`-s` scales the render (the lab's
`-s 2` exactly doubled the basic
flow, 252 × 799 to 504 × 1598), and
`--size` caps the maximum width or
height — and pick a background with
`-b` when the picture will sit on
something other than white
(`transparent` is a legal value).
Older write-ups mention `-w` and `-H`
flags; this version's `--help` has
neither, and neither does this guide.
SVG has none of these problems and
stays the default wherever SVG is
accepted; reach for PNG settings only
where PNG is required. Both settings
and the measured sizes are recorded
in
`mermaid-lab/transcripts/t02-cli-options.txt`.

## "The diagram is right but the system is not"

The most expensive entry on this page
has no command in it. The diagram
showed the structure you claimed
(chapter 14); the system drifted; the
neat picture kept testifying for the
old system. The fix is process, not
syntax: diagrams live beside the code
and documents they describe, their
diffs get reviewed with the change
that caused them, and a diagram nobody
will maintain gets deleted before it
starts lying with confidence.

Check: pick any diagram in
`mermaid-lab/diagrams/`, break one
line on purpose, run the chapter 3
version check and then the render, and
watch the error arrive. Fix the line
and render clean. If you can separate
"tool broken" from "source broken"
that way, you have this chapter.
