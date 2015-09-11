Clustering
========================================================
author: Matt Pettis
date: 2015-09-14


Background
========================================================
incremental: true

- A client wants to forecast hundreds of time series at once.
- They believe they only have around 10 basic time series index patterns.
- Can we verify this is true?
- How can we find these possible 10 indexes?
- How can we demonstrate we have the right curves?


First, always look at all of the data
========================================================

Here are [all of the indexes](file:///Users/mpettis/Personal/tech-talks/clustering/img/all-indexes.png)

How could one group these indexes in "like" groups?

Approach: K-Means
========================================================
incremental: true

- Why should k-means be applicable?
    - Normally meant for Euclidian closeness, how does that translate to time series?
- Pros
    - Easy to understand.
    - Many tools have the ability to compute in pre-packaged modules.
    

Approach: K-Means
========================================================
incremental: true
- Cons
    - Not easy to visualize in high dimensions.
    - Non-spherical clusters or poor starting conditions can lead to non-optimal cluster convergence.
    - Noise during non-important stretches of time can make two curves alike or different purley on random correlations.



Results
========================================================

- Here is [strips by cluster and colors by region](file:///Users/mpettis/Personal/tech-talks/clustering/img/strip-cluster-color-georegion.png)
    - Clusters often highly homogeneous for a region, with a few stragglers.
    - Region Eur1 seems split across clusters 6 & 7.
    - Overall suggests region might be better than just clustering.
    

Results
========================================================

- Here is [strips by region and colors by cluster](file:///Users/mpettis/Personal/tech-talks/clustering/img/strip-georegion-color-cluster.png)
    - Regions not as highly homogeneous by kmeans cluster.
    - Overall appears to have a looser federation of indexes than for kmeans clusters.
    - Some regions sparsely populated -- may or may not be problem.


Results
========================================================

- Are there quantitative measures of goodness of fit of clusters?  Yes, such as:
    - Time series Pearson correlation function.
        - can be misleading if there are long stretches of noise.
    - Silhouette calculations on clusters.  Plots of these "widths" can help you determine natural or optimal number of clusters, and how well-defined the clusters are.

Alternate: Hierarchical clustering
========================================================

A nice feature to this is that you can tell how strongly clusters diverge or converge as you try to roll clusters together.

[Here](file:///Users/mpettis/Personal/tech-talks/clustering/img/dendogram.png) is a dendogram for hierarchical clustering, more clusters.


Conclusions
========================================================
incremental: true

- Should we use raw clustering, or the region attribute?
    - Straight analysis doesn't tell us.  Depends on other components, like: are the curves close enough by region, and are regions easier to administer?
- Try to find ways to look at your data.
- Understand the limitations of your models.  Where are they good?  What are their edge cases?


Questions?
========================================================

... and thank you!
