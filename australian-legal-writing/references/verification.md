# Verifying Australian law

A citation is usable only after you have opened the source and confirmed it says what the draft claims. This file covers where to look and what to record. The method follows the point-in-time and fail-closed approach of the upstream checkers credited in [sources.md](sources.md).

## Legislation: official registers

| Jurisdiction | Official register | Name for a point-in-time text |
|---|---|---|
| Commonwealth | <https://www.legislation.gov.au> (Federal Register of Legislation) | compilation |
| South Australia | <https://www.legislation.sa.gov.au> | version (listed as Current or Historical, Authorised) |
| New South Wales | <https://legislation.nsw.gov.au> | version |
| Victoria | <https://www.legislation.vic.gov.au> | authorised version |
| Queensland | <https://www.legislation.qld.gov.au> | reprint |
| Western Australia | <https://www.legislation.wa.gov.au> | compilation |
| Tasmania | <https://www.legislation.tas.gov.au> | version |
| ACT | <https://www.legislation.act.gov.au> | republication |
| Northern Territory | <https://legislation.nt.gov.au> | reprint |

Steps:

1. Find exactly one official title. Use the short title and year of original enactment.
2. Choose the version whose date range covers the "as at" date. If the user gives no date, use today's date and say so.
3. Open the provision and confirm its number and words. Section numbers move when Acts are amended.
4. Check for repeal, uncommenced provisions, and amendments not yet incorporated. Treat a future commencement as future law. For example, the current *Privacy Act 1988* (Cth) compilation runs until 10 December 2026, when APP 1.7–1.9 commence `[PRIV] [POLA-2024 s 2 item 7]`.
5. Record: title, provision, register URL, version or compilation identifier and date range, and the date you checked.

An as-made Act, a Bill, a news article, or a law firm summary does not prove the current text.

## Cases

| Source | Use |
|---|---|
| Court websites, e.g. <https://www.hcourt.gov.au>, <https://www.fedcourt.gov.au>, <https://www.caselaw.nsw.gov.au>, <https://www.courts.sa.gov.au> | Official judgments where published. |
| AustLII <https://www.austlii.edu.au> | Free full text of most Australian judgments and legislation. It may block automated requests; then use a browser the user operates, or mark the citation `unverifiable`. Never try to get around a bot check. |
| Jade <https://jade.io> | Free judgment text and some citator information. Some features need an account. |

For each case, record two checks separately: the citation details (party names, year, report or court-allocated medium neutral citation, court, date, judges) and the relied-on passage at the pinpoint. To use a quotation, find it word for word there. Older High Court judgments are often available as official scans, e.g. <https://www.hcourt.gov.au/sites/default/files/eresources/1946/HCA/46.pdf> for *Penfolds Wines* (1946) 74 CLR 204.

Later treatment: check whether the case has been overruled, doubted, or distinguished, using the "cited by" or noteup features on AustLII or Jade. If you cannot check treatment, say so next to the citation.

## Status labels

Give every authority one label, and say what was checked (citation details, the relied-on passage, or both):

- **verified**: opened at an official or recognised source; the citation details match, and the relied-on passage was read and supports the point.
- **citation details verified; pinpoint not sighted** (or **passage: not applicable** for a pure format task): the authority and its details are confirmed, but the pinpoint or passage was not read. Say which.
- **located, proposition not supported**: the authority is real but does not say what the draft needs. Do not cite it for that point.
- **unverifiable**: the source could not be reached (blocked, paywalled, offline). This is not evidence that the authority is fake. Keep `[VERIFY]` in the notes and out of sendable text.
- **not located in [named searches]**: the named databases were searched and nothing matched. This strongly suggests a fabrication or a wrong citation, but it is not proof. Remove it from the draft and tell the user what was searched.

Never merge "unverifiable" and "not located".

## When asked to find authority for a proposition

1. Look for a statute first. It is often the real source of the rule and is easier to verify.
2. Search for cases only through real databases. Report what you searched.
3. If nothing verified supports the proposition, say so plainly. Offer a narrower proposition you can support, the statutory basis, or the search a lawyer should run. Do not supply a "representative" or "illustrative" case name.

## Regulator guidance

Guidance from regulators such as the OAIC, ACCC, ASIC, and the Fair Work Ombudsman helps with interpretation, but it is not law. Cite it as guidance, record its date or version, and check it against the statute.
