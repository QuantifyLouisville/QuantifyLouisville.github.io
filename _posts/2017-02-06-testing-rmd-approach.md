---
id: 91
title: Testing RMarkdown Approach
date: 2017-02-06T14:51:46+00:00
author: Eric Bickel
layout: post
guid: http://www.quantifylouisville.com/?p=91
permalink: /testing-rmd-approach/
categories:
  - Uncategorized
tags:
  - RMarkdown
  - R
---

<h1>
<big><b> OPTIMIZATION TECHNIQUES </b></big>
</h1>
<h2>
<b> Background & Info </b>
</h2>
Optimization is a valuable tool for data analytics, and is widely used throughout many organizations in the decision making process. In this set of lectures, we are going to cover some of the basic methodologies for performing optimization:

-   Linear Programming
-   Simulation

While simulation modeling is becoming a more common form of optimization, the classical form of optimization via linear programming is still widely used in operations at many corporations as it deals with linear relationships between constraints. For example, production lines with fixed costs fit very much into a linear programming optimization model while a simulation model makes less sense (if costs don't vary, there's not a lot to simulate). We've also covered simulations quite a bit (we'll finish on simulations still here), so the focus of much of this week's lectures will be on the linear programming style.

<h2>
<b> What is Linear Programming </b>
</h2>
Using linear models to minimize loss (or, maximize benefit) has been around since WWII along with the advent of operations research. As a technique, it relies on functions and constraints that are linear - meaning they all exist on a constant plane. The benefit of this criteria is that these models are fairly easy to solve, and can be used in many ocmmon business practices.

A linear programming model consists of <b>three main components</b>:

-   An objective function of decision variables and their costs/profits
-   A set of constraints around each of the decision variables
-   Defined boundaries for the decision variables

In many cases, these won't be glaringly obvious. Working directly with business partners will help you to identify the constraints that surround your decision variables as well as the cost associated with the decisions. It is crucial that you clearly define these parameters, as <b>your</b> output will only be as good as <b>their</b> input.

For solving these types of problems, there are two main routes:

-   Simplex Algorithm
-   Interior Point Algorithm

<b>Simplex Algorithm</b> is the most common algorithm for solving linear programming problems - and is the algorithm most software uses today to solve them. There are variants of this algorithm used for large scale problems, but as long as you have enough information you can find the region that satisfies all constraints (the <i>feasible region</i>) using this method.

The <b>Interior Point Algorithm</b> is useful when the information provided is large and sparse. This method starts from a point within the feasible region to solve one constraint, and then iteratively approaches the optimum.

<h4>
<b> Let's look at an example </b>
</h4>
<i> A small business sells two products - Product 1 and Product 2. Each ton of Product 1 takes 30 working hours to make, and each ton of Product 2 takes 20 working hours. The business has a maximum of 2,700 working hours for the period considered.

As for machine hours, each ton of Products 1 and 2 consumes 5 and 10 machine hours, respectively. There are 850 machine hours available.

Each ton of Product 1 yields 20 dollars of profit, while Product 2 yields 60 dollars for each ton sold.

For technical reasons, the firm must produce a minimum of 95 tons in total between both products. We need to know how many tons of Product 1 and 2 must be produced to maximize total profit. </i>

This is an ideal setup for a linear programming model for optimizing production of the products. To do so, we first need to define our parameters. Once we know those, we can use the <b>lp</b> function in the lpSolve package in R to solve our model.

<b> Objective Function </b>

The objective function is the combination of <b>decision variables</b> and their associated <b>costs</b>.

The decision variable is often the easiest to find in these problems, as they are the final outcome of the model. In this case, the decision variables are the production and Product 1 and Product 2.

As far as the cost, this one can be tricky. Most textbooks will call these costs, but in reality it can reflect cost <b>or</b> revenue associated with each decision variable. This is an incredibly important distinction, as it defines whether you are trying to <b>maximize</b> revenues or <b>minimize</b> cost. In our example, we know that Product 1 yields 20 dollars of profit and Product 2 yields 60 dollars. So, we will be maximizing profits of 20 per Product 1 and 60 per Product 2.

