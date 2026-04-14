# Voxel AI Customer Call Records Analysis: Non-safety Opportunities and Data Extraction Reliability

#### Yifei Hang

## Data Overview
The dataset contains 99 customer call records, each stored in a json file with use cases labels, descriptions, and supporting evidence, bucketed into safety or nonsafety use cases. With 7 of the files containing no use case in either bucket, the remaining files include 702 extracted use cases, with 471 safety cases (67.1%) and 231 nonsafety cases (32.9%). It also contains 2,227 evidence snippets, with 1,999 unique quotes.

## Main Quality Issues in the Current Extraction
While the dataset is large enough to show directional patterns, the raw labels are noisy, making the current extraction output not reliable enough for face-value counting. The main quality issues include:

1. **Almost every extracted use case is unique** 
There are 659 unique use cases (93.9% of 702 total use cases). Simple normalization only reduced unique use case labels by 1. A tf-idf-based similarity scoring also detects 293 similar pairs and 35 candidate subgroups with 2 or more case labels. This means that the current extraction splits the same idea across many slightly different phrases, making direct counting meaningless.

2. **Safety and nonsafety are not cleanly separated** 
There are 28 normalized labels that appeared in both the safety and nonsafety buckets, and all of them happen within the same call. 23 of them also reuse the same evidence across both buckets, while the remaining 5 also have partial evidence overlap. Thus the extraction pipeline is not stable in classifying safety and nonsafety.

3. **A meaningful share of nonsafety output lacks customer signal** 
Among the 231 nonsafety use cases, 74 cases (32.0%) are supported only by Voxel speakers, 124 cases (53.7%) contain at least one customer-signal evidence, and 33 cases (14.3%) are ambiguous, with speaker identities not clearly stated. That is, at least 32% of the nonsafety use cases does not come from customer needs, but rather internal onboarding, product explanation, or workflow discussion on the Voxel side. The current nonsafety counts may therefore overstate adjacent opportunity signals.


## Top 3 nonsafety or adjacent opportunities
Using the filtered nonsafety results and grouping similar labels into broader concepts, three groups stand out:

1. **Dashboard / heatmap / reporting workflow**
This is the strongest adjacent opportunity, with 28 occurrences across 22 calls. Supporting examples include API and BI integration for leading and lagging metrics, automated reporting and notifications, near-miss reporting, and heat maps for trend monitoring. This suggests that beyond detection itself, customers want better ways to see patterns, track risk, and share results.

2. **Action tracking / accountability**
This category includes 18 filtered nonsafety cases across 15 calls. Sample evidence includes action management workflows, ownership and follow-up tracking, and corrective action tracking after incidents. This is a clear workflow extension that supports customers' needs of closing the loop after a detection.

3. **Training / coaching / adoption support**
This theme appears in 7 filtered nonsafety cases across 7 calls. Supporting examples include coaching tied to incident clips, training workflows for remediation, and coaching actions linked to event reduction. This is a strong sign that customers want help turning incident outputs into behavior change.

It is worth noting that `Deployment / infrastructure / camera rollout` scored well and appeared in 12 filtered nonsafety cases across 8 calls, but it could be seen as a secondary theme because it reads more like rollout friction than a distinct adjacent opportunity. `Security / theft / tampering / loss prevention` is also worth watching. It appears in 7 filtered nonsafety cases across 6 calls and could be a good expansion area, but it shows up less often than the top three.

Thus, the strongest adjacent signals are not new safety use cases, but rather a set of workflow needs around reporting, action management, and coaching.

## One practical way to improve the workflow

A practical next step is to add a targeted review step for higher-risk nonsafety rows before using them downstream. Examples include rows supported only by Voxel speakers, rows that appear in both safety and nonsafety, and rows that reuse the same evidence across buckets. These are the exact patterns that make the current nonsafety output less reliable. This keeps most of the pipeline unchanged and limits review to a small flagged subset, so it improves trust without adding much overhead.