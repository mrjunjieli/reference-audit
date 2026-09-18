# Independent multi-agent verification

Use this workflow by default for reference audits. Explicit user requests for a single-agent or limited audit take precedence. Use internal subagents, not new user-visible tasks. Do not claim independence unless separate agents actually completed their checks.

## Assign work without leaking conclusions

The coordinator extracts the complete bibliography, verifies PDF extraction against rendered pages, assigns stable IDs, and maintains a coverage ledger. Give each verifier the original entry text and structured transcription, source page/context when available, the skill and source-strategy instructions, and the same requested scope. Ask verifiers to flag possible transcription mistakes. Do not give either verifier the other's findings or the coordinator's suspected verdict before their first pass is saved. Use fresh contexts (for example, `fork_turns="none"`) with explicit skill paths and raw inputs.

Assign two distinct agents to every entry:

- Verifier A resolves identifiers and prioritizes publisher, official proceedings, and primary records.
- Verifier B independently searches title/author and checks work identity, all material metadata, and formal-publication status. Independently open the supporting records; checking A's report alone is not an independent pass.

Both agents perform the complete field and version checks required by this skill. Their different discovery routes are intended to expose wrong DOI targets and missed formal versions, not to divide fields between them. Prefer distinct authoritative records where available; disclose when both rely on the same underlying source. Do not invent a second source merely to claim diversity.

For long lists, use matching bounded batches in two lanes; queue batches within available concurrency. Each ID must occur in both lanes. Keep agent outputs in separate files or messages so one cannot overwrite the other. The coordinator can check extraction, coverage, and report assembly while verifiers run. Do not consume a slot with an idle third reviewer.

## Required verifier result per entry

Return the ID, original text, matched work/version, verified fields, proposed category and secondary flags, exact evidence URLs mapped to supported fields, formal-version search and outcome, unresolved conflicts/access limits, and any transcription concern. For unsuccessful searches, record the queries and sources attempted. Distinguish direct source observations from inference. A URL without an opened supporting record is not verified evidence.

Each verifier saves its first-pass results before receiving other findings. Retain those results when subsequent review changes a verdict.

## Reconcile using evidence

The coordinator compares the two passes field by field. Reopen primary evidence for every disagreement, suspected fabricated entry, substantive correction, and proposed replacement of a preprint with a formal version. Agreement alone does not validate a high-impact claim. For remaining agreed entries, verify that the evidence mapping and coverage are complete; spot-check source support and widen the recheck if a shared error is found.

If a disagreement remains after direct rechecking, assign a fresh adjudicator agent only the original entry and disputed question for an initial independent check, then supply the competing evidence for reconciliation. Bound adjudication to one additional pass per unresolved issue; retain unresolved status rather than retrying until agents agree. Do not decide by majority vote, average confidence, or unsupported certainty.

Keep an unconfirmed entry or field visibly unresolved; failure to find a work is not proof of fabrication. If the five headline categories cannot describe an access-limited entry honestly, place it in a separate unresolved bucket and include it in the total reconciliation. Explain whether the gap concerns existence, metadata, or formal publication.

## Completion and fallback

Maintain one ledger row per input ID: A complete, B complete, evidence links, agreement/dispute, adjudication if needed, final outcome, and remaining limits. Require complete dual coverage before describing the audit as fully independently reviewed. Verify original count, unique IDs, final category totals (including unresolved), and overlapping formal-version flags.

If an agent fails, retry its affected batch once or reassign it to another available agent. If subagents are unavailable or still fail, finish useful checks, explicitly report single-agent/partial coverage and affected IDs, and do not claim the multi-agent quality gate passed. Missing evidence remains a disclosed limit rather than an invented link.

In the delivered report, state actual agent roles, dual-review coverage (N of total), disagreements and how evidence resolved them, unresolved items, and shared-source/access limitations. Multiple agents reduce some errors but do not guarantee correctness or independent source data.
