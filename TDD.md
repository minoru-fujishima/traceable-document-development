# Traceable Document Development (TDD)

## A Method for Creating Traceable Documents from LLM-Assisted Exploration

Traceable Document Development (TDD) is a procedure for developing
complex documents through exploratory dialogue with large language
models (LLMs). Its purpose is to make explicit a state-management
problem that arises in actual document development and to provide one
concrete way of addressing it in a form that others can examine, use,
and criticize.

A long dialogue with an LLM contains not only the ideas ultimately
adopted, but also intermediate hypotheses, incorrect explanations,
conditional claims, rejected alternatives, and understandings that were
later revised. Therefore, **information that exists in the dialogue is
not the same as information that may currently be used in the
document.**

TDD separates these two. Its central relationship is:

``` text
Dialogue → DSR ⇄ Document
```

Dialogue is used for exploration, while the current Document State is
recorded in a Document State Register (DSR). The document is generated
using the DSR as its reference, and after generation the DSR and the
document are checked against each other in both directions. When an
important change occurs, the change is returned to the DSR rather than
being made only in the document.

## 1. Minimal workflow

The basic procedure for using TDD is:

1.  **Explore freely in Dialogue.**
2.  **Extract important current claims into the DSR.**
3.  **Retain rejected claims whose reuse would be risky as Negative
    Knowledge.**
4.  **Verify claims against external information when necessary.**
5.  **Generate the Document from the latest DSR.**
6.  **Check DSR → Document.**
7.  **Check Document → DSR.**
8.  **If an important change is required, return to the DSR.**
9.  **Revise the Document from the updated DSR and check it again.**

Dialogue is used for free exploration. The object of management is not
the exploration history itself, but the current Document State extracted
from it. An LLM can assist with exploration, organization, research,
document generation, and checking, but the human decides which claims
are adopted as the current Document State.

## 2. Creating a DSR from Dialogue

In Dialogue, hypotheses can be proposed, challenged, investigated,
replaced with alternative explanations, and discarded when necessary. It
is acceptable for this stage to produce large amounts of information
that will never be used later.

Even after exploration has progressed, Dialogue still contains a mixture
of current, intermediate, unverified, and rejected claims. Generating a
document directly from that dialogue can lead to important content being
omitted, old explanations being revived, hypotheses being presented as
facts, or conditions being lost.

TDD therefore extracts from Dialogue the important content that may
currently be used in the document. This is called the **Document
State**, and its external record is called the **Document State Register
(DSR)**.

The DSR is neither a summary of the Dialogue nor an outline of the
Document. It represents **what information may currently be used to
create the document**.

The DSR records important content as numbered claims. The basic unit is
**one independently assessable claim per item**.

``` markdown
## A. Problem

A01
A long LLM Dialogue contains both currently accepted claims
and rejected claims.

A02
Information that exists in the Dialogue is not the same as
information that may currently be used in the Document.

A03
Therefore, the entire Dialogue is not treated as the current
Document State.
```

Fine-grained decomposition is not itself the objective. The DSR should
not be divided so finely that maintaining it begins to dominate the
document-development work.

The latest DSR is treated as the current Document State. Older DSR
versions and the Dialogue may remain as history, but old decisions
should not be mixed with the latest DSR when creating the current
document.

## 3. Managing claims and Negative Knowledge

Not every claim needs to be managed with the same degree of detail. When
useful, the DSR can record whether a claim is a fact or a hypothesis,
accepted or unresolved, conditional or unconditional, and how strongly
it can be stated.

The following information can also be distinguished when needed.

**Source**\
Where the information came from.

**Evidence**\
What supports the claim.

**Derivation**\
The reasoning by which the claim was derived.

**Rationale**\
Why a particular judgment or method was adopted.

``` markdown
A07
Existing method X causes problem Z under condition Y.

Evidence:
- [@reference1]

Derivation:
Measurement result P together with previous report Q
supports the conclusion that Z occurs.

Rationale:
Therefore, method X is not adopted in this document.
```

These fields are used only for claims where they are useful.

A DSR may also retain information that should **not** be adopted. A
rejected claim can remain plausible and may later reappear. In
particular, an LLM may regenerate an explanation that was previously
rejected, either from earlier Dialogue or from its general knowledge.

TDD therefore retains selected rejected content as **Negative
Knowledge** when accidental reuse would be risky.

``` markdown
NK01
"Method X completely solves problem Y."

Rejected.

Reason:
It was confirmed that the claim does not hold under condition Z.
```

When useful, **Rejected** can be distinguished from **Not Selected**.
Rejected means that a claim should not be reused because it is incorrect
or does not hold. Not Selected means that a claim may be valid but is
not adopted in the current document.

## 4. Generating a Document from the DSR

The Document is generated using the latest DSR as its reference. The
order of DSR items, however, does not have to become the structure of
the Document.

