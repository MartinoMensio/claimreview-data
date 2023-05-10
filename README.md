# claimreview-data

[![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg

This repository contains the dataset of a paper that we submitted to the [ISWC 2023 Resource Track](https://iswc2023.semanticweb.org/call-for-resources-track-papers/).
The data is automatically updated every day with ClaimReview.

You can download the [latest version from the release section](https://github.com/MartinoMensio/claimreview-data/releases/latest), or browse [all the versions](https://github.com/MartinoMensio/claimreview-data/releases/).


## Collection

The data collection is performed in 6 steps:

1. Collection of ClaimReviews URLs Candidates: using DataCommons and Google Fact-Check API, we get all the URLs where ClaimReviews are published
2. Collection of ClaimReviews from fact-checkers: we recollect from the websites of fact-checkers the ClaimReviews
3. Validation and Cleaning: we fix and clean the metadata
4. Ratings Mapping: we normalise the labels to credible, mostly credible, uncertain, mostly non-credible, non-credible and unknown 
5. Occurrences Extraction and Unshortening: we extract the URLs where the claims occur and we resolve the links that use shortening services (e.g., bit.ly) or archives (e.g., archive.is)
6. Misinformation Database and Snapshot: we build the output files described below

## Output files

Each archive contains the following files:

- `ifcn_sources.json`: details of the fact-checkers present in the dataset, such as website, country and language. The details also include the details of the IFCN compliance: date of issue, expiration, adherence to each of the skills (e.g. transparency of sourcing, transparency of methodology).
- `claim_reviews_raw.json`: this file contains the ClaimReviews collected in the first step from DataCommons and Google Fact-Check Tools. As noted before, this is bigger than the final cleaned dataset (recollection issues) but contains uncleaned data (`appearance` and `firstAppearance` fields).
- `claim_reviews_recollected.json`: the recollected dataset.
- `claim_reviews.json`: the final cleaned dataset with ratings mapping and unshortening.
- `claim_labels_mapping.json`: statistics on how labels have been translated.
- `disagreeing_reviews.json`: cases where the same URL has received multiple disagreeing ratings.
- `not_ifcn_sources.json`: this file contains a list of domains that published ClaimReview but are not in the IFCN list.
- `links_all_full.json`: details of the reviewed URLs. For each URL that has been reviewed, we show the reviews and the normalised ratings. 

This data is currently used by [MisinfoMe](https://misinfo.me/).



## License

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].
