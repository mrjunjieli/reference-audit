# Evidence and source strategy

Use the strongest source available for each bibliographic field. Search engines and aggregators help locate candidates, but the final verdict should cite records that are as close as possible to the publisher or authors.

## Source priority

1. **Official venue or publisher record**
   - IEEE Xplore for IEEE conferences and journals.
   - ISCA Archive for Interspeech and Odyssey.
   - ACL Anthology for ACL-family proceedings.
   - CVF Open Access and IEEE Xplore for CVPR.
   - ACM Digital Library, SpringerLink, ScienceDirect, journal sites, or official conference proceedings as applicable.
   - ICLR official proceedings/program and OpenReview for ICLR papers.
2. **Registration-agency metadata**
   - Crossref for publisher-deposited DOI metadata: <https://www.crossref.org/documentation/retrieve-metadata/rest-api/>
   - DataCite/DOI resolution for repository DOIs, including arXiv DOI records.
3. **Primary repository/version record**
   - arXiv abstract page plus the exact PDF/version.
   - Other official preprint repositories where relevant.
4. **Author or institution source**
   - Official project repository, author publication page, laboratory page, or institution publication record. Author-provided BibTeX is useful when group authorship or title versions differ.
5. **Broad scholarly indexes**
   - OpenAlex works and authors: <https://help.openalex.org/api/endpoints/>
   - Semantic Scholar Academic Graph: <https://api.semanticscholar.org/api-docs>
   - DBLP for computer-science bibliography.
   - Google Scholar for discovery and citation-export conventions when primary records are unavailable.

Do not use Google Scholar, a browser citation extension, ResearchGate, or a citation generator as the sole proof when primary records are available. Do not ignore them when the user explicitly follows that citation convention; report the convention difference.

## Evidence recording

- Give every audited entry, including a basically correct entry, at least one direct URL to the exact authoritative or primary record used to verify it. A search-results page, database home page, or unlinked source name is not sufficient evidence.
- Record which fields each source supports. For example: publisher record supports title, authors, venue, year, and locator; Crossref supports DOI registration metadata; arXiv supports the preprint title, author list, identifier, and version history.
- If one source does not expose all material fields, cite additional records rather than implying that it supports fields it does not show. Disclose conflicts between reputable sources.
- Every corrected field and ready-to-use citation must be traceable to its supporting source. Prefer an official citation export or author-provided BibTeX when available. If the citation is reconstructed from verified metadata, say so and retain the field-to-source mapping.
- Link to the most stable exact record available, such as the publisher article page, DOI landing page, official proceedings entry, or arXiv abstract page. Record a precise access limitation when no direct record can be opened.

## Resolution flow

### DOI present

1. Resolve `https://doi.org/<DOI>`.
2. Check registration metadata and publisher landing page.
3. Compare normalized title, authors, year, venue, volume/issue, and pages/article number.
4. Mark a DOI wrong only when it resolves to a different work or does not resolve after retry/cross-check. A missing publisher page caused by access controls is not a nonexistent DOI.

### arXiv identifier present

1. Open `https://arxiv.org/abs/<id>` and the cited version when supplied.
2. Inspect the PDF byline/title page if the author list or team name is disputed.
3. Check submission history and comments for later publication claims.
4. Actively search for a formal version even when arXiv comments/journal-reference fields are empty: search title plus authors, official venue/publisher archives, and registration or scholarly indexes as needed. Check plausible renamed versions against the authors and paper content.
5. Confirm formal publication using an official proceedings/publisher record or publisher-deposited metadata. Distinguish submission, acceptance, and published online-first/final versions. Do not convert a comment such as “published at...” into invented pages or a conference DOI.
6. If the same work is formally published, recommend that version instead of the preprint and collect its own complete bibliographic metadata. If multiple formal records are distinct conference/journal works, establish which corresponds to the cited work rather than automatically choosing the newest.
7. Record the outcome for each preprint: formal version found (with evidence and replacement citation), none confirmed after search, or search limited (with the specific limitation).

### No identifier

1. Search exact quoted title.
2. Search title keywords plus first author and year.
3. Query Crossref and OpenAlex; use Semantic Scholar/DBLP as additional discovery channels.
4. Search the claimed venue's official archive.
5. If only near matches exist, compare which fields diverge and classify as partial/ambiguous rather than choosing the highest fuzzy score automatically.

## Matching rules

- Normalize case, whitespace, punctuation, Unicode accents, and PDF line-break hyphenation for matching, while preserving official spelling in the correction.
- Accept subtitle and capitalization differences only when the same work/version is clear.
- Check at least the first author, author order/prefix, and total/full list when `et al.` is used.
- A title match with a different author list, venue, or DOI requires investigation; it is not automatically valid.
- A DOI match is strong identity evidence, but deposited metadata may still contain incomplete authors or pages. Compare the official PDF/landing page.

## Metadata-conflict example

A technical report may show a collective byline in its PDF, list the collective name plus individual contributors in arXiv/DBLP, and export a citation beginning with the first individual author. These are different representations of authorship. Unless the publisher or authors explicitly require one form, label the difference as a metadata convention and present the supported alternatives instead of declaring an omitted or fabricated author.

## Mature supporting tools

- **Zotero** retrieves PDF metadata using document text, Crossref, DOI, and ISBN lookup. It is useful for ingestion and cleanup, not a complete authenticity audit: <https://www.zotero.org/support/retrieve_pdf_metadata>
- **Crossref REST API** is the strongest general source for publisher-deposited DOI metadata, but coverage and field completeness vary.
- **OpenAlex** and **Semantic Scholar** provide broad discovery and cross-checking, but their merged metadata can disagree with primary sources.
- **arXiv** is authoritative for its submission metadata and version history; formal conference status must still be verified at the venue.

Community skills such as `citation-verify`, `cite-verify`, and `ref-verify` demonstrate useful multi-API pipelines. Treat them as implementation references rather than unquestioned authority; inspect their code, dependencies, licenses, and source-priority rules before installation.
