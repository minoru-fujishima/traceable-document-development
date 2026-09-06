# TDD Example

This directory contains a minimal example of Traceable Document Development (TDD).

The example concerns a simple decision to move a weekly meeting from Monday morning to Tuesday afternoon.

## Files

- `DSR.md` records the current Document State used to generate the document.
- `document.md` is the resulting reader-facing document.

Read `DSR.md` first, then compare it with `document.md`.

The example illustrates several points:

- The DSR records claims, supporting information, limitations, and selected Negative Knowledge.
- The document is generated from the current Document State, but it does not reproduce the DSR item by item.
- Negative Knowledge can constrain generation without appearing in the final document.
- A claim introduced during document generation should be returned to the DSR before being retained in the document.
- The final document can therefore be checked in both directions: DSR → Document and Document → DSR.

During review of this example, the plan to continue tracking attendance appeared in `document.md` before it existed in the DSR. It was therefore added to the DSR as B03 before being retained in the final document. This illustrates the Document → DSR direction of the workflow.

This is a fictional minimal example intended only to demonstrate the TDD workflow. It is not intended to represent a real team or meeting.
