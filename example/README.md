# TDD Example

This directory contains a minimal example of Traceable Document Development (TDD).

The example concerns a fictional research group deciding how to protect its project files against accidental loss and other events that could make the working files unavailable.

During the discussion, the group considered how its synchronized working location should relate to recovery. External guidance was then checked to identify backup practices relevant to that decision.

## Files

- `DSR.md` records the current Document State used to generate the document.
- In this Markdown/BibTeX example, `references.bib` records external sources used to verify source-dependent claims in the DSR.
- `document.md` is the resulting reader-facing document.

Read `DSR.md` first, inspect the external-source trace in `references.bib`, and then compare the DSR with `document.md`.

The example illustrates several points:

- The DSR contains the current claims and decisions, not the full exploratory dialogue.
- External information used for verification is preserved in `references.bib`.
- Source-dependent DSR claims trace to that registry using `\cite{key}`.
- A citation in the DSR records verification provenance; it does not require the final document to display the citation.
- External evidence can support the basis of a decision without being the source of the decision itself.
- Negative Knowledge can record a claim rejected through external verification so that it does not reappear during later generation.
- The document is generated from the current Document State but does not reproduce the DSR item by item.
- Unresolved implementation questions can remain in the DSR without being presented as resolved facts in the document.
- The final document can be checked in both directions: DSR → Document and Document → DSR.

The external source in this example is real and was checked against the official CISA publication. The research group and its decision are fictional.

This example is intended only to demonstrate the TDD workflow. It is not intended as a complete backup policy or as technical guidance for a particular organization.