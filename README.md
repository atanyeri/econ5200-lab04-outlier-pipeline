# Outlier Detection on California Housing

## Objective
I built and debugged an outlier-detection pipeline, then compared three detection methods to see where they agree and disagree on California housing data.

## Methodology
* Diagnosed three bugs in a broken outlier-detection pipeline: a non-robust center/spread calculation, a wrong fence constant, and an unrealistic contamination setting
* Fixed each bug and confirmed the corrected functions behaved as expected
* Used an `OutlierDetector` class with three methods — modified Z-score, Tukey fences, and Isolation Forest — that checks its own settings when built and returns a summary of what it found
* Ran modified Z-score and Tukey fences on the `MedInc` column, and Isolation Forest across all nine numeric columns
* Compared the three methods' flagged rows directly to see how much they overlap
* Built an interactive explorer with dropdowns and sliders so the column, threshold, k, and contamination values can be adjusted and the flagged counts and rows update live
* Wrote a memo recommending a method for a policy team cleaning this data before using it for funding decisions

## Key Findings
* Modified Z-score flagged 400 rows on `MedInc` (1.9%)
* Tukey fences flagged 681 rows on `MedInc` (3.3%)
* Isolation Forest flagged 1,032 rows across all nine columns (5.0%)
* All three methods agreed on 322 rows
* I recommended using modified Z-score or Tukey fences as the main screening step, since their results are easy to explain and check by hand, with Isolation Forest used separately to flag unusual combinations of values for manual review
* I also noted that a flagged row should not automatically be removed, since some flagged rows may represent the exact areas a housing-funding program is meant to help, not errors in the data