<b> Decision Variable Constraints </b>

Aside from the cost or profit, just about every other bit of information when optimizing can be thought of as a constraint. For instance, we know that it takes 30 hours to make Product 1 and 20 hours to make Product 2. So, hours worked of 30 and 20 are one set of constraints. We also know that it takes 5 machine hours to make Product 1 and 10 hours for Product 2. So, machine hours of 5 and 10 are another set of constraints. Last, we also know that we need to make at least 1 unit of each product. So, 1 unit of Product 1 and 1 unit of Product 2 is our final set of constraints.

Constraints by definition, however, are inequalities around boundaries. Meaning we have a limit for the constraints, but we can operate either above or below that limit depending on what the constraint is. For instance, for the working hours constraints c(30, 20), we know we have a cap of 2,700 working hours total. So, the working hours (WH) constraint looks like:

<code><b>WH: 30P1 + 20P2 &lt;= 2700</b></code>

Additionally, for the machine hours constraints c(5, 10), we know we have a cap of 850 machine hours total. So, the machine hours (MH) constraint looks like this:

<code><b>WH: 5P1 + 10P2 &lt;= 850</b></code>

And, finally, for the number of units produced constraints c(1, 1), we know we need to produce at least 95 tons of both products. So, the minimum production (MP) constraint looks like this:

<code><b>WH: P1 + P2 &gt;= 95</b></code>

So, the set c(2700, 850, 95) is the set of <b>defined boundaries</b> for the decision variable constraints c(30, 20, 5, 10, 1, 1).

<b> Objective Function </b>

If we put all of this together, we can build our object function that we will maximize along with the defined constraints as:

<code><b> MAX p = 20P1 + 60P2 </b><br> WH) 30P1 + 20P2 &lt;= 2700 <br> MH) 5P1 + 10P2 &lt;= 850 <br> MP) P1 + P2 &gt;= 95 </code>

Where we want to maximize the profit equation p given constraints WH, MH, and MP. Now that we have set our problem up, we can solve this linear programming model in R

<h2>
<b> Solve the Objective Function with Linear Programming </b>
</h2>
<h3>
<b> Load Packages & Set Themes </b>
</h3>
``` r
# Load packages
library(lpSolve)
```

    ## Warning: package 'lpSolve' was built under R version 3.2.5

``` r
library(ggplot2)
```

    ## Warning: package 'ggplot2' was built under R version 3.2.5

``` r
library(ggthemes)
```

    ## Warning: package 'ggthemes' was built under R version 3.2.4

``` r
library(extrafont)
```

    ## Warning: package 'extrafont' was built under R version 3.2.3

``` r
library(scales)
```

    ## Warning: package 'scales' was built under R version 3.2.5

``` r
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 3.2.3

``` r
library(reshape2)
library(plotly)
```

    ## Warning: package 'plotly' was built under R version 3.2.5

``` r
# Set plot theme
theme_set(
  theme_bw(base_family = 'Trebuchet MS', base_size = 12) +
    theme(
      plot.title = element_text(face = 'bold', hjust = 0),
      text = element_text(colour = '#4e5c65'),
      panel.background = element_rect('white'),
      strip.background = element_rect('#f0f2f3', colour = 'white'),
      plot.background = element_rect('white'),
      panel.border = element_rect(colour = 'white'),
      panel.grid.major.x = element_blank(),
      panel.grid.major.y = element_blank(),
      panel.grid.minor.y = element_blank(),
      legend.background = element_rect('white'),
      legend.title = element_blank(),
      legend.position = 'right',
      legend.direction = 'vertical',
      legend.key = element_blank(),
      strip.text = element_text(face = 'bold', size = 10),
      axis.text = element_text(face = 'bold', size = 9),
      axis.title = element_blank(),
      axis.ticks = element_blank()
    )
)
```

<h3>
<b> Define Parameters of Objective Function </b>
</h3>
The lp function in the lpSolve package requires five main arguments in order to build:

-   Direction (max or min) of the optimization ('direction')
-   Vector of costs or profits of the objective function ('objective.in')
-   Matrix of constraint coefficients ('const.mat')
-   Vector of direction for each constraint ('const.dir')
-   Vector of boundaries for each constraint ('const.rhs')

Since we've already defined those in our example, we can easily build them out individually.

``` r
## Define Parameters for Optimization Function

