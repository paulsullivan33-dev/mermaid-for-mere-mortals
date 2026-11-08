# The command line: mmdc at work

Outcome: you can drive `mmdc` beyond
the one basic render — output formats,
backgrounds, scale, themes from the
command line, PDF, and whole Markdown
files — using only options this
guide's lab actually ran.

## The shape of every command

```text
mmdc -p puppeteer-config.json -i <input> -o <output>
```

`-i` is the input, `-o` the output,
and the output's ending chooses the
format: `.svg`, `.png`, or `.pdf`.
`-p` points at the Puppeteer config
from chapter 3; leave it off on a
machine where Chromium launches
without it. Everything below adds one
option at a time to that shape. The
full list the lab worked from is the
`--help` text in
`mermaid-lab/transcripts/t00-help.txt`;
this chapter teaches the options it
ran and names the boundary in
criteria.md.

## Backgrounds: -b

PNG and SVG outputs sit on a
background, white by default. `-b`
sets it:

```text
mmdc -p puppeteer-config.json -i flowchart-basic.mmd -o basic-transparent.png -b transparent
```

The lab ran exactly that (transcript
`t02-cli-options.txt`). `transparent`
is a legal value, and the one to use
when a picture will sit on a coloured
slide or page: a white box around a
diagram on a dark slide is the
signature of the default nobody
changed.

## Scale and size: -s and --size

A PNG's dimensions are decided at
render time. The basic lending flow at
the default scale came out at
252 × 799 pixels; the same source at
`-s 2` came out at exactly double,
504 × 1598 (transcript `t02`). Scale
is the dial when a PNG is too small to
read where it will be shown. `--size`
takes the other approach — a maximum
width or height, from which the tool
works out the rest — and chapter 15
points at both when a reader's PNG is
the wrong size. SVG needs neither: it
scales without loss, which is why SVG
is this guide's default and PNG the
format of places that refuse SVG.

## Themes from the command line: -t

Chapter 6 set a theme inside the
source, where it travels with the
diagram. `-t` sets one from outside,
for a render whose source you are not
changing:

```text
mmdc -p puppeteer-config.json -i flowchart-basic.mmd -o basic-dark.svg -t dark
```

The lab's dark render's node colours
differ from the default render's, and
the transcript (`t05-themes.txt`) puts
the two palettes side by side. Note
what `-t` did *not* change: the page
background stayed white, because the
background is `-b`'s job, not the
theme's. Theme and background are two
dials, and a dark diagram for a dark
page needs both turned.

## PDF, and Markdown in, images out

Two more outputs earned their place in
the lab. Ending the output name in
`.pdf` produces a real PDF (the lab's
begins `%PDF-1.4`, on record in `t02`)
— the format for sending one diagram
to someone who will print it.

And the input need not be a `.mmd`
file. Hand `mmdc` a Markdown file and
it finds every `mermaid` fence,
renders each one, and writes a copy of
the Markdown with each fence replaced
by an image link:

```text
mmdc -p puppeteer-config.json -i sample.md -o sample-out.md
Found 1 mermaid charts in Markdown input
```

The lab's run (transcript `t02`)
turned one fence into `sample-out-1.svg`
and rewrote the page around it. This
is chapter 10's two forms — live fence
and image file — with a bridge between
them: keep fences as the source, and
export images for any audience whose
renderer cannot.

Check: render the pie source
(`pie-collection.mmd`) three ways —
default PNG, `-s 2` PNG, and
`-b transparent` PNG — and compare the
pixel dimensions the way `t02` did.
If the second is exactly double the
first and the third opens without a
white box on a dark viewer, you have
this chapter.
