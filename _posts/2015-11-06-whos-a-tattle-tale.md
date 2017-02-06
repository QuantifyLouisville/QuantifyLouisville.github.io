---
id: 37
title: 'Who&#8217;s a Tattle-Tale?'
date: 2015-11-06T03:37:32+00:00
author: Michael Weis
layout: post
guid: http://www.quantifylouisville.com/?p=37
permalink: /whos-a-tattle-tale/
categories:
  - Health and Wellness
  - Uncategorized
format: video
---
<div>
  <h4>
    <span style="color: #ff6600;">What&#8217;s All The Complaining About?</span>
  </h4>
  
  <p>
    <span style="font-weight: 400;">In our </span><a href="http://www.quantifylouisville.com/adventures-in-sad-data/"><span style="font-weight: 400;">previous post</span></a><span style="font-weight: 400;">, we found out how likely your dog was to die once surrendered to Animal Services. Hopefully, a look into Health Complaints will be a bit less morbid. The </span><a href="http://portal.louisvilleky.gov/dataset/complaints-data"><span style="font-weight: 400;">data we explored</span></a><span style="font-weight: 400;"> represents “complaints reported by the public and investigated by Louisville Metro Department of Public Health and Wellness.”</span>
  </p>
  
  <div>
    <h4>
      <span style="color: #ff6600;"><strong>The Data</strong></span>
    </h4>
  </div>
</div>

<!--more-->

<span style="font-weight: 400;">As soon as we opened the data, we naturally wanted to see which zip codes were the biggest tattle-tales. Maturer heads prevailed, unfortunately, and we then began to wonder what storylines existed in the data. With the data covering all health complaints within the city, along with several characteristics of each complaint (type, location, date made, date resolved, etc.) we started to whittle down the list of questions to just a couple: </span>

<li style="font-weight: 400;">
  <span style="font-weight: 400;">Are types of complaints clustered in certain parts of the city?</span>
</li>

<li style="font-weight: 400;">
  <span style="font-weight: 400;">Do certain regions and certain complaints tend to take longer to resolve &#8211; if they are resolved at all?!</span>
</li>

<span style="color: #ff6600; font-size: 16px; font-weight: 600;">What We Did With It</span>

<span style="font-weight: 400;">As we began to summarize the data, we noticed that a few types of complaints were much more common than others. Since 2011, for instance, there have been 5,514 complaints about rabies! [Sadly, the data does not specify species of the accused]</span>

<span style="font-weight: 400;">Despite the funny and terrifying number of rabies complaints, we realized that we were really more concerned with how many of a specific type of complaint were left unresolved. The right-most column in the table below shows just that (along with the number of open and total complaints by type). A few things stood out to us:</span>

<li style="font-weight: 400;">
  <span style="font-weight: 400;">If you are thinking about making a Food Manager complaint, you may want to adjust your expectations downward a bit, way down&#8211; nearly 2/3rds of Food Manager complaints are currently unresolved</span>
</li>

<li style="font-weight: 400;">
  <span style="font-weight: 400;">Calling to complain about mosquitoes and getting a resolution is basically a coin flip</span>
</li>

<li style="font-weight: 400;">
  <span style="font-weight: 400;">Just over 30% of Hotel or Motel complaints are currently unresolved (Yessss, the Economy Inn is in there a few times)</span>
</li>

<li style="font-weight: 400;">
  <span style="font-weight: 400;">To the likely relief of everyone in the city, only 2% of rabies complaints are currently unresolved, with the majority occurring in 2015</span>
</li>

[<img class="aligncenter wp-image-44 size-full" src="../images/2015/10/table.png?fit=656%2C396" alt="table" srcset="../images/2015/10/table.png?w=692 692w, ../images/2015/10/table.png?resize=300%2C181 300w" sizes="(max-width: 656px) 100vw, 656px" data-recalc-dims="1" />](../images/2015/10/table.png)

<span style="font-weight: 400;">As that last bullet implies, how long the complaint has been unresolved is also fairly important to consider. This led us to create the graph below in order to highlight how many complaints remain open in 2015 by the year reported. For instance, there are currently around 50 complaints regarding meth labs reported in 2011 and 2012 that are still open today. Which, considering those are illegal and probably easy to check into, is pretty wild.</span>

