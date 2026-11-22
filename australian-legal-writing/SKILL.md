---
name: australian-legal-writing
description: >
  Draft, edit, and cite Australian legal writing: letters and letters of
  demand, advice and memos, submissions, affidavit drafts, plain-English
  contract clauses, and pointer-level privacy (APP) and Australian Consumer Law
  website text. Use for Australian (Commonwealth, state, or territory) legal
  documents, AGLC4 citations, or checking that cited Australian law is real and
  current. Never invents authorities. For structural feedback on a law
  student's own draft, use legal-writing instead.
---

# Australian Legal Writing

Write Australian legal documents that are clear, correctly cited, and built only on authorities you have checked. This skill drafts and edits. It is not legal advice, and sending, signing, swearing, filing, and serving stay with the user.

Rule tags such as `[AGLC4 r 1.4.3]` or `[UCR r 332.2]` point to entries in [references/sources.md](references/sources.md), where each source has a URL that was opened and checked.

## When to use

- Drafting or tightening an Australian letter, letter of demand, reply, advice, file memo, submission, affidavit draft, or contract clause.
- Formatting or auditing citations in AGLC4 (the *Australian Guide to Legal Citation*, 4th edition).
- Checking that a cited Act, section, or case exists, is current, and says what the draft claims.
- First-pass privacy collection notices, privacy policy outlines, or consumer-law wording for an Australian website or app.

## When not to use

- Structural feedback on a student's own memo or essay with no rewriting: use `legal-writing`.
- US, UK, or other foreign law, or Bluebook and OSCOLA citation.
- Deciding the user's legal position as final advice. Draft it, flag the open points, and recommend review by an Australian lawyer when the stakes or the uncertainty are high.
- Court forms the court prescribes. Fill in the official form; do not imitate it.

## Workflow

1. **Fix the frame before drafting.** Record jurisdiction, forum (if any), document type, reader, purpose, and the "as at" date for the law. Ask for anything that changes the law or the form, not for nice-to-haves. See "Jurisdiction". Before asking for court materials, check the forum's AI rules on what may be put into an AI tool (e.g. suppressed, subpoenaed, or compulsorily produced material in NSW `[NSW-PN23 para 9A]`).
2. **Lock the facts.** Use only the facts, dates, amounts, names, and documents the user supplied. Mark a gap `[CONFIRM: …]`; never fill it with an invented fact.
3. **Verify every authority you will rely on** using [references/verification.md](references/verification.md). Anything you cannot open goes in the notes as `[VERIFY: …]` and stays out of the document.
4. **Draft by document type** using the quick guides below and [references/documents.md](references/documents.md).
5. **Cite** in the style the document needs: AGLC4 for advice, memos, and academic work ([references/aglc4.md](references/aglc4.md)); the forum's own practice for court documents; plain identification in correspondence.
6. **Run the final checks** at the end of this file and return the output contract.

## Jurisdiction

- Australia has nine legislatures: the Commonwealth, six states, and two territories. Name the jurisdiction of every statute: `(Cth)`, `(SA)`, `(NSW)`, and so on `[AGLC4 r 3.1.3]`.
- Default to South Australia plus Commonwealth law when the user is in SA and gives no other cue, and say so in one line. Switch when the facts point elsewhere: where the parties are, the governing-law clause, the court, or where the conduct happened.
- Do not carry one state's rule, form, time limit, or label into another. State equivalents differ in wording and numbering; for example, purposive interpretation sits in *Acts Interpretation Act 1901* (Cth) s 15AA and *Legislation Interpretation Act 2021* (SA) s 14 `[AIA] [SA-LIA]`.
- Commonwealth laws that commonly govern business documents: *Competition and Consumer Act 2010* (Cth) sch 2 (the Australian Consumer Law), *Privacy Act 1988* (Cth), *Spam Act 2003* (Cth), *Corporations Act 2001* (Cth). Verify the provision before relying on it.

## Source discipline

These rules override everything else in this skill.

