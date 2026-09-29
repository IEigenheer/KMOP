This repository contains a scientific paper written in LaTeX.

Rules:
- Never invent references.
- Never invent experimental results.
- Verify references before adding them.
- Add references to references.bib.
- Use \cite{} correctly.
- Maintain academic writing style.
- Preserve consistency between sections.
- Compile the LaTeX project after significant changes.
- Report compilation errors.
- Do not modify numerical results unless explicitly requested.

# References

- references.bib is maintained with Zotero + Better BibTeX, and Codex may also edit it when the user authorizes this or when a verified source PDF is already available under papers/.
- Before adding an entry, check references.bib for an existing citation key, title, DOI, or arXiv identifier to avoid duplicates.
- Verify bibliographic fields against the source paper in papers/ or an authoritative publication record. Do not infer missing authors, titles, DOIs, venues, pages, or publication dates; omit unverified fields and tell the user when the source does not establish them.
- Use citation keys that exist in references.bib and cite them with \cite{}.
- Never invent references, citations, authors, titles, DOIs, or publication data.
- Keep Zotero-generated entries intact when adding a manually verified entry. Do not overwrite or reformat unrelated entries.
- If a required source cannot be found in papers/ or verified from an authoritative record, mark the citation as pending and tell the user instead of fabricating it.

## Scientific writing workflow

- Treat the user's observations as research intuitions to be examined, not as claims to repeat verbatim. Translate them into academic arguments only when the cited evidence supports the claim, and state the scope and limitations of that evidence.
- Build the argument from the literature: explain what a source establishes, how that evidence bears on the paper's claim, and what it does not establish. Place citations next to the claims they support; do not use citations as decorative lists or attach them to unrelated generalizations.
- Preserve the user's hypotheses that do not yet have supporting sources as explicit, provisional hypotheses for later literature review and empirical testing. Do not present them as findings, silently remove them, or convert them into source-backed conclusions without evidence.
- Develop the manuscript as a coherent scientific article over successive revisions. Avoid author-motivation anecdotes, progress diary language, generic template sections, and claims of planned contributions when a source-grounded argument can be written. Do not invent results to make the manuscript appear complete.
- When revising, identify the substantive changes for the user and distinguish evidence-based claims from the user's open hypotheses.
