---
layout: post
title:  "Inspect the uninspected"
subhead: "A look at how NYC restaurants make the grade"
date:   2016-05-09 14:39:40 -0700
categories: government restaurant nyc
---

![grade card on window]({{ site.baseurl }}/images/NYC_restaurants/window_grade.jpg)

When it comes to New York City restaurant inspection, "A" really is for average. Based on my analysis of the [official dataset][], 9 out of 10 restaurants earned the top grade in 2015, a level of distinction (or lack thereof) rarely seen this side of Yale's English Department.

  [official dataset]: http://www.opendatanetwork.com/dataset/data.cityofnewyork.us/9w7m-hzhe

{% include NYC_restaurants/Grade_distribution.html %}

Luckily for my inaugural project, the dataset contains raw scores (lower is better). The distribution of these scores reveals a far more interesting picture below. (Hover over each bar for details.)

{% include NYC_restaurants/Initial_inspection_score_distribution.html %}

Most saliently, the A share, while large, is not as overwhelming as in the previous plot. As it turns out, although the grades have fixed score ranges, the *initial inspection* scores don't always translate into grades. Restaurants that earn scores in the A range do get A's, but those that don't will get another shot at it in the *re-inspection* about a month later (until which time their grade will be "Pending"). If you think the system is rigged in favor of A's, you're probably just cynical.

## Forgiving on the edge

But you may not be cynical enough. The plot shows a curious crevasse at the score range just shy of A (from 14 to 16). Could it be that inspectors bump some of those scores down into the A range? Sure, it could! I, for one, would be tempted. Restaurants are happy, diners are happily misled, and inspectors don't have to come back in a month. What's not to like?

This hypothesis is supported by the lack of a similar break at the B-C threshold. Thanks to the mandatory re-inspection, which alone will determine the eventual grade, any score below the A range is as good as another in the initial inspection. The threshold therefore doesn't exist for practical purposes. (Technically, it may play a role in determining whether the next inspection cycle is 4 months or 6 months later, but who's thinking that far?) With no extrinsic incentive to effect it, the distribution follows a smooth downward curve, as one would expect. If anything, the count at 28 is actually slightly higher than at 27.

## Second time lucky

This line of reasoning suggests that the *re-inspection* score distribution should show a break the B-C threshold as well as at the A-B one. That is indeed the case.

{% include NYC_restaurants/Re-inspection_score_distribution.html %}

The discontinuities are starker here in fact. The inspectors are even nicer, apparently, when they're giving grades that restaurants will be stuck with for months until the next inspection cycle. Interestingly, while the A-B break here shows a crevasse profile observed in the initial inspection plot, the B-C break looks like a flat-out cliff. Inspectors *really* hate to give out C's, it seems, and that tends to suppress C scores across the board.

## 50 ways to peeve your inspector

But how do inspectors really go about doling out their gentleman's A's (and less often B's)? Because grading is mechanical and transparent, inspectors needs to give a better score in order to give a better grade, as we have seen. (By contrast, professors often bump a student up a grade without bothering with the score.) Scoring, too, is largely mechanical and transparent, with a rigid rubric specifying a range of scores for each violation found. To give a lower score, the inspector must turn a blind eye to a violation (or two).

What kinds of violations tend to get ignored? That depends, first and foremost, on what kinds of violations are there to begin with. Then the seriousness of the violation likely becomes a factor. Of the [68 scored violations][], 50 are deemed "critical" and 18, "general." The critical violations, especially the 21 considered to be "public-health hazards" (PHH), are probably more difficult to overlook than the general ones. All three types are represented among the most common violations found in 2015 (hover for description).

[68 scored violations]: http://www.nyc.gov/html/doh/downloads/pdf/rii/self-inspection-worksheet.pdf "official worksheet"

{% include NYC_restaurants/violations.html %}

The stickling 10F violation affects more than 60% of NYT restaurants, and that's just the reported figure, mind you. In any kitchen, one can always find *something* that isn't "improperly maintained and/or not properly sealed, raised, spaced or movable to allow accessibility for cleaning on all sides, above and underneath the unit." Like most general violations, 10F has a score range of 2 to 5 (each instance of violation brings the score up a level). If you, as inspector, found a 10F instance that puts the total score at 14, wouldn't you be inclined to ignore it so that the restaurant can get an A at 12? This would explain not only the trough at 14, but also the spike at 12.

## 10F schmen-F

If a 10F really does tend to get a pass in order to help a restaurant over the edge, then the percentage of restaurants found with the violation should be relatively low just north of the A-B threshold. (The B-C threshold is different because it doesn't exist in the initial expectation and has a different profile in the re-inspection.) This is indeed what I've found.

{% include NYC_restaurants/10F_prevalence.html %}

The dip and subsequent recovery are unmistakable in each graph. On top of that, the re-inspection graph's consistent undershooting is consistent with the extra leniency observed. Case closed!

Not impressed? Okay, I'd hoped for more striking evidence, too, but there are too many factors at play. If we don't know the plot should look like in its absence, then we cannot confidently identify the effect of inspectors' intervention. To begin with, we cannot expect the same level of prevalence across all scores, i.e. a flat line. Even in the simplest case, where all violations occur at random and carry the same score of 1, the graph would be upward-sloping at every score for every violation. The higher the score, the more "slots" available as it were, and the more likely a violation is to be found. With this in mind, our graphs' uninspiring flattish contour is in fact evidence of human intervention.

Disparate scoring further complicates this picture. The total scores of 2 and 3, for example, can only be made up of one general violation since no critical violation carries a minimum score below 5. With much competition eliminated, the 10F, already most prevalent overall, is even more prevalent there. The total score of 5, on the other hand, can be either one (non-PHH) critical violation or two general violations worth 2 and 3 points, and the former's exclusionary effect makes the 10F relatively uncommon. This score combination effect is also easy to explain at the total score of 4, but becomes too complex at higher scores, where its existence is confirmed only by the broad agreement of the initial-inspection and re-inspection graphs. The trouble is, when the graphs are naturally supposed to zigzag, it becomes impossible to definitely discern the effects of inspectors' leniency.

The best I can do, probably, is to contrast the 10F's plot with those of other violations that do *not* appear to be overlooked at the margins. Here are the next two most common violations, 08A and 02G. See for yourself what these plots have in common with each other and in contrast with the 10F one. (NB: The graphs are probably less meaningful at very high scores due to small sample sizes.)

{% include NYC_restaurants/08A_prevalence.html %}

{% include NYC_restaurants/02G_prevalence.html %}

## Conclusion

I have established to my satisfaction that inspectors bias their scoring in favor of A's and against C's. Exactly how they do it is inconclusive and likely differs from case to case, although it does appear that the 10F violation is more likely to be overlooked than, say, the 02G.

Finally, lest you think that inspectors are too lax, this [_New York Times_ article][NYT] provides a different perspective. Forget technical infractions like the 10F, strict enforcement against even "public health hazards" can lead to ridiculous results. Perhaps a little leniency is fitting. This write-up is not meant to make a policy recommendation, especially if said policy is serving camembert straight out of the fridge. _Bon appétit._

[NYT]: http://www.nytimes.com/2012/02/29/dining/new-york-city-restaurants-skirt-inspections-finer-points.html