1. **Never invent an authority.** No made-up case, party, citation, report volume, page, paragraph, section, judge, quote, or holding. Courts have warned that generative AI produces fictitious citations `[NSW-PN23 para 7]`.
2. **A citation must be opened before it is used.** Open the case on an official court site, AustLII, or Jade, and the legislation on the official register for its jurisdiction. Training memory is a lead, not a source.
3. **If you cannot verify, say so.** List `[VERIFY: what and where]` in the notes and leave the point out of the document. A real case that does not support the point is not support: label it "located, proposition not supported". Never upgrade "probably" to a citation. When asked for a case you cannot find, say that none was verified and offer what could be checked instead (the statute, a search to run, a question for a lawyer).
4. **Law has a date.** State the "as at" date. For legislation, record the version or compilation that covers that date and flag uncommenced amendments. For example, APP 1.7–1.9 on automated decisions start on 10 December 2026 `[POLA-2024 s 2 item 7]`.
5. **Quote exactly.** Keep the source's words, spelling, and punctuation. Mark omissions with an ellipsis and changes with square brackets `[AGLC4 r 1.5.3–1.5.4]`.
6. **Separate formatting from verification.** A perfectly formatted AGLC4 citation can still be wrong or fake. Report both checks separately.
7. **Treatment matters.** A case can be overruled or distinguished. If you have not checked later treatment, say so before relying on a case for a contested point.

## Plain English

Plain legal English is precise English. Keep terms of art, defined terms, and conditions; cut everything else `[OPC-PEM] [STYLE-MANUAL]`.

- Use "must" for obligations, "must not" for prohibitions, and "may" for discretions. Do not use "shall" `[OPC-PEM para 83]`.
- Prefer the active voice and positive statements `[OPC-PEM para 52]`. One idea per sentence: cut unnecessary words and move long conditions and exceptions out of the main sentence `[OPC-PEM para 57]`.
- Prefer ordinary words: "under" not "pursuant to", "before" not "prior to", "if" not "in the event that", "is taken to be" not "shall be deemed to be" `[OPC-PEM app 3] [STYLE-MANUAL]`.
- Use "and/or" only where it is unambiguous, and not at the end of a paragraph or sub-paragraph `[OPC-PEM para 69]`.
- Define a term once, only if it saves words, and then use it consistently.
- Use numbered paragraphs for anything that may be quoted back, and headings that tell the reader what is in the section.
- When simplifying, list any condition, time limit, burden, or party that the plain version dropped. Simplifying must not change the legal effect.

## Citation essentials

Full rules and verified examples: [references/aglc4.md](references/aglc4.md).

- Case: *Mabo v Queensland [No 2]* (1992) 175 CLR 1. Use the authorised report when one exists, and give no parallel citations `[AGLC4 r 2.2.2, 2.2.7]`.
- Unreported case: use a medium neutral citation only if the court itself allocated it, e.g. *Case Name* [Year] Court Number, [para] `[AGLC4 r 2.3.1]`; otherwise use r 2.3.2. Database identifiers such as "[1992] HCA 23" are search aids, not court-allocated citations (the High Court began allocating numbers in 1998).
- Statute: *Acts Interpretation Act 1901* (Cth) s 15AA. Italicise the title and year; do not italicise the jurisdiction or pinpoint `[AGLC4 r 3.1]`.
- Pinpoints go straight after the citation, with no "p" or "para" for cases ("at" only for a later pinpoint in the same footnote). Use a comma before a page pinpoint in a reported case `[AGLC4 r 1.1.6, 1.4.6, 2.2.5]`.
- Subsequent references: `Ibid` only for the sole source in the immediately preceding footnote. Otherwise use a short title or surname with `(n X)` `[AGLC4 r 1.4.1, 1.4.3]`.
- Court documents follow the forum's practice note. Do not convert them to AGLC4 just to be tidy.

## Document quick guides

Detail and source tags: [references/documents.md](references/documents.md).

