# Exports

Choose a day in the Journal window, then **Export** in the toolbar. A save panel asks where to write the file.

| Export | Range | File |
|---|---|---|
| Markdown (standup) | this day, or the last 7 days ending on it | `work-journal-YYYY-MM-DD.md` |
| Timesheet CSV | this day, or the last 7 days | `timesheet-YYYY-MM-DD.csv` |
| Files CSV | last 7 days | `files-YYYY-MM-DD.csv` |

## Markdown

One section per day: the summary, a **Time by app** table, **Files touched** (up to 10 names per folder, then a count) and a **Timeline** of sessions of a minute or more. If you used Summarize on-device for a day in this session, that text is used; otherwise the template summary.

## Timesheet CSV

One row per app session. Columns and an example row (invented sample data):

```
date,start,end,minutes,app,bundle_id
2026-11-20,09:14,10:41,87.0,Xcode,com.apple.dt.Xcode
```

## Files CSV

One row per distinct file touched per day (invented sample data):

```
date,folder,file,path
2026-11-20,app-prototype,Package.swift,/Users/sample/Projects/app-prototype/Package.swift
```

## Spreadsheet safety

CSV follows RFC 4180 quoting. A text field that starts with `=`, `+`, `-`, `@`, a tab or a carriage return gets a leading apostrophe so a spreadsheet will not run it as a formula.
