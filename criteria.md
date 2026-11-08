# Writing criteria for this guide

Every "for Mere Mortals" guide is written to the same nine-point
standard, so a reader who trusts one can trust the rest. Here it
is, with the verification notes for this particular guide below.

1. **Fix it first.** Reader outcomes lead, not action items: each
   chapter opens by naming the outcome it delivers, shows a check
   the reader can run to confirm they got it, and a reasonable
   reader finishes able to state what was done, what it means,
   and what to try next.
2. **Plain language.** Short sentences, everyday vocabulary,
   technical terms defined on first use. No slang, and no
   idioms that only make sense in one country — the reader may
   be translating as they go.
3. **No dead ends.** A guide never tells the reader to do
   something it cannot show them how to verify. Every claim a
   reader relies on — an install, a command, an output — is
   something this guide demonstrates or clearly labels
   documented-only below.
4. **Live-verified where it matters.** Procedures are run for
   real in the guide's lab wherever the build machine allows it,
   and the transcripts kept in the repository are the evidence.
   What could not be run is listed honestly below, never
   presented as if it had been.
5. **General audiences.** Nothing in this guide — examples,
   fixtures, names, addresses — is modelled on any particular
   reader or author's real life, network, or organisations.
   The lab's traffic is the lab talking to itself.
6. **Standalone.** A reader needs this guide, its lab, and
   nothing else. Where another guide would genuinely help, it
   is pointed to once, by name, and the chapter still completes
   without it.
7. **Honest about limits.** Layout is automatic and not
   negotiable per node — you say what connects, the engine
   decides where it sits, and big diagrams sprawl; the syntax
   differs per diagram family and its errors can be cryptic,
   reporting where the parser gave up rather than where you
   went wrong; a diagram shows the structure you claimed, not
   the system you have — it cannot check itself against
   reality; and rendering needs a browser engine behind the
   library and the CLI, which is why the install carries one.
8. **The one rule is in the text, early.** Chapter 1 and the
   README state the rule plainly — *the text is the diagram;
   the picture is a printout, and if the words and arrows do
   not say it, no amount of styling will* — before any
   procedure depends on it, and later chapters point back to
   it where the rule bites: styling that pretends to be
   meaning, the layout that can only be changed by changing
   the text, and the review that reads the source.
9. **Builds clean.** The site builds with MkDocs in strict mode
   with no warnings, and a fresh reader following the chapters
   in order reaches the stated outcome of each.

## Verification notes for this guide

**Plan A was achieved: every diagram in this guide was
rendered for real.** The build machine is an Ubuntu sandbox
with Node v24.22.1 and npm 10.9.4. The lab installed the
official tools with `npm install @mermaid-js/mermaid-cli
mermaid` in a scratch project: **@mermaid-js/mermaid-cli
12.2.0** (the CLI; `mmdc --version` reports 12.2.0, and its
package declares a dependency on mermaid ^12.2.0) alongside
the **mermaid 12.3.0** library package. Puppeteer downloaded
Chromium 156 into the user cache (676 MB; `node_modules`
449 MB) — sizes kept in transcript t07 rather than hidden.
Chromium in this sandbox runs only with `--no-sandbox`, so
every render used the Puppeteer config kept in the lab
(`mermaid-lab/puppeteer-config.json`). The lab is in
`mermaid-lab/`: fifteen diagram sources with their rendered
SVG and PNG outputs in `diagrams/`, and transcripts in
`transcripts/`. Fixtures are two invented systems: a library
book-lending flow and a community radio station's request
line.

Run for real, with transcripts as evidence:

- Versions and provenance (t00): Node and npm versions, both
  package versions from their `package.json` files,
  `mmdc --version` (12.2.0), the full `--help` text (t00-help,
  33 lines — the source of every flag this guide names; there
  is no `-w`/`-H` in it, and chapter 15 says so), and the
  diagram families present in the installed package's own
  `dist/diagrams/` folder, which is where chapter 2's family
  list comes from.
- All fifteen diagrams rendered (t03): every `.mmd` in
  `mermaid-lab/diagrams/` rendered to SVG and to PNG with
  exit success — flowcharts (basic, directions, shapes,
  styled, subgraph, themed), sequence (radio, lending),
  class, state, ER, Gantt, pie, journey, and git graph.
  Every SVG was checked to be a real SVG document with no
  error text, and spot-checked labels from the sources were
  found in the pictures' SVG text (t06): "Is it on the
  shelf?", "Phones in a song request", "due in 3 weeks",
  "cardNumber", "Overdue", "Fiction", and more.
- The first render measured (t01): flowchart-basic.svg with
  its viewBox, and flowchart-basic.png at 252 × 799 pixels.
- The CLI's options (t02): `-b transparent` produced its PNG;
  `-s 2` produced 504 × 1598 — exactly double in both
  dimensions; a `.pdf` output is a real PDF (%PDF-1.4); and
  a Markdown input had its one `mermaid` fence found,
  rendered, and replaced by an image link in the output file.
- Themes (t05): the theme choices printed by `--help` (the
  classic five plus `neo` and the `redux` family); the
  frontmatter `theme: forest` render uses the theme's own
  font stack where the default render uses the CLI's
  embedded font; a `-t dark` render's node colours differ
  from the default render's while its page background stays
  white, as chapter 11 describes; and every colour named in
  `flowchart-styled.mmd` (`#dbeafe`, `#dcfce7`, `#fef9c3`,
  `#fee2e2`, and the strokes) is present in its SVG.
- The failures, kept on record: without the Puppeteer
  config, Chromium refuses to launch as root ("Running as
  root without --no-sandbox is not supported"), exit 1, no
  output (t07); and a source with a missing closing brace
  fails with "Parse error on line 3 … Expecting
  'DIAMOND_STOP' … got 'PIPE'" — one line after the actual
  mistake — exit 1, no output file (t04).

Documented only — described from the projects' documentation,
not run, and the text does not claim otherwise:

- GitHub's rendering of `mermaid` fences in Markdown, issues,
  and pull requests (chapter 10). Nothing was pushed anywhere
  for this guide, by design; the behaviour is GitHub's own
  documented feature. What was run is the local half of the
  story: `mmdc` extracting and rendering fences from a
  Markdown file (t02), and this guide's own MkDocs build
  emitting chapter 10's fence as a Mermaid block for the
  theme's browser-side rendering.
- Sequence-diagram `loop`, `alt`, and `opt` blocks: named in
  chapter 7 as following the taught pattern, not rendered.
- The CLI options the lab did not exercise: `-c` config
  files, `-C` CSS files, `-I` SVG ids, `--size` (named from
  `--help`; `-s` was the measured one), `--iconPacks`, batch
  Markdown artefacts beyond the single-fence file in t02,
  and install routes other than npm (browser embedding,
  CDN use, editor plugins).
- The neighbouring tools in chapter 13 (canvas editors,
  Graphviz, PlantUML, D2) are characterised, not run.

Fixtures are this guide's own and deliberately generic: a
library that lends books and a radio station that takes
requests, both invented. No example is modelled on any real
person, network, service, or organisation.