- **Letter of demand.** Who is owed what, why (contract, invoice, dates), the amount and how it is calculated, a deadline, how to pay or respond, and the next step the client is actually entitled and instructed to take. In SA, check which pre-action route applies before drafting; for a minor civil action, an ordinary notice of intention must be served at least 21 days before starting `[UCR r 332.2]`. Do not threaten action that is not intended or possible, and do not misstate consequences `[RG96 s 19]`.
- **Advice or memo.** The answer first, then the question, short facts and assumptions, the law with pinpoints, the application, risks and options, and next steps. Show your confidence honestly, and list what still needs to be verified.
- **Submissions.** Outcome sought and issues first; then, for each issue, the rule, the authority with a pinpoint, and its application to the evidence. Concede weak points rather than overstating. If the court has AI rules, follow them: in the NSW Supreme Court, Gen AI-assisted submissions, summaries, and skeletons of argument must verify their citations and evidence references in the body; leave a placeholder for the author to complete after their own check `[NSW-PN23 paras 16–17]`.
- **Affidavit.** The deponent's own first-person facts in numbered paragraphs, with no argument. Hearsay only where permitted, and then in the form the rules require `[UCR r 31.7(12)]`. Use the court's form and oath or affirmation wording. Check the court's generative AI rules before helping: NSW Supreme Court bars Gen AI from generating or rephrasing affidavit content `[NSW-PN23 paras 10–13]`, and SA courts have guidelines applying from 1 January 2026 `[SA-GENAI]`.
- **Contract clause.** One obligation per clause: who, "must" or "may", and what; add timing or consequences only where the parties agreed them. Define money (currency, GST), time (business or calendar days, which state's holidays), and notices. Check unfair contract terms risk in standard form contracts `[ACL s 23]`, and never purport to exclude consumer guarantees `[ACL s 64]`.
- **Website or app legal text.** A collection notice tells people the APP 5.2 matters that are reasonable in the circumstances, at or before collection (later only if that is impracticable; see the reference file) `[PRIV sch 1 cl 5] [OAIC-APP5]`. A privacy policy follows APP 1 `[OAIC-APP1]`. Commercial emails with an Australian link generally need consent, sender identification, and an unsubscribe facility `[SPAM ss 16–18]`. Keep "draft, not legally reviewed" visible until a lawyer signs off.

## Output contract

Return, in this order:

1. **The document**, ready to edit, with `[CONFIRM: …]` for missing facts. Do not state unverified law in it; put questions about unverified law in the reviewer notes.
2. **Authorities used**: each citation, where it was checked (URL), the version or date, what was checked (citation details, the relied-on passage, or both), and its status label from [references/verification.md](references/verification.md). Keep unresolved law in these notes, not in text that could be sent.
3. **Assumptions and open points**: jurisdiction chosen and why, facts assumed, and anything a lawyer should decide.
4. **One line of boundary**: "Drafting assistance, not legal advice; check current law and forms before sending or filing." Do not pad it into a disclaimer block.

For a pure citation task, return the corrected citations first, then a short note of changes and any unresolved fields.

## Final checks

- Every case, Act, and section was opened at a real source, or is left out of the document and listed as `[VERIFY]` in the notes.
- No fact, amount, date, or party was added that the user did not supply.
- Jurisdiction stated; every statute carries its jurisdiction; the version date is recorded.
- AGLC4 or forum style applied consistently; `Ibid` and `(n X)` re-checked after edits.
- "Must", "must not", and "may" are used correctly; no "shall" or empty legalese.
- Any threat, deadline, or consequence is one the client can lawfully carry out.
- Prescribed forms, oaths, and statutory wording are copied exactly, not paraphrased.

## References

- [references/aglc4.md](references/aglc4.md): AGLC4 rules for cases, legislation, journal articles, pinpoints, and subsequent references, with checked examples.
- [references/verification.md](references/verification.md): official registers by jurisdiction, case sources, point-in-time checks, and status labels.
- [references/documents.md](references/documents.md): longer guides for each document type.
- [references/sources.md](references/sources.md): every source with URL and check status, plus the upstream skills this one draws on and their licences.