_<span style="font-weight: 400;">[As a brief aside, we previously mentioned that rabies has experienced a pretty serious uptick in 2015. We are not saying this is the zombie apocalypse, but we are also not NOT saying that either (“You don&#8217;t know what it&#8217;s like out there. You may think you do but you don&#8217;t.” &#8212; RG).]</span>_

<span style="font-weight: 400;">The big kahuna here, however, is the fact that Food Managers have 800 complaints in 2013 and 2014 that are still open today. And given that these complaints make up close to half of all open complaints within the city, it makes sense to dive into this complaint type a little bit more to better understand what’s going on (and, maybe, where we should avoid eating) from a geographical perspective.</span>

[<img class="aligncenter wp-image-47 size-large" src="https://i0.wp.com/www.quantifylouisville.com/wp-content/uploads/2015/10/barchart-1024x615.png?fit=656%2C394" alt="barchart" srcset="../images/2015/10/barchart.png?resize=1024%2C615 1024w, ../images/2015/10/barchart.png?resize=300%2C180 300w, ../images/2015/10/barchart.png?w=1312 1312w, ../images/2015/10/barchart.png?w=1968 1968w" sizes="(max-width: 656px) 100vw, 656px" data-recalc-dims="1" />](../images/2015/10/barchart.png)

<span style="font-weight: 400;"> The Jefferson County map below features  the number of open complaints by zip code, with more open complaints shown by a darker shade of blue. It’s pretty clear where the complaints for food managers are coming from &#8211; zip code 40219 made up about 10% of all 1,100 or so open complaints for food managers despite having only 5% of Jefferson County’s population and 5% of its Food Service and Restaurant locations.</span>

<span style="font-weight: 400;">Although the categories between the Health Complaints and Census Stats don’t entirely line up, it is reasonable to assume that Okolona doesn’t account for 10% of all of Jefferson County’s Food Manager locations.</span>

[<img class="aligncenter wp-image-68 size-full" src="../images/2015/10/Rplot02.png?fit=656%2C437" alt="Rplot02" srcset="../images/2015/10/Rplot02.png?w=787 787w, ../images/2015/10/Rplot02.png?resize=300%2C200 300w" sizes="(max-width: 656px) 100vw, 656px" data-recalc-dims="1" />](../images/2015/10/Rplot02.png)

<div>
  <h4>
    <span style="font-weight: 400;">Diving deeper into 40219, the map below the next paragraph plants a dot for each open complaint in the region. We can see that the vast majority of the open complaints follow along Preston Highway. Highlights (lowlights?) include 18 instances of quarantines, and a whopping 30 complaints spanning just three establishments. </span>
  </h4>
  
  <h4>
    <span style="font-weight: 400;">Proudly, expanding to the top five establishments with multiple open complaints includes the former employer of one of your authors and the list in general is a wonderfully nostalgic trip through our childhood dining experiences.</span>
  </h4>
  
  <p>
    <a href="../images/2015/11/40219-Food-Establishments.png"><img class="aligncenter wp-image-74 size-large" src="../images/2015/11/40219-Food-Establishments-1024x856.png?fit=656%2C548" alt="40219-Food-Establishments" srcset="../images/2015/11/40219-Food-Establishments.png?resize=1024%2C856 1024w, ../images/2015/11/40219-Food-Establishments.png?resize=300%2C251 300w, ../images/2015/11/40219-Food-Establishments.png?w=1312 1312w, ../images/2015/11/40219-Food-Establishments.png?w=1968 1968w" sizes="(max-width: 656px) 100vw, 656px" data-recalc-dims="1" /></a>
  </p>
  
  <h4>
    <span style="color: #ff6600;">What We Found</span>
  </h4>
</div>

<span style="font-weight: 400;">It is important to note that the data itself did give us pause when evaluating its true value. In mind-bending fashion, a few Health Complaints were resolved before they were made, and, when combined with Health Inspections data, one lucky establishment has managed to have its next inspection scheduled right around the corner in the year 3201. As such, we are left with a minimum of three scenarios:</span>

<li style="font-weight: 400;">
  <span style="font-weight: 400;">The data is mostly accurate, and there really is a two in three chance that a Food Manager will avoid any meaningful action for a given complaint</span>
</li>
<li style="font-weight: 400;">
  <span style="font-weight: 400;">The data is mostly inaccurate and, therefore, difficult to use to garner any true insights about Health Complaints in our city</span>
</li>
<li style="font-weight: 400;">
  <span style="font-weight: 400;">There is unprovided context for this data, such as the possibility that an open status reflects an ongoing investigation, albeit one with an exceptionally long lifecycle</span>
</li>

<span style="font-weight: 400;">Regardless, the number of complaints for food managers is very likely to be much higher than anything else. And, the clustering of food manager complaints in 40219 is very apparent. Based on this data, if you are a health-violating Food Manager out by J-Mall, you have a decent chance of skating by.</span>

<span style="font-weight: 400;">However, rabies calls are taken pretty seriously.</span>

<span style="font-weight: 400;">As always, feel free to get in touch with either of us if you have any questions!</span>

<span style="font-weight: 400;">michaelweis@gmail.com</span> <span style="font-weight: 400;">or  @michael_weis </span>

<span style="font-weight: 400;">bickel.eric@gmail.com</span> <span style="font-weight: 400;">or @eric_bickel </span>