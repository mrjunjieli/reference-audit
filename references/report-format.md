# Full audit and correction format

Scale the output to the request. A short list can be answered inline; a manuscript-wide audit should produce a reviewable Markdown report and, when requested, a corrected bibliography file.

## Report structure

1. Scope: source file, page/section, reference range, count, verification date, and citation-style assumptions.
2. Overall conclusion: counts by mutually exclusive category.
3. Priority corrections: substantive errors and ambiguous records with direct evidence.
4. All-entry table with direct evidence for every row, including basically correct entries.
5. Corrected citations or BibTeX.
6. Review process: actual agent roles, independent dual-review coverage, resolved disagreements, and unresolved IDs.
7. Verification limits: inaccessible pages, unconfirmed publication status, and whether citation-to-claim support was outside scope.

Recommended all-entry columns:

| ID | Existence | Author/title match | Year/venue | Pages/article no. | DOI/identifier | Verdict | Evidence and supported fields |
|---|---|---|---|---|---|---|---|

Every row must link to at least one exact authoritative or primary record. In the evidence cell, name the source and state which fields it verifies. Add a second source when the first does not support all material fields. Do not omit evidence merely because the entry is basically correct.

For an ambiguous record, name each source and the differing field. Avoid forcing it into a false binary result.

## Preprints with formal versions

Include a separate “Formal version available—update citation” list and count. For every affected entry, show the original arXiv citation, the verified formal publication, the official evidence, and a ready-to-use formal citation. This version-update count is a secondary flag and may overlap headline categories; do not add it to the mutually exclusive total. An accurate preprint record can still require this update under the user's formal-version preference.

In corrected BibTeX, retain existing keys and any explicitly required entry-type convention, but update the publication metadata to the verified formal version. Do not leave `arXiv preprint` as the primary publication description or put a preprint DOI in the formal DOI field. An optional arXiv link may remain as an access link. Where no formal version is confirmed, state that result instead of implying publication does not exist.

## Recommended correction block

For each problem entry include:

- Current text or field.
- Verified metadata.
- Why it is wrong, incomplete, or ambiguous.
- Direct official/primary evidence link for each suggested change, with the exact fields supported by that source.
- Recommended citation in the user's requested style.

When presenting a corrected citation, identify whether it came from an official citation export or was reconstructed from verified fields. A reconstructed citation must retain the field-to-source mapping so the recommendation can be independently reproduced.

## Article numbers in BibTeX and audit reports

For a real article whose verified locator is 103104, `pages = {103104}` is a valid conventional BibTeX representation. If the bibliography renders `pp. 103104`, do not count it as a substantive bibliographic error: the identifier is correct and the prefix comes from the style. Recommend `Art. no. 103104` only as a style-dependent improvement; retain the existing representation when the required template supports or produces it. The same applies to locators such as 101027.

Do not move an article number into `number` (usually the journal issue) or `eid` without checking the actual style's support. Keep factual corrections, missing information, and optional formatting suggestions separate in report totals. If a classification is corrected after user feedback, reconcile the summary and all-entry table.

## IEEE and `@misc`

Respect a user's uniform `@misc` convention. Use standard fields that leave enough locating information in the rendered bibliography:

```bibtex
@misc{key,
  author        = {...},
  title         = {{Protected Product or Paper Title}},
  howpublished  = {arXiv preprint arXiv:1234.56789},
  year          = {2026},
  eprint        = {1234.56789},
  archivePrefix = {arXiv},
  doi           = {10.48550/arXiv.1234.56789},
  note          = {doi: 10.48550/arXiv.1234.56789},
  url           = {https://arxiv.org/abs/1234.56789}
}
```

For formally published work kept as `@misc`, put the venue plus pages/article number in `howpublished`; include the publisher DOI. Some versions of `IEEEtran.bst` ignore an independent `doi` field for `@misc`, so put `doi: ...` in `note` when the user requires the DOI to appear. Compile-test rather than assuming fields render.

Protect acronyms, model names, and intentional capitalization with braces: `{Qwen3-Omni}`, `{SpeakerLLM}`, `{ArcFace}`, `{CoLMbo}`, `{CN-Celeb}`. Use TeX accent escapes if the target BibTeX engine does not reliably accept UTF-8.

Do not place `et al.` as literal prose in an `author` field. Use the full author list when practical or the BibTeX sentinel `and others` when deliberate truncation is required. A corporate author needs braces, for example `author = {{KimiTeam} and others}`, but only use that representation when it matches the selected metadata convention.

## Validation

- Count generated entries and ensure keys are unique.
- Run the actual BibTeX/BibLaTeX style when available and require no parser errors or warnings attributable to the new file.
- Inspect the rendered `.bbl` or PDF for title casing, author order/truncation, page/article labels, DOI visibility, and URL duplication.
- Reconcile report totals with the complete table, confirm every row has direct evidence, and confirm every corrected field and recommended citation is traceable to its supporting source.