# Define direction of optimization
direction <- 'max' # Since we are maximizing profits as opposed to minimizing costs

# Define vector of costs or profits of the objective function
objective.in <- c(20, 60) # 20 dollars of profit for Product 1, 60 dollars for Product 2

# Define matrix of constraint coefficients
const.mat <- matrix(c(30, 20, 5, 10, 1, 1), # Each set of constraint coefficients in order
                    ncol = 2, # Built across two columns - one for Product 1 and one for Product 2
                    byrow = TRUE) # Down as many rows as we have constraints

# Define vector of direction for each of the constraints
const.dir <- c('<=', # The first constraint is WH below a boundary
               '<=', # The second constraint is MH below a boundary
               '>=') # The third constraint is MP above a boundary

# Define vector of boundaries for each constraint
const.rhs <- c(2700, # WH should be less than or equal to 2700
               850, # MH should be less than or equal to 850
               95) # MP should be greater than or equal to 95
```

<h3>
<b> Solve the Objective Function </b>
</h3>
Now that we have the objective function defined, we can now solve it using the lp function

``` r
## Solve Function Based on Paramters

# Find optimum something
prod.max <- lp(direction, 
               objective.in, 
               const.mat, 
               const.dir, 
               const.rhs)

## Observe Results

# First, let's look at the solution of our objective function 
data.frame('Product1' = prod.max$solution[1],
           'Product2' = prod.max$solution[2])
```

    ##   Product1 Product2
    ## 1       20       75

``` r
# Next, let's see what the maximized profit is
data.frame('Product1' = prod.max$solution[1],
           'Product2' = prod.max$solution[2],
           'MaxProfit' = prod.max$objval)
```

    ##   Product1 Product2 MaxProfit
    ## 1       20       75      4900

``` r
# Test to see if that number is accurate
prod.max$solution[1] * 20 + prod.max$solution[2] * 60
```

    ## [1] 4900

``` r
# Calculate the constraints for the optimum solution
data.frame('WH' = prod.max$solution[1] * 30 + prod.max$solution[2] * 20,
           'MH' = prod.max$solution[1] * 5 + prod.max$solution[2] * 10,
           'MP' = prod.max$solution[1] + prod.max$solution[2])
```

    ##     WH  MH MP
    ## 1 2100 850 95

<p>
<b> What We Now Know </b>
</p>
Based on the constraints defined in our problem as well as the profits associated with the decision variables, we will maximize profit by producting 20 units of Product 1 and 75 units of Product 2 while still satisfying all of our constraints.

<h2>
<b> Solve the Objective Function with Simulation </b>
</h2>
Aside from using linear programming, we could also solve the problem using simulation techniques that satisfy our constraints.

MAX p = 20P1 + 60P2 </b><br> WH) 30P1 + 20P2 &lt;= 2700 <br> MH) 5P1 + 10P2 &lt;= 850 <br> MP) P1 + P2 &gt;= 95

``` r
## Using Simulations to Optimize

# Define objective dataframe
obj.df <- data.frame()

set.seed(1620)
for (i in 1:10000) {
  prod1 <- round(runif(1, min = 1, max = 94), 0)
  prod2 <- 95 - prod1
  
  if ((prod1 * 30 + prod2 * 20 > 2700)|(prod1 * 5 + prod2 * 10 > 850)|(prod1 + prod2 < 95))
  {next} else {
  obj.df[i, 1] <- prod1
  obj.df[i, 2] <- prod2
  obj.df[i, 3] <- prod1 * 20 + prod2 * 60
  }
}

# Rename columns
names(obj.df) <- c('Product1', 'Product2', 'Profit')

# Remove rows where constraints were not met and duplicated values
obj.df <- obj.df[!is.na(obj.df$Profit), ]
obj.df <- obj.df[!duplicated(obj.df$Product1), ]

## Observe Results

# First, let's look at the solution of our objective function 
obj.df %>% 
  filter(Profit == max(Profit)) %>% 
  select(Product1, Product2)
```

    ##   Product1 Product2
    ## 1       20       75

``` r
# Next, let's see what the maximized profit is
obj.df %>% 
  filter(Profit == max(Profit)) %>% 
  select(Profit)
```

    ##   Profit
    ## 1   4900

``` r
# Calculate the constraints for the optimum solution
obj.df %>% 
  filter(Profit == max(Profit)) %>% 
  select(Product1, Product2) %>% 
  summarise('WH' = Product1 * 30 + Product2 * 20,
           'MH' = Product1 * 5 + Product2 * 10,
           'MP' = Product1 + Product2)
```

    ##     WH  MH MP
    ## 1 2100 850 95

``` r
data.frame('WH' = prod.max$solution[1] * 30 + prod.max$solution[2] * 20,
           'MH' = prod.max$solution[1] * 5 + prod.max$solution[2] * 10,
           'MP' = prod.max$solution[1] + prod.max$solution[2])
```

    ##     WH  MH MP
    ## 1 2100 850 95

``` r
## Visualize Results

# Decompose profit by product
profit.decomp <- data.frame('Scenario' = paste0('Scenario', seq(1, nrow(obj.df), by = 1)),
                            'Product1' = obj.df$Product1 * 20,
                            'Product2' = obj.df$Product2 * 60)

# Melt for plotting
profit.decomp <- melt(profit.decomp, id.vars = 'Scenario')

# Calculate units
for (i in 1:nrow(profit.decomp)) { 
  
  profit.decomp$units[i] <-
    if (profit.decomp$variable[i] == 'Product1') {
    profit.decomp$value[i] / 20
    } else {
    profit.decomp$value[i] / 60
    }
    
}

ggplotly( 
  
  ggplot(profit.decomp, aes(x = reorder(Scenario, -value), y = value, fill = variable, text = paste0(variable, ' Profit = ', value, ' at ', units, ' produced'))) + 
    geom_bar(stat = 'identity') + 
    scale_y_continuous(labels = dollar) + 
    labs(title = 'Total Profit by Production Mix') + 
    theme(axis.text.x = element_blank()),
  tooltip = 'text'
  
  )
