---
id: 14
title: Adventures in Sad Data
date: 2015-09-02T04:11:52+00:00
author: Eric
layout: post
guid: http://www.quantifylouisville.com/?p=14
permalink: /adventures-in-sad-data/
categories:
  - LMAS
  - Probability City
tags:
  - LMAS
  - LouieStat
  - LouMetro
  - ProbabilityCity
---
#### <span style="color: #ff6600;"><strong>Will Your Dog Make The Cut?</strong></span>

So, in this inaugural post we&#8217;re going to start by looking at arguably the saddest set of data in Louisville&#8217;s arsenal – <a href="http://portal.louisvilleky.gov/dataset/animal-services-outcomes-data" target="_blank">Louisville Metro Animal Services (LMAS) Animal Outcomes</a>. Essentially, this data tracks every dog, cat, rabbit, guinea pig, lizard, and horse (yes.) that makes its way through the doors at LMAS.

#### <span style="color: #ff6600;"><strong>What We Did With It</strong></span>

<a href="https://ericbickel.shinyapps.io/app1" target="_blank">We made an app to predict how likely your dog is to die!</a>

<!--more-->Without getting into the gory math details around the models built to test each characteristic (if you want it, let me know), I was able to find that there are roughly five characteristics that most influence a dog&#8217;s chances of being euthanized:

  * <span style="color: #ff6600;">Whether it is a pit breed<br /> </span>
  * <span style="color: #ff6600;">Gender</span>
  * <span style="color: #ff6600;">Whether it is Spayed/Neutered</span>
  * <span style="color: #ff6600;">Age</span>
  * <span style="color: #ff6600;">Size</span>

Based on the previously mentioned models, I can see how each characteristic increases or decreases the chances for the average dog coming into LMAS to be euthanized. For instance, a dog&#8217;s chances of being euthanized are more than 150% greater if that dog is a pit bull, and the chances skyrocket if that pit bull is a non-neutered male (the chances are roughly 450% higher). Age, while still pretty important, still has an impact – as a dog&#8217;s chances of being put to sleep are about 16% higher if they are older than 7 years old. And as far as size is concerned, being smaller definitely pays off – chances for a dog to be euthanized decrease by nearly 90% if they are toy-sized and 80% for small-sized pooches.

Now, there are tons of combinations of these variables that are unique to every dog. So, I wanted to hand the power of this analysis over to YOU the reader to see how your very own dog will fare within LMAS. The app will allow you to make selections around your dog&#8217;s breed, gender, age, and size.
  
The first thing you may notice as you make new selections, the charts to the right start to move around. The top chart (Figure 1) plots your dog&#8217;s chances against the average dog&#8217;s chances – pegged at the 13% mark mentioned above. If your bar is greater than this bar, then your dog has an above-average chance of being euthanized.<figure id="attachment_17" style="width: 597px" class="wp-caption alignnone">

[<img class="wp-image-17 size-full" src="../images/2015/09/BarChart.png?fit=597%2C513" alt="One of these charts is a lot sadder than the other." srcset="../images/2015/09/BarChart.png?w=597 597w, ../images/2015/09/BarChart.png?resize=300%2C258 300w" sizes="(max-width: 597px) 100vw, 597px" data-recalc-dims="1" />](../images/2015/09/BarChart.png)<figcaption class="wp-caption-text">Figure 1: One of these charts is a lot sadder than the other.</figcaption></figure> 

The chart below this one (Figure 2) is a little more involved. It&#8217;s a distribution of 8,000 predictions of real dog&#8217;s with real outcomes within LMAS that were built using the models discussed. The average prediction is ~14%2, and the distribution will shade up to whatever odds the model predicts for your dog as you make your selections. The more shading, the greater the number of dogs who are less likely to be put to sleep than your own. In short, it&#8217;s bad if there&#8217;s a lot of dark gray.<figure id="attachment_16" style="width: 624px" class="wp-caption alignnone">

[<img class="wp-image-16 size-full" src="../images/2015/09/DistChart.png?fit=624%2C473" alt="Figure 2: This isn&#8217;t one of those things where being greater than the rest is a good thing." srcset="../images/2015/09/DistChart.png?w=624 624w, ../images/2015/09/DistChart.png?resize=300%2C227 300w" sizes="(max-width: 624px) 100vw, 624px" data-recalc-dims="1" />](../images/2015/09/DistChart.png)<figcaption class="wp-caption-text">Figure 2: This isn&#8217;t one of those things where being greater than the rest is a good thing.</figcaption></figure> 

#### <span style="color: #ff6600;"><strong>The Data</strong></span>

The Animal Outcomes data covers just about everything you can think of for each animal. It shows us the breed of each animal, appearance/age, its reason for coming in (owner surrender, impound, stuff like that), and how the animal leaves. While the main focus of this post is on the last of those, in reality the work going into this project covers the whole shebang. Specifically, we&#8217;re going to look at what characteristics tend to increase the odds that any given animal (in this case, a dog) is euthanized. Like I said&#8230;super sad data stuff here.
  
The data itself starts in January 2011, and over that time just over 50k animals came through LMAS. Of these, more than half were dogs. A lot of these animals come in multiple times. My own dog, Murray (aka A478026), is an example of this. However, not all are lucky enough to make it out alive. About 13% of all dogs that find their way into LMAS are ultimately put down.

Knowing that, I wanted to find out what pieces of information can lead to the greatest risk for a given dog when entering the doors of LMAS – and ultimately build something that lets people see how likely their own dog is to meet their maker within their walls.

#### <span style="color: #ff6600;"><strong>How We Built This Thing</strong></span>

Essentially, we pulled all of the data back to January 2011 and expanded the intake types, breeds, ages, genders, sizes, colors, and intake types for each and every dog that came through the doors. This gave us a ton of characteristics for every dog, each of them what is known as a &#8216;categorical&#8217; variable.
  
Categorical variables are true/false variables indicating whether each variable exists for each entry. For instance, if we were categorizing an entry for a male dog that is greater than 7 years old, then the gender categorical variables would be a 1 for &#8216;MALE&#8217; and the age categorical variables would be a 1 for &#8216;Greater than 7 Years Old&#8217; and a zero for everything else. We did this same technique for whether or not a dog was a pit breed, neutered/spayed, its size, etc.
  
In the end of this, we had a few hundred categorical variables to feed into models that are geared toward predicting likelihoods. To hit my statistics quota for the month, this type of model is known as a logistic regression (or, logit for short). Technically, I built about 6 individual of these using 6 different methodologies&#8230;but&#8230;I already hit my quota, so let&#8217;s just move on for now.

#### <span style="color: #ff6600;"><strong>In <span style="color: #ff6600;">Closing</span></strong></span>

A lot wasn&#8217;t fully covered here, and I&#8217;m sure we will dive more deeply into this data in future posts (and possibly continue building on this post in turn). But, as an inaugural post, I think it serves well at setting the stage of how we will be tackling these datasets as the city posts them out there.

Of course, if there are any questions or if anyone wants to talk more about the math behind this post, shoot me an email! You can reach me at eric.bickel@QuantifyLouisville.com or on the Twitter @eric_bickel

###### 1. This is ignoring dogs who are euthanized by request from their owner, which is a really weird policy for LMAS to have anyways.
  
2. Just 1 percentage point from the actual chances, I would like to point out. I`ll take a bow over here&#8230;