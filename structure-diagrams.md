# Structure diagrams: class, state, and ER

Outcome: three diagram families that
describe what a system *is* rather
than what it *does* — classes and
their relations, the states of one
thing over its life, and the tables of
a small database — each with a
rendered example from the library
fixture.

## Class diagrams: the nouns and their links

A **class diagram** names the kinds of
thing in a system, what each holds,
what each can do, and how they relate.
From `class-library.mmd`:

```text
classDiagram
    class Book {
        +String title
        +String author
        +String isbn
        +isOnLoan()
    }
    class Reader {
        +String name
        +String cardNumber
        +borrow(Book)
        +returnBook(Book)
    }
    Reader "1" --> "*" Loan : holds
    Book "1" --> "*" Loan : appears in
```

A class block lists **attributes**
(`+String title` — public, of type
String) and **methods** (lines ending
in `()`). Below the blocks,
relationship lines carry
**cardinality** in quotes: one reader
holds many loans (`"1"` to `"*"`).
The rendered picture draws the three
boxes with their members divided by a
line, and the labelled arrows between
them. What it does not do is check
any of it against real code — chapter
14's warning in its purest form: the
diagram shows the structure you
claimed.

## State diagrams: one thing, over its life

A **state diagram** follows a single
kind of thing through the states it
can be in and the events that move it.
One library book, from `state-book.mmd`:

```text
stateDiagram-v2
    [*] --> OnShelf
    OnShelf --> OnLoan : checked out
    OnLoan --> OnShelf : returned
    OnLoan --> Overdue : due date passes
    Overdue --> OnShelf : returned late
    OnShelf --> InRepair : damaged
    InRepair --> OnShelf : repaired
    OnShelf --> [*] : withdrawn
```

`[*]` is the start (and, at the other
end, the finish). Each line is a
**transition**: from-state, to-state,
and the event after the colon. The
picture makes gaps visible in a way a
list cannot — there is no line out of
`Overdue` except "returned late", so
the diagram asks a real question: can
an overdue book go straight to repair?
If it can, the text is missing a line,
and fixing the text fixes the diagram
(chapter 1).

## ER diagrams: the tables and their keys

An **entity relationship diagram**
describes a database: which tables
exist, which columns each holds, and
which rows point at which. From
`er-library.mmd`:

```text
erDiagram
    READER ||--o{ LOAN : holds
    BOOK ||--o{ LOAN : "appears in"
    READER {
        string cardNumber PK
        string name
    }
    BOOK {
        string isbn PK
        string title
        string author
    }
```

The relationship symbols are the dense
part: `||--o{` reads "exactly one to
zero or more" — one reader, many
loans; the loan may exist in numbers
from zero up. `PK` marks a **primary
key**, the column that identifies a
row. As with class diagrams, the ER
diagram is a claim about a database,
not a reading of one: nothing here
connects to a live database to verify
it, and the chapter does not pretend
otherwise.

Check: for each of the three sources,
cover the picture and read the text
aloud, then cover the text and read
the picture. If both readings agree in
all three families, you have this
chapter.
