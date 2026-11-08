# Installing Mermaid

Outcome: the `mmdc` command on your
machine, proved by the version check —
and an honest account of what the
install actually downloads, because it
is larger than you expect.

## Two ways to meet Mermaid

Most readers first meet Mermaid doing
nothing at all: a diagram renders in a
GitHub page or a documentation site
they are reading (chapter 10), drawn by
JavaScript their browser already ran.
Installing something is only needed
when you want to render diagrams
yourself, from your own files, on your
own machine. For that, this guide uses
the project's official command-line
tool, **mermaid-cli**, whose command is
`mmdc`. It needs **Node.js** and its
package manager `npm` — the lab's
machine had Node v24.22.1 and npm
10.9.4.

## The route the lab used: npm

```text
npm install @mermaid-js/mermaid-cli
```

One command, two consequences the
guide will not hide. First, the
install is big: the lab's
`node_modules` came to 449 MB, and the
tool's browser engine — a full
Chromium, downloaded by the Puppeteer
library into `~/.cache/puppeteer` —
came to another 676 MB (transcript
`mermaid-lab/transcripts/t07-nosandbox-and-sizes.txt`).
That browser is not bloat; chapter 2
explained that rendering Mermaid means
running its JavaScript somewhere, and
the CLI brings its own somewhere.
Second, in a sandbox or container that
Chromium will refuse its first launch
— the next section's fix.

## The check

However you install it, the proof is
the same:

```text
mmdc --version
```

The lab's install answers `12.2.0`
(transcript
`mermaid-lab/transcripts/t00-version.txt`),
and `--help` prints the tool's full
option list — 33 lines in this version,
captured before anything else was
trusted (`t00-help.txt`). If
`mmdc --version` does not run, nothing
else in this guide will either; fix
the install before going on. Where
`mmdc` lands depends on how npm was
told to install: a project-local
install puts it in that project's
`node_modules/.bin/`, which is where
the lab ran it from, rather than
installing anything system-wide.

## The sandbox fix: --no-sandbox

Chromium refuses to run as the root
user, or inside many containers,
unless told not to use its sandbox.
The lab's first unconfigured render
failed exactly this way, and the error
names the cure:

```text
Error: Failed to launch the browser process
Running as root without --no-sandbox is not supported.
```

(transcript `t07-nosandbox-and-sizes.txt`;
exit code 1, no output file.) The cure
is a small JSON file — the lab keeps
it in the repository as
`mermaid-lab/puppeteer-config.json`:

```json
{"args":["--no-sandbox","--disable-setuid-sandbox"]}
```

and one extra flag on every `mmdc`
command in this guide:

```text
mmdc -p puppeteer-config.json -i in.mmd -o out.svg
```

On an ordinary desktop install you
will likely never need it. In any
sandboxed or containerised setting,
expect to: it is the single most
common first-run failure, and chapter
15 keeps the diagnosis.

Check: run `mmdc --version`, then
render any file from
`mermaid-lab/diagrams/` with the `-p`
flag as above. If an SVG appears,
your install is the lab's install,
and every later chapter's commands
will behave as written.
