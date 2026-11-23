# Bill of Sale Requirements by US State (2026)

A free, source-linked dataset covering when a bill of sale is needed for a private-party vehicle title transfer in all 50 US states and the District of Columbia. It also covers notarisation, each state's official bill of sale form and odometer disclosure rules.

Published by **Robot Lawyer** ([robotlawyer.co](https://robotlawyer.co)). Need a bill of sale for your own sale? Create one at **[Robot Lawyer bill of sale](https://robotlawyer.co/documents/bill-of-sale)**.

- **File:** `bill_of_sale_requirements_by_us_state.csv` (UTF-8, comma-separated, one row per jurisdiction, 51 rows)
- **Last checked:** 23 November 2026
- **Licence:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

## What it answers

- Does this state require a bill of sale to title a vehicle bought from a private seller?
- Must the bill of sale or the title signature be notarised?
- Does the state publish its own bill of sale form? If so, what is its number and where is the official PDF?
- What are the odometer disclosure rules?

## Columns

| Column | Description |
|---|---|
| `state` | State name (includes District of Columbia) |
| `state_code` | Two-letter USPS code |
| `bill_of_sale_required_for_vehicle_title_transfer` | `yes` / `no` / `conditional` / `unverified`. This means required for a standard private-party sale of a titled passenger vehicle. `conditional` means required only in stated situations, for example when the price is not on the title, the vehicle is title-exempt or the title assignment is incomplete. |
| `notarization_required` | `yes` / `no` / `conditional` / `unverified`. This covers notarisation of the bill of sale or of the seller's or buyer's title signatures in a standard private sale. See `notes` for which document it applies to. |
| `official_state_form_name` | Name of the state-issued bill of sale form, or "None identified" |
| `official_form_number` | State form number, or `none` |
| `official_form_url` | Direct link to the official form on a government site, or `n/a` |
| `form_url_check` | Result of our link check on `official_form_url` |
| `odometer_disclosure_rule` | Federal rule summary plus any state-specific wording found in the sources |
| `notes` | Plain-English summary of the official guidance, including recent changes |
| `source_url` | Primary official source (state DMV/revenue agency or, where titling is county-run, the county) |
| `source_url_check` | Result of our link check on `source_url` |
| `additional_source_urls` | Further official sources, separated by ` | ` |
| `unverified_fields` | Fields we could not confirm from an official source (blank = none) |
| `notarization_basis` | How the `notarization_required` value was reached: an explicit official statement, official forms or form instructions, official guidance that names notarisation only for other documents, or `unverified` (with the reason) |
| `verification_status` | `fully verified` (every field confirmed from an official source), `partly verified` (some fields remain `unverified`), or, for Illinois only, `verified via search index only` (the official site could not be reached from our server, so its text was confirmed through a search index) |
| `last_checked` | Date the row was checked (ISO 8601) |

## Methodology

1. For each jurisdiction we located the state agency responsible for vehicle titles (DMV, MVD, BMV, revenue department or Secretary of State). Where titling is done by counties (Hawaii, Wyoming, Tennessee), we used county government pages; Colorado's rule for older titles also cites a county page.
2. We read the official guidance pages, manuals and form PDFs on government sites and recorded only what those sources state. Third-party summaries were not used as sources.
3. Every `source_url` and `official_form_url` was requested on 23 November 2026, and the result is recorded in the `*_check` columns. Some government sites block automated requests (HTTP 403) or time out. In those cases the page content was confirmed through a web reader or a search index, and the check column says which.
4. Where a fact could not be confirmed from an official source, the field is marked `unverified` and listed in `unverified_fields` instead of being guessed. The most common gap is notarisation: many states simply do not say either way.
5. Notarisation is recorded as `no` only when one of these applies: (a) the state says so explicitly; (b) the state's official form instructions, official guidance or administrative code set out what the title assignment or bill of sale must contain and how it is signed, and notarisation is not among the requirements (for example Texas Form 130-U, or South Dakota rule 64:28:09:02); or (c) the state's official guidance or administrative code names notarisation only for other documents (for example lien releases, powers of attorney or affidavits for untitled vehicles), which shows it is not required for the standard transfer. A form without a notary block, or a document checklist that is silent, is not enough on its own: those states stay `unverified`. The basis is recorded in `notarization_basis`.
6. Where official sources conflict, the value stays `unverified` and the conflict is described in `notes` (Alaska, Mississippi and Nevada; see Limitations).
7. The federal odometer rule was taken from 49 CFR 580.17 (eCFR).

### Federal odometer rule (applies in every state)

Under 49 CFR 580.17, a seller must disclose the mileage when ownership is transferred, with these exemptions:

- vehicles of model year 2010 or older;
- vehicles of model year 2011 or newer once they are 20 years old (for example, model year 2011 vehicles become exempt in 2031);
- vehicles with a gross vehicle weight rating over 16,000 lb;
- vehicles that are not self-propelled.

Some states publish their own wording (for example "less than 10 years old"). Where they do, it is quoted in the row, but the federal rule still applies.

## Sources

All sources are official government websites (.gov or the state's official agency domain). County clerk pages are used where counties run titling. Oregon's statute (ORS 803.094) is linked on the Oregon Legislature site, which blocks automated requests; its text was confirmed via an unofficial copy. Louisiana's Office of Motor Vehicles runs its official site at expresslane.org, and its forms are hosted on the Louisiana DPS document system. The federal source is [eCFR 49 CFR 580.17](https://www.ecfr.gov/current/title-49/subtitle-B/chapter-V/part-580/section-580.17). The per-state URLs are in the CSV.

Two cross-state official references are quoted in `notes` as corroboration only, never as the sole basis for a value:

- the New York DMV page [Acceptable Proofs of Ownership for Vehicles](https://dmv.ny.gov/titles/acceptable-proofs-of-ownership-for-vehicles), which lists the states whose titles need a notarised transfer section (Alaska, Arizona, Hawaii, Kentucky, Louisiana, Mississippi, Montana, Nevada, North Carolina, Ohio, Oklahoma, Pennsylvania, Washington, Wyoming and Puerto Rico);
- the notary chart in the Nebraska DMV County Treasurer's Manual (dated December 2011, so possibly out of date).

## Limitations

- These rules cover standard private-party sales of titled passenger vehicles. Dealer sales, gifts, inheritance, salvage, boats, trailers and title-exempt vehicles often follow different rules, which appear in `notes` only where relevant.
- State rules change. Two recent changes are captured: Maryland repealed its notarised bill of sale rule for vehicles under 7 years old (1 October 2026), and Montana titles no longer need notarisation (October 2025). Always check the linked source before relying on a row.
- County practice can differ from state guidance.
- Conflicting official sources: the New York DMV lists Alaska, Mississippi and Nevada titles as needing notarised transfers, but those states' own guidance names no such step. These rows stay `unverified`. Hawaii is recorded as `conditional` from Honolulu's guidance (notarising the seller's signature is optional), although New York also lists Hawaii.
- Illinois: the Secretary of State site (ilsos.gov) could not be reached from our server on 23 November 2026. Its FAQ and brochure text was confirmed through a search index, and the statute (625 ILCS 5/3-112) through a web reader.
- Minnesota: the older DVS title booklet could not be reached. The row uses the current DVS guide "Buying or Selling a Motor Vehicle" (March 2025) and Minn. Stat. 168A.10.
- Still `unverified` for notarisation (6): Alaska, Mississippi and Nevada (conflict above); District of Columbia and Maine (official sources silent, no signing instructions); Nebraska (title signing has no notary step, but the DMV bill of sale form, which the seller must give, has a notary or county official block, and we could not confirm whether it must be completed).
- Colorado is recorded as `conditional`: current titles need no notary, but older Colorado titles with a notary space must be notarised or accompanied by form DR 2445.
- Coverage as of 23 November 2026: 45 of 51 jurisdictions have a confirmed notarisation answer (31 `no`, 8 `yes`, 6 `conditional`) and 6 remain `unverified`. 44 rows are fully verified, 6 partly verified and 1 (Illinois) is verified via search index only.

## Licence and attribution

This dataset is released under **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)** (full text in `LICENSE`). You may share and adapt it, including commercially, provided you give attribution:

> Source: Robot Lawyer ([robotlawyer.co](https://robotlawyer.co)). "Bill of Sale Requirements by US State" (2026), CC BY 4.0.

## Disclaimer

This dataset is general information, not legal advice. It summarises official guidance as it stood on the date checked and may be incomplete or out of date. For advice on a specific transaction, check with the relevant state agency or a lawyer licensed in that state.

## Citation

```
Robot Lawyer (2026). Bill of Sale Requirements by US State [Data set]. https://robotlawyer.co
```
