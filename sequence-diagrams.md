# Sequence diagrams

Outcome: you can draw who says what to
whom, in order — participants,
messages, replies, activation, and
notes — with two examples the lab
rendered.

## Time runs down the page

A **sequence diagram** shows a
conversation over time. Each
**participant** gets a column; time
runs downward; each horizontal arrow
is one **message**, in the order
written. The community radio station's
request line, in
`mermaid-lab/diagrams/sequence-radio.mmd`:

```text
sequenceDiagram
    participant Listener
    participant Host
    participant Playlist
    Listener->>Host: Phones in a song request
    Host->>Playlist: Looks up the song
    Playlist-->>Host: Found, track 12
    Host-->>Listener: Playing it next
```

The grammar in four lines of messages:

- `participant` names a column, in
  left-to-right order.
- `->>` is a solid arrow: a message
  sent, a request, a call.
- `-->>` is a dashed arrow: a reply.
- The words after the colon are the
  message text, printed beside the
  arrow.

Read top to bottom, the picture tells
the story in the order it happens —
which is exactly what a flowchart
cannot do, and why this family exists.

## The lending desk, with the extras

The second example,
`sequence-lending.mmd`, uses the rest
of the everyday grammar:

```text
sequenceDiagram
    actor Reader
    participant Desk as Front Desk
    participant Catalogue
    participant Shelf
    Reader->>+Desk: Asks for a book by title
    Desk->>Catalogue: Search by title
    Catalogue-->>Desk: Shelf mark B-14
    Desk->>Shelf: Fetch the book
    activate Shelf
    Shelf-->>Desk: Book in hand
    deactivate Shelf
    Note over Desk,Reader: The loan is recorded before handover
    Desk-->>-Reader: Here is your book, due in 3 weeks
```

- `actor` draws a participant as a
  stick figure — a person, as opposed
  to a system.
- `participant Desk as Front Desk`
  gives a participant a short ID to
  type and a long name to display.
- `->>+` switches the receiver's
  **activation bar** on; `-->>-`
  switches it off. The bar shows who is
  busy handling a request. Explicit
  `activate` / `deactivate` lines do
  the same job around several
  messages.
- `Note over A,B: text` places a note
  spanning the named participants —
  the place for a fact about the
  conversation that is not itself a
  message.

Loops, alternatives, and optional
blocks exist (`loop`, `alt`, `opt`)
and follow the same pattern of a
keyword, a label, and an `end`. They
are named here so the manual is not a
surprise; the lab's examples stay with
the grammar above, and criteria.md
keeps that boundary honest.

Check: write the sequence for a
returned book — reader, desk,
catalogue — in four messages, using
one reply arrow and one note. Render
it. If time reads downward and the
reply is dashed, you have this
chapter.
