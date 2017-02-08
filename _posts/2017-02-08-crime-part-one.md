---
id: 1
title: Crime (Part One)
date: 2017-02-08
author: Michael Weis
layout: post
guid: http://www.quantifylouisville.com/?p=1
permalink: /crime-part-one/
categories:
  - Uncategorized
tags:
  - Government
  - LouieStat
  - Crime
---

<h1>
<big><b> ANALYZING LOUISVILLE Crime Data Part I</b></big>
</h1>
<h4>
<b> The Data </b>
</h4>
For our initial exploration of this data set, we tackled crimes reports from the last five years [2012 - 2016](https://data.louisvilleky.gov/dataset/crime-data).

<h4>
<b> Things To Do Today </b>
</h4>
-   Get the data in...
-   Do things to it...
-   Look at it...
-   Say things about it...
-   ~~Commit a few crimes and track how long it takes to impact the data~~

<h4>
<b> Hilarious Outliers </b>
</h4>
One of the first steps to reviewing a new data set is to try to tease out outliers. Doing so can highlight weaknesses in how the data was captured. For example, one easy way that tends to yield silly results is to create comparisons between dates in the set and intepret the outliers literally. In this particular data set, both the date a crime occured and the time it was reported are captured.

Some crimes appear to be reported days, weeks, and sometimes even *years* after they occurred. The visual below tallies any crime from ten years that was reported at least one year after it allegedly perpetrated. ![](crimez_files/figure-markdown_github/Older%20than%20a%20year%20graph-1.png)

Understandably, sexual assults and identity thefts make up a large portion of the crimes with a long lag between their occurence and report. However, someone also waited over 12 years to report a stolen firearm and a burglary on 24th Street wasn't reported for over a decade ("Should I call the cops? Does that *really* qualify as a burglary? Maybe I should sleep on it for one more night and see how I feel in the morning.").

Perhaps the most baffling the records include the 32 times in the last ten years in which someone waiting over a year to report that someone was Disturbing The Peace. While the majority of those appear to be prostitution related, one record seems to indicate that someone waited SEVEN YEARS to report that someone got a little crazy in a 7th street bar.

At the other extreme, some crimes appear to have been reported before they even occurred. These Minority-Report crimes, in theory, should be fairly easy to prevent.

![](crimez_files/figure-markdown_github/Minority%20Report%20Graph-1.png)
