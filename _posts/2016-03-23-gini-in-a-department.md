---
id: 90
title: Gini In A Department
date: 2016-03-23T14:51:46+00:00
author: Michael Weis
layout: post
guid: http://www.quantifylouisville.com/?p=90
permalink: /gini-in-a-department/
categories:
  - Uncategorized
tags:
  - Government
  - LouieStat
  - Salaries
---
&nbsp;

**<span style="color: #ff6600;">INTRODUCTION</span>**

<span>Have you ever wondered which country has an income distribution most similar to the Louisville Metro Police Department’s salary distribution in 2015? (Us too! It’s Bosnia in 2003.) How about Metro Animal Services? (That would be Canada in 2004.) The Mayor’s Office? (Argentina in 1993.)</span><!--more-->

Ok, first a step back… for our third leap into the free-data portal, we decided to find out whether departmental salaries were more equitably shared than those of entire nations. Happily for our government employees and their salaries, but sad for many, many countries, Louisville Metro Government salaries tend to be much more equally distributed than their national counterparts.

**<span style="color: #ff6600;">WHAT’S THE DATA?</span>**

Not a small goal of our third post was to identify a data set that was fairly easy to interpret without the Louisville Metro equivalent of the Rosetta Stone (our plan is to walk through some of the shortcomings of the current data offerings in a subsequent post). After searching through dozens of data sets, we arrived at the <a href="http://portal.louisvilleky.gov/dataset/salary-data" target="_blank">Louisville Metro salary data</a> that met our criteria. Fairly lengthy time period? Check (2008-2015). Likely interesting story with hopefully limited assumptions on our part? Check (&#8230;check?).

**<span style="color: #ff6600;">WHAT WE DID</span>**

So we had our main goal, to understand how ‘equal’ income is distributed within each department of Louisville Metro. Our second goal, of course, was to find out which salary distribution was most similar to that of the County Attorney’s Office (USA!, USA!, USA!)

To do this, we needed to dive into the typically avoided world of macroeconomics using a number called the Gini Coefficient (pronounced ‘Genie’), which represents how disperse income is distributed within a group of people.  A Gini Coefficient (henceforth called a ‘Gini’) of 0 represents perfect equality (1% of the population holds 1% of income, 2% holds 2%, etc.), while a Gini of 1 represents perfect inequality (1% of the population has all of the money). Put even more plainly, high &#8211; bad, low &#8211; good.

To help visualize this, economists use what is known as a Lorenz curve &#8211; a graph designed to visualize inequality within a group of people. The closer the curve is to the 45 degree “perfect equality” line (a.k.a., a lower Gini), the more equally pay is distributed within the income earners &#8211; the fatter the slope, the less so.

This can be seen pretty clearly among two departments &#8211; Louisville Metro Police and the Louisville Zoo. The Louisville Metro Police has a relatively skinny slope in their Lorenz curve, while the Zoo has a much fatter slope &#8211; indicating more pay inequality at the Louisville Zoo than the Metro Police.

<a href="../images/2016/03/LorenzeExample.png" rel="attachment wp-att-103"><img class="alignnone wp-image-103 size-large" src="../images/2016/03/LorenzeExample-1024x671.png?fit=656%2C430" alt="LorenzeExample" srcset="../images/2016/03/LorenzeExample.png?resize=1024%2C671 1024w, ../images/2016/03/LorenzeExample.png?resize=300%2C197 300w, ../images/2016/03/LorenzeExample.png?resize=768%2C503 768w, ../images/2016/03/LorenzeExample.png?w=1175 1175w" sizes="(max-width: 656px) 100vw, 656px" data-recalc-dims="1" /></a>

Luckily, because we had the year-to-date salary of every employee in each dept, the calculation was extremely straightforward &#8211; and we were able to get to an annual coefficient for every single department as well as Lorenze curves based on 2015 salaries to help visualize the inequality.

<a href="https://i0.wp.com/www.quantifylouisville.com/wp-content/uploads/2016/03/LorenzCurves.png" rel="attachment wp-att-94"><img class="alignnone wp-image-94 size-large" src="../images/2016/03/LorenzCurves-1024x856.png?fit=656%2C548" alt="LorenzCurves" srcset="https://i0.wp.com/www.quantifylouisville.com/wp-content/uploads/2016/03/LorenzCurves.png?resize=1024%2C856 1024w, https://i0.wp.com/www.quantifylouisville.com/wp-content/uploads/2016/03/LorenzCurves.png?resize=300%2C251 300w, https://i0.wp.com/www.quantifylouisville.com/wp-content/uploads/2016/03/LorenzCurves.png?resize=768%2C642 768w, https://i0.wp.com/www.quantifylouisville.com/wp-content/uploads/2016/03/LorenzCurves.png?w=1312 1312w, https://i0.wp.com/www.quantifylouisville.com/wp-content/uploads/2016/03/LorenzCurves.png?w=1968 1968w" sizes="(max-width: 656px) 100vw, 656px" data-recalc-dims="1" /></a>

While this is all well and good, as a couple of numbers guys, we really like to do comparisons. In this case, the Gini is a natural comparison tool for income distribution among two or more groups of people (typically, country populations). And, thanks to the [World Bank](http://api.worldbank.org/v2/en/indicator/si.pov.gini?downloadformat=csv), we could attempt to  compare all of our department Ginis with global Ginis in order to answer questions like, which country has an income distribution most similar to to the Louisville Zoo? (Hey guys, it’s Bhutan in 2003!)

<a href="../images/2016/03/DensityPlot.png" rel="attachment wp-att-95"><img class="alignnone wp-image-95 size-large" src="../images/2016/03/DensityPlot-1024x856.png?fit=656%2C548" alt="DensityPlot" srcset="../images/2016/03/DensityPlot.png?resize=1024%2C856 1024w, ../images/2016/03/DensityPlot.png?resize=300%2C251 300w, ../images/2016/03/DensityPlot.png?resize=768%2C642 768w, ../images/2016/03/DensityPlot.png?w=1312 1312w, ../images/2016/03/DensityPlot.png?w=1968 1968w" sizes="(max-width: 656px) 100vw, 656px" data-recalc-dims="1" /></a>

To see how the two sets of Ginis compare, we created the density plot above to depict the distributions of both country and department Ginis, as well as their overlap. While some overlap does exist between the two distributions, for the most part the pink shaded area representing department Ginis is to the left of the Aqua-colored country Ginis. What this means is that Louisville Metro Government salaries are more equally distributed (its Ginis tend to be smaller) than most national incomes.

Sadly, this means that there are many members of both groups of Ginis that we couldn&#8217;t _really_ compare to each other (all the shaded areas that do not overlap). So, in order to be able to properly compare the two sets of data, we ‘normalized*’ both sets (a fancy way of saying that we forced the shaded areas to sit on top of each other). After doing this, we were able to make some pretty great comparisons &#8211; such as, which country is relatively as unequal as &#8211; say &#8211; the Russian Federation in 1996 (24/7 SPOILERS: it’s the Metro Council!).

So, _should_ one say that the salary distribution of the Coroner’s Office is really that similar to Hungary’s income distribution in 1987? No, not directly (and maybe not even sanely). But one _could_ say that the salary distribution of the Coroner’s Office is to the Louisville Metro Government what Hungary’s 1987 income distribution is to the world. Similarly, one could say that the salary distribution of the Kentuckiana Works Foundation is to the Louisville Metro Government what El Salvador’s 1999 income distribution is to the world.

We’ll leave you with <a href="http://www.quantifylouisville.com/wp-content/uploads/2016/03/deptTable.html" target="_blank">this table</a> to discuss amongst yourselves.

**<span style="color: #ff6600;">SOME INTERESTING TIDBITS FROM OUR INITIAL DATA EXPLORATION</span>**

The median salary across all government departments for the period 2008 &#8211; 2015  is about $41,350. Three departments, EMS, LMPD (a chief and an officer), & the Director of the Library account for the top ten highest individual salaries since 2008. Within only 2015, LMPD accounts for six of the top ten salaries, with Waterfront Development, the Zoo, the Library, and Metro Corrections accounting for the other four.

Due to their heavy leaning on part-time & seasonal employees (we hope anyway), the heads of both the Zoo & the Belle of Louisville currently earn the highest multiples above their departments median salary (roughly 19 & 12 times, respectively).

**Neighborhoods Department**

This marks a stark contrast to the beginning of the dataset when the head of the Neighborhoods department made over 60 times the departmental median salary, nine additional Neighborhoods employees made more than 30 times over, and contributed the most unequal Gini in the government data set.

After some digging, the reason for this is pretty obvious, if not terrifying. In 2008, there were 167 employees listed as ‘Youth Worker-Intern.’ On average, these interns made roughly $600 in 2008 &#8211; and, combined, the 167 interns made $102,641 for the entire year. In comparison, the Director of the Neighborhoods department that year made $104,448 &#8211; meaning this one person within the department made more in 2008 than 167 other employees combined. It appears that this department folded after 2010, and possibly morphed into a new department in 2013 &#8211; [The Department of Safe and Healthy Neighborhoods](https://louisvilleky.gov/government/safe-healthy-neighborhoods/meet-our-team). However, this department itself doesn’t exist in this database (despite its Director being included under the Public Health & Wellness department), so we don’t know how income is distributed within this department or its counterpart today.

Let’s not get bogged down in negativity. For every bad apple, there’s some cliche that says there are good ones. In this case, our good apple is the Fire Department**. The department takes not just the top spot, but the top four spots in terms of income equality (for years 2008, 2011, 2012, and 2014 respectively). In 2008, the highest income earner in the Fire Department made just twice the median income earner &#8211; a relatively low premium that has persisted through 2015 as well.

As was the case in the Neighborhoods Department, digging into the data helps us to better understand what is happening here (although, in this case the cause doesn’t seem so crummy). In 2008, the Louisville Fire Department clocked a crazy amount of overtime pay &#8211; which helped boost median incomes, and creating more equality. In fact, the department regularly rests at the top of the list for overtime pay &#8211; which likely goes more toward the median worker than it does the highest paid.

As always, feel free to get in touch with either of us if you have any questions!

michaelweis@gmail.com or @michael_weis on Twitter

bickel.eric@gmail.com or @eric_bickel on Twitter

###### **_* The adjustment factor was calculated by removing the average of the category (dept or country) and then multiplying back in the average of the entire data set. This ‘removes’ the average effect of the category &#8211; allowing them to all shift closer to the total mean._**

###### **_** Technically, there were a few better than this but they all had less than 20 employees working for them._**

###### **__Data Note: _We limited our dataset to only pre-2016 and to total payments of at least $365 (or at least one dollar per day). This removed 6,700 records, including one exceptionally generous Zoo employee that apparently donated nearly $30K back to the department in 2015._**