The DSR is a Document State, not an outline. Multiple DSR claims may be
integrated into one paragraph, and one important claim may be explained
across several sections. TDD fixes the content that must be preserved,
not the presentation order.

Writing the Document can reveal relationships or new claims that were
not previously explicit. This is not itself a problem. However, an
important new claim should not simply be added to the Document and
treated as established.

``` text
new claim → verification → DSR update → Document update
```

If the new claim is accepted after verification, it is added to the DSR
first. The Document State is then updated before the claim is
incorporated into the Document. This prevents important Document State
from accumulating only inside the prose.

## 5. Checking the DSR and Document in both directions

After the Document is generated, it is checked bidirectionally against
the DSR used for its generation.

### DSR → Document

For each important claim, check whether it is reflected in the Document.
The goal is not merely to find matching words, but to determine whether
the meaning has been preserved.

-   Has a required claim been omitted?
-   Has its meaning changed?
-   Has a condition disappeared?
-   Has a hypothesis become a fact?
-   Has the claim become stronger than its Evidence supports?

### Document → DSR

For each important claim in the Document, check where it is represented
in the DSR. In particular, look for the following exceptions.

-   **Missing** --- a required DSR claim is missing from the Document
-   **New / Unsupported** --- an important claim not present in the DSR
    has been added to the Document
-   **Strengthened** --- a claim has become stronger than it is in the
    DSR
-   **Contradicted** --- the Document contradicts the DSR
-   **Negative Knowledge Conflict** --- a rejected claim has reappeared
-   **Uncertain** --- the correspondence cannot be determined
    automatically and requires human review

Together, these two directions provide **bidirectional traceability**.

This checking differs from simply asking an LLM to "read it again and
look for problems." Open-ended self-critique leaves the choice of what
to inspect to the LLM. TDD instead uses the DSR as an external criterion
and makes the checking targets explicit. An LLM or other tool can be
used to identify candidate exceptions, while a human reviews the
important cases.

### Return to the DSR when a problem is found

When checking reveals a problem, not every issue should be corrected
only in the Document.

If the problem is purely one of wording or presentation, the Document
can be revised directly. If the underlying claim was wrong, a condition
was missing, Evidence changes the judgment, an important new claim is
needed, or the treatment of Negative Knowledge changes, the DSR should
be updated first.

The Document is then revised from the updated DSR and checked again.

``` text
Dialogue → DSR ⇄ Document
              ↑       |
              └───────┘
```

In TDD, returning changes in the Document State to the DSR provides the
mechanism corresponding to Change Control rather than leaving those
changes only in the prose.

## 6. Version management when needed

The DSR is a register of Document State that can continue to evolve.
When a particular Document version is generated and checked, however, a
particular DSR version is used as its reference.

That specific version is treated as the **Baseline** for the artifact.
The DSR itself and a Baseline are not the same thing.

For example, if Article v3 is generated and checked from DSR v7, then
DSR v7 is the Baseline for Article v3. Even if the DSR is later updated
to v8, it remains possible to trace which Document State was used to
create Article v3.

The same DSR can be used to generate multiple documents for different
purposes, audiences, or media. When multiple artifacts are produced,
each artifact only needs to remain traceable to the DSR version used as
its reference; the artifacts do not all need to be updated at the same
time.

## 7. External verification and document quality

TDD does not automatically establish whether the claims recorded in a
DSR are true. Claims that require verification must still be checked
against appropriate primary sources, literature, data, calculations,
experiments, rules or standards, or expert judgment.

What TDD manages is **making explicit what is currently adopted and
tracing the relationship between that Document State and the Document**.

Consistency with the DSR also does not guarantee that a Document is well
written. Readability, structure, repetition, transitions between
sections, and the amount of explanation are separate quality dimensions.
Normal document-quality review should therefore be performed when needed
even after bidirectional traceability has been checked.

If a document-quality revision does not change the Document State, the
Document can be revised directly. If it introduces a new important
claim, changes claim strength, changes a condition, or otherwise changes
the Document State, the process returns to the DSR.

## 8. Tailoring the level of management to the document

Full TDD is not necessary for every document. For a short email or a
simple edit, the cost of maintaining a DSR may exceed its benefit.

A DSR becomes more useful when the work involves a long exploratory
process, hypotheses or problem formulations change during development,
many claims or conditions must be maintained, rejected ideas are likely
to reappear, multiple versions or multiple artifacts are being produced,
or accuracy is important.

The level of management should therefore be tailored to the complexity,
importance, and risk of the document.

TDD does not require every claim to have a responsible owner, every
prompt to be saved, all Dialogue to be structured, or every claim to
contain complete Source, Evidence, Derivation, and Rationale fields.
These can be added where needed.

The purpose is not to create a larger management system. It is to keep
the current Document State explicit enough that a complex document can
be generated, revised, and checked without repeatedly reconstructing
that state from the entire Dialogue.
