---
name: sheets-formulas
description: Use when a staff member asks for a Google Sheets or Excel formula, asks why a formula isn't working, wants to count, sum, average, look up, filter, sort, split, combine or clean data in a spreadsheet, or needs conditional formatting, data validation or a dropdown.
---

# Sheets formulas

Help EVSC staff write and fix spreadsheet formulas. Default to Google Sheets,
since EVSC uses Google Workspace; give the Excel version too if the staff
member says they use Excel or the formula differs.

## Work from the layout, not the data

You need to know how the sheet is laid out, not what's in it.

- Ask for the column letters and headers, the row where data starts, the sheet
  (tab) names, and what the result should look like.
- If you need examples to get it right, ask for two or three made-up rows. Don't
  ask for a real export.
- If the staff member pastes real data with student or staff names, IDs, grades,
  attendance or other records, don't repeat it back. Work out the formula from
  the column layout, and suggest using made-up rows or de-identify next time.

## Writing the formula

- Give the formula in a code block, ready to paste, and say exactly which cell
  to put it in.
- Prefer formulas that fill a whole column from one cell when the sheet will
  grow (ARRAYFORMULA, FILTER, QUERY, or BYROW in Sheets), and say so. Use a
  simple formula copied down when that's easier for the staff member to
  maintain.
- Use XLOOKUP or INDEX/MATCH rather than VLOOKUP when a lookup column might move.
- Handle blanks and errors: wrap in IFERROR or IF(A2="", "", …) when empty rows
  would otherwise show errors, but don't hide errors that signal a real problem.
- Use straight quotes and commas. Note if the staff member's locale uses
  semicolons as separators.
- Reference other tabs as 'Tab name'!A2:A. For other files, IMPORTRANGE needs
  one-time access approval in the sheet.

## Explaining it

After the formula, a short plain-language explanation: what each part does, in
order. Then one or two quick checks the staff member can do to confirm it works
(for example, "the total in F2 should match the count at the bottom of column
A").

## Fixing a broken formula

Ask for the exact formula and the error or wrong result. Common causes to check:
text that looks like a number, extra spaces (TRIM), mismatched range sizes,
absolute vs. relative references ($A$2 vs A2), wrong separator, and a range that
stops before the data ends.

## Beyond formulas

- Conditional formatting and dropdowns: give the menu steps (Format → Conditional
  formatting; Data → Data validation) and the custom formula if one is needed.
- If the task needs Apps Script instead of a formula, say so. The google-apps-script
  and plan-first skills help with scripts.
- You can't open or edit the staff member's spreadsheet directly; they paste the
  formula in themselves.
