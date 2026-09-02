# greenwichdining.com

Health inspection records for every licensed food establishment in Greenwich, Connecticut,
published as a searchable public record.

The underlying documents were obtained from the Town of Greenwich Department of Health under
the Connecticut Freedom of Information Act (Conn. Gen. Stat. §§ 1-200 et seq.). Inspections are
recorded on Connecticut DPH form EHS-108 and cover February 2023 onward, the period since
Connecticut adopted the current FDA Food Code.

## What's here

| | |
|---|---|
| `index.html` | The entire site: markup, styles, script and data in one file. No build step at serve time, no runtime dependencies, nothing to break. |
| `og-card.png` | Social preview image. |
| `CNAME` | Custom domain for GitHub Pages. Do not delete — Pages rewrites it on some settings changes. |
| `.nojekyll` | Stops GitHub from running the files through Jekyll. |

## How a record is verified

Every violation read off a scanned form is cross-checked against the count the inspector wrote
in the form's own summary box. The `verification` status on each inspection is one of:

- **reconciled** — the itemised violations match the inspector's own count
- **verified** — same, confirmed by hand after the automatic check flagged it
- **nosummary** — the inspector left the summary box blank, or the scan destroyed it, so there
  is nothing to check against. Violations are shown with a note.
- **mismatch** — the summary and the itemised marks genuinely disagree. Shown with the
  discrepancy stated, and excluded from the ranked lists.
- **unclear** — the summary box could not be read with confidence.

Only reconciled and verified inspections feed the ranked lists, so no establishment is ranked
on an unconfirmed reading.

## Rebuilding

The site is generated from the extraction pipeline's output, one directory up:

```bash
cd ../site
python3 build_data.py     # inspections.csv + violations.csv -> site_data.json
python3 build_site.py     # site_data.json -> greenwich_dining_record.html
./publish.sh              # copy into this repo, commit, push
```

## Corrections

These are reproductions of public records, not an official rating and not a health department
grade. To report an error, open an issue with the establishment name and inspection date. For
the authoritative record, contact the Greenwich Department of Health.