```

<!--html_preserve-->

<script type="application/json" data-for="htmlwidget-2525">{"x":{"data":[{"x":[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61],"y":[400,420,440,460,480,500,520,540,560,580,600,620,640,660,680,700,720,740,760,780,800,820,840,860,880,900,920,940,960,980,1000,1020,1040,1060,1080,1100,1120,1140,1160,1180,1200,1220,1240,1260,1280,1300,1320,1340,1360,1380,1400,1420,1440,1460,1480,1500,1520,1540,1560,1580,1600],"text":["Product1 Profit = 400 at 20 produced","Product1 Profit = 420 at 21 produced","Product1 Profit = 440 at 22 produced","Product1 Profit = 460 at 23 produced","Product1 Profit = 480 at 24 produced","Product1 Profit = 500 at 25 produced","Product1 Profit = 520 at 26 produced","Product1 Profit = 540 at 27 produced","Product1 Profit = 560 at 28 produced","Product1 Profit = 580 at 29 produced","Product1 Profit = 600 at 30 produced","Product1 Profit = 620 at 31 produced","Product1 Profit = 640 at 32 produced","Product1 Profit = 660 at 33 produced","Product1 Profit = 680 at 34 produced","Product1 Profit = 700 at 35 produced","Product1 Profit = 720 at 36 produced","Product1 Profit = 740 at 37 produced","Product1 Profit = 760 at 38 produced","Product1 Profit = 780 at 39 produced","Product1 Profit = 800 at 40 produced","Product1 Profit = 820 at 41 produced","Product1 Profit = 840 at 42 produced","Product1 Profit = 860 at 43 produced","Product1 Profit = 880 at 44 produced","Product1 Profit = 900 at 45 produced","Product1 Profit = 920 at 46 produced","Product1 Profit = 940 at 47 produced","Product1 Profit = 960 at 48 produced","Product1 Profit = 980 at 49 produced","Product1 Profit = 1000 at 50 produced","Product1 Profit = 1020 at 51 produced","Product1 Profit = 1040 at 52 produced","Product1 Profit = 1060 at 53 produced","Product1 Profit = 1080 at 54 produced","Product1 Profit = 1100 at 55 produced","Product1 Profit = 1120 at 56 produced","Product1 Profit = 1140 at 57 produced","Product1 Profit = 1160 at 58 produced","Product1 Profit = 1180 at 59 produced","Product1 Profit = 1200 at 60 produced","Product1 Profit = 1220 at 61 produced","Product1 Profit = 1240 at 62 produced","Product1 Profit = 1260 at 63 produced","Product1 Profit = 1280 at 64 produced","Product1 Profit = 1300 at 65 produced","Product1 Profit = 1320 at 66 produced","Product1 Profit = 1340 at 67 produced","Product1 Profit = 1360 at 68 produced","Product1 Profit = 1380 at 69 produced","Product1 Profit = 1400 at 70 produced","Product1 Profit = 1420 at 71 produced","Product1 Profit = 1440 at 72 produced","Product1 Profit = 1460 at 73 produced","Product1 Profit = 1480 at 74 produced","Product1 Profit = 1500 at 75 produced","Product1 Profit = 1520 at 76 produced","Product1 Profit = 1540 at 77 produced","Product1 Profit = 1560 at 78 produced","Product1 Profit = 1580 at 79 produced","Product1 Profit = 1600 at 80 produced"],"key":null,"type":"bar","marker":{"autocolorscale":false,"color":"rgba(248,118,109,1)","line":{"width":1.88976377952756,"color":"transparent"}},"name":"Product1","legendgroup":"Product1","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text"},{"x":[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61],"y":[4500,4440,4380,4320,4260,4200,4140,4080,4020,3960,3900,3840,3780,3720,3660,3600,3540,3480,3420,3360,3300,3240,3180,3120,3060,3000,2940,2880,2820,2760,2700,2640,2580,2520,2460,2400,2340,2280,2220,2160,2100,2040,1980,1920,1860,1800,1740,1680,1620,1560,1500,1440,1380,1320,1260,1200,1140,1080,1020,960,900],"text":["Product2 Profit = 4500 at 75 produced","Product2 Profit = 4440 at 74 produced","Product2 Profit = 4380 at 73 produced","Product2 Profit = 4320 at 72 produced","Product2 Profit = 4260 at 71 produced","Product2 Profit = 4200 at 70 produced","Product2 Profit = 4140 at 69 produced","Product2 Profit = 4080 at 68 produced","Product2 Profit = 4020 at 67 produced","Product2 Profit = 3960 at 66 produced","Product2 Profit = 3900 at 65 produced","Product2 Profit = 3840 at 64 produced","Product2 Profit = 3780 at 63 produced","Product2 Profit = 3720 at 62 produced","Product2 Profit = 3660 at 61 produced","Product2 Profit = 3600 at 60 produced","Product2 Profit = 3540 at 59 produced","Product2 Profit = 3480 at 58 produced","Product2 Profit = 3420 at 57 produced","Product2 Profit = 3360 at 56 produced","Product2 Profit = 3300 at 55 produced","Product2 Profit = 3240 at 54 produced","Product2 Profit = 3180 at 53 produced","Product2 Profit = 3120 at 52 produced","Product2 Profit = 3060 at 51 produced","Product2 Profit = 3000 at 50 produced","Product2 Profit = 2940 at 49 produced","Product2 Profit = 2880 at 48 produced","Product2 Profit = 2820 at 47 produced","Product2 Profit = 2760 at 46 produced","Product2 Profit = 2700 at 45 produced","Product2 Profit = 2640 at 44 produced","Product2 Profit = 2580 at 43 produced","Product2 Profit = 2520 at 42 produced","Product2 Profit = 2460 at 41 produced","Product2 Profit = 2400 at 40 produced","Product2 Profit = 2340 at 39 produced","Product2 Profit = 2280 at 38 produced","Product2 Profit = 2220 at 37 produced","Product2 Profit = 2160 at 36 produced","Product2 Profit = 2100 at 35 produced","Product2 Profit = 2040 at 34 produced","Product2 Profit = 1980 at 33 produced","Product2 Profit = 1920 at 32 produced","Product2 Profit = 1860 at 31 produced","Product2 Profit = 1800 at 30 produced","Product2 Profit = 1740 at 29 produced","Product2 Profit = 1680 at 28 produced","Product2 Profit = 1620 at 27 produced","Product2 Profit = 1560 at 26 produced","Product2 Profit = 1500 at 25 produced","Product2 Profit = 1440 at 24 produced","Product2 Profit = 1380 at 23 produced","Product2 Profit = 1320 at 22 produced","Product2 Profit = 1260 at 21 produced","Product2 Profit = 1200 at 20 produced","Product2 Profit = 1140 at 19 produced","Product2 Profit = 1080 at 18 produced","Product2 Profit = 1020 at 17 produced","Product2 Profit = 960 at 16 produced","Product2 Profit = 900 at 15 produced"],"key":null,"type":"bar","marker":{"autocolorscale":false,"color":"rgba(0,191,196,1)","line":{"width":1.88976377952756,"color":"transparent"}},"name":"Product2","legendgroup":"Product2","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text"}],"layout":{"margin":{"t":46.2864259028643,"r":7.97011207970112,"b":15.1432129514321,"l":47.8206724782067},"plot_bgcolor":"rgba(255,255,255,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(78,92,101,1)","family":"Trebuchet MS","size":15.9402241594022},"title":"<b> Total Profit by Production Mix \u003c/b>","titlefont":{"color":"rgba(78,92,101,1)","family":"Trebuchet MS","size":19.1282689912827},"xaxis":{"domain":[0,1],"type":"linear","autorange":false,"tickmode":"array","range":[0.4,61.6],"ticktext":["Scenario9","Scenario43","Scenario31","Scenario24","Scenario33","Scenario27","Scenario49","Scenario4","Scenario50","Scenario17","Scenario3","Scenario7","Scenario26","Scenario6","Scenario53","Scenario40","Scenario39","Scenario5","Scenario19","Scenario13","Scenario23","Scenario57","Scenario34","Scenario44","Scenario28","Scenario47","Scenario1","Scenario59","Scenario21","Scenario42","Scenario2","Scenario46","Scenario55","Scenario8","Scenario48","Scenario18","Scenario38","Scenario37","Scenario20","Scenario29","Scenario51","Scenario58","Scenario35","Scenario54","Scenario45","Scenario25","Scenario36","Scenario30","Scenario16","Scenario60","Scenario32","Scenario14","Scenario41","Scenario22","Scenario11","Scenario12","Scenario10","Scenario15","Scenario61","Scenario56","Scenario52"],"tickvals":[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61],"ticks":"","tickcolor":null,"ticklen":3.98505603985056,"tickwidth":0,"showticklabels":false,"tickfont":{"color":null,"family":null,"size":0},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":false,"gridcolor":null,"gridwidth":0,"zeroline":false,"anchor":"y","title":"","titlefont":{"color":null,"family":null,"size":0},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"type":"linear","autorange":false,"tickmode":"array","range":[-245,5145],"ticktext":["$0","$1,000","$2,000","$3,000","$4,000","$5,000"],"tickvals":[0,1000,2000,3000,4000,5000],"ticks":"","tickcolor":null,"ticklen":3.98505603985056,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"Trebuchet MS","size":11.9551681195517},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":false,"gridcolor":null,"gridwidth":0,"zeroline":false,"anchor":"x","title":"","titlefont":{"color":null,"family":null,"size":0},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":"transparent","line":{"color":"rgba(255,255,255,1)","width":0.66417600664176,"linetype":"solid"},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":true,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(78,92,101,1)","family":"Trebuchet MS","size":12.7521793275218},"y":1},"barmode":"stack","hovermode":"closest"},"source":"A","config":{"modeBarButtonsToAdd":[{"name":"Collaborate","icon":{"width":1000,"ascent":500,"descent":-50,"path":"M487 375c7-10 9-23 5-36l-79-259c-3-12-11-23-22-31-11-8-22-12-35-12l-263 0c-15 0-29 5-43 15-13 10-23 23-28 37-5 13-5 25-1 37 0 0 0 3 1 7 1 5 1 8 1 11 0 2 0 4-1 6 0 3-1 5-1 6 1 2 2 4 3 6 1 2 2 4 4 6 2 3 4 5 5 7 5 7 9 16 13 26 4 10 7 19 9 26 0 2 0 5 0 9-1 4-1 6 0 8 0 2 2 5 4 8 3 3 5 5 5 7 4 6 8 15 12 26 4 11 7 19 7 26 1 1 0 4 0 9-1 4-1 7 0 8 1 2 3 5 6 8 4 4 6 6 6 7 4 5 8 13 13 24 4 11 7 20 7 28 1 1 0 4 0 7-1 3-1 6-1 7 0 2 1 4 3 6 1 1 3 4 5 6 2 3 3 5 5 6 1 2 3 5 4 9 2 3 3 7 5 10 1 3 2 6 4 10 2 4 4 7 6 9 2 3 4 5 7 7 3 2 7 3 11 3 3 0 8 0 13-1l0-1c7 2 12 2 14 2l218 0c14 0 25-5 32-16 8-10 10-23 6-37l-79-259c-7-22-13-37-20-43-7-7-19-10-37-10l-248 0c-5 0-9-2-11-5-2-3-2-7 0-12 4-13 18-20 41-20l264 0c5 0 10 2 16 5 5 3 8 6 10 11l85 282c2 5 2 10 2 17 7-3 13-7 17-13z m-304 0c-1-3-1-5 0-7 1-1 3-2 6-2l174 0c2 0 4 1 7 2 2 2 4 4 5 7l6 18c0 3 0 5-1 7-1 1-3 2-6 2l-173 0c-3 0-5-1-8-2-2-2-4-4-4-7z m-24-73c-1-3-1-5 0-7 2-2 3-2 6-2l174 0c2 0 5 0 7 2 3 2 4 4 5 7l6 18c1 2 0 5-1 6-1 2-3 3-5 3l-174 0c-3 0-5-1-7-3-3-1-4-4-5-6z"},"click":"function(gd) { \n        // is this being viewed in RStudio?\n        if (location.search == '?viewer_pane=1') {\n          alert('To learn about plotly for collaboration, visit:\\n https://cpsievert.github.io/plotly_book/plot-ly-for-collaboration.html');\n        } else {\n          window.open('https://cpsievert.github.io/plotly_book/plot-ly-for-collaboration.html', '_blank');\n        }\n      }"}],"modeBarButtonsToRemove":["sendDataToCloud"]},"base_url":"https://plot.ly"},"evals":["config.modeBarButtonsToAdd.0.click"],"jsHooks":[]}</script>
<!--/html_preserve-->
<p>
<b> What We Now Know </b>
</p>
While using the linear programming method gets us the exact number, it doesn't necessarily provide as much detail as we would like. Namely, what is the minimum value of Product 1 we can create while still meeting our constraints - and, comparatively, what is the minimum value of Product 2. Sometimes, due to unexpected circumstances (production line halts or scenario gaming, for instance) having this information is helpful.

Through our simulation, we can show that there is no feasibility in producing less than 20 units of Product 1 or 15 units of Product 2. And since our optimized solution is at a production of 20 units of Product 1, it's worth noting that our total profits can be heavily affected should production of Product 2 go down.
