# Human Perception of Gerrymandering Dataset

This directory contains a public, de-identified data used in the analysis of human perception of Gerrymandering. The goal of this project is to simulate district maps and the election outcomes based them to collect human responses for which maps are more "fair". 

## Files

- `responses.csv`: one row per submitted survey response.
- `comparisons.csv`: one row per map-pair judgment. Each response contributes five rows.
- `comparison_summary.csv`: aggregate counts for each ordered map-pair comparison, split by spam flag.
- `map_layouts.csv`: derived metadata for the 25 map layouts.
- `map_layouts.jsonl`: full 8x8 grids and derived metadata for the 25 map layouts.
  - the map is expressed as a `list[list[dict[Literal["party", "district], int]]]` where the each dictionary contains the `party` (who that block votes for) and `district` (which district that block belongs to).

## De-identification

Original `userid` values are replaced with sequential `participant_id` values. Original survey response keys, MTurk Worker IDs, HIT IDs, assignment IDs, payment records, approval statuses, and receipt documents are not included in this export. Free response strings and MTurk worker IDs in free-text fields are redacted.

## Map Layouts

Each map layout is an 8x8 grid. Every cell has:

- `party`: integer party/color category from the original map.
- `district`: integer district assignment.

Each base map has five district layouts: `map_0` through `map_4`, each with `layout_0` through `layout_4`.
For a comparison row, `map_a_layout_id` and `map_b_layout_id` identify the two layouts shown to the respondent.

## Reason Codes

The survey stored checkbox-style reason codes as integers. The codes can be mapped as follows:

- `0`: The shape of the districts
- `1`: The winner of election
- `2`: The distribution inside districts
- `3`: None of the above

## Quality Flag

`is_spam` is carried over from `combined.csv`. It should be used as a filtering flag rather than a deletion record. This flag was manually assigned based on the free-response text at the end of the survey.

## Citation

Please cite the original paper if you use this dataset:

```bib
@article{kellyCrowdsourcingPerceptionsGerrymandering2022,
  title = {Crowdsourcing {{Perceptions}} of {{Gerrymandering}}},
  author = {Kelly, Benjamin and Kang, Inwon and Xia, Lirong},
  year = 2022,
  journal = {Proceedings of the AAAI Conference on Human Computation and Crowdsourcing},
  volume = {10},
  number = {1},
  pages = {124--132},
  issn = {2769-1349, 2769-1330},
  doi = {10.1609/hcomp.v10i1.21993}
}
```
