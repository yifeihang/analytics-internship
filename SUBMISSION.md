## Implementation approach

I first read a few JSON files by hand to understand the call structure, the extraction output, and the business question. I then loaded all files and flattened them into two tables: one for use cases and one for supporting evidence.

My first pass focused on cleaning the label space. I tried simple text normalization, but it had very little effect because the labels were still highly fragmented. I then looked at repeated labels, cross-bucket overlap, reused evidence, and similar-label pairs using fuzzy matching and TF-IDF similarity. This helped me confirm that many labels were slight variations of the same underlying idea.

To turn the fragmented labels into something more usable, I grouped them into broader concepts with a keyword-based semantic mapping approach. I chose this because it is easy to inspect and explain. I used label keywords as the main signal and descriptions as a secondary signal when assigning each label to a concept group.

For the final recommendations, I combined a simple opportunity score with manual review. I ranked concept groups using call breadth, case volume, and signal purity after filtering. I then manually checked the highest-ranked themes to separate true adjacent opportunities from secondary themes such as deployment friction.