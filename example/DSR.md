# Document State Register (DSR)

## Document

- **Title / Working title:** Project file backup policy
- **Purpose:** Explain the research group's current decision for protecting project files against loss or unavailability.
- **Current DSR version:** v5
- **Baseline for:** `document.md`

## Current Document State

### A. Problem and verified basis

**A01.** The research group stores active project files in a synchronized working location so that team members can access the current files.

**A02.** The group wants project files to remain recoverable if the active working files become unavailable or unusable.

**A03.** CISA recommends maintaining offline, encrypted backups of critical data and regularly testing the availability and integrity of those backups.

\cite{cisaStopRansomwareGuide}

**A04.** CISA states that maintaining backups offline is important because ransomware may attempt to delete or encrypt accessible backups.

\cite{cisaStopRansomwareGuide}

### B. Decision

**B01.** The synchronized location will remain the primary working location for active project files.

**B02.** The group will maintain a separate recovery copy in addition to the active working files.

**B03.** The recovery arrangement will include a copy that is not continuously accessible from the active working environment.

- **Rationale:** This decision is intended to apply the verified principle in A04 so that a compromise affecting accessible working files does not automatically expose every recovery copy to the same compromise.

**B04.** The group will periodically test whether its recovery copy can actually be used for recovery.

- **Rationale:** This applies the verified testing principle in A03 rather than assuming recoverability from the existence of backup data.

### C. Scope and limitation

**C01.** This decision establishes the basic separation between the active working files and a recovery copy.

**C02.** The current decision does not yet specify the backup product, storage provider, backup frequency, retention period, encryption implementation, or recovery-test schedule.

**C03.** The external guidance provides evidence for the backup principles used in the decision; the specific policy decisions in B01–B04 are decisions of the fictional research group.

## Negative Knowledge

**NK01.** “If backup data exist, successful recovery can be assumed.”

- **Disposition:** Rejected
- **Reason:** The verified guidance calls for regular testing of backup availability and integrity.

## Open / Unresolved

**U01.** Which backup system or storage location should be used.

**U02.** How frequently backups should be created.

**U03.** How long previous backup generations should be retained.

**U04.** How often recovery should be tested.

**U05.** How encryption and access control should be implemented for the recovery copy.

## Change Log

| DSR version | Change |
| --- | --- |
| v1 | Initial state: use a synchronized working location for project files |
| v2 | Added externally verified backup and recovery principles |
| v3 | Added the separate recovery copy, recovery testing, Negative Knowledge, scope limitations, and unresolved implementation questions |
| v4 | Added evidence concerning synchronized cloud copies for further verification |
| v5 | Removed the synchronized-cloud claim because it was not retained as directly verified evidence and aligned Negative Knowledge with the remaining verified basis |