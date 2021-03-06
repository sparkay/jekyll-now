---
layout: post
title: Data Structures and Visualization
tags: R Python matplotlib ggplot
---
## or matplotlib versus ggplot

I am currently on a quest to improve my python abilities. On this quest, my love for pandas is matched only by my loathing of matplotlib. There appears to be a philosophy out there that one should learn matplotlib/pyplot as the basic python visualization tool. This is not unlike this (link) debate on ggplot versus base graphics in R. However, given the availability of libraries like ~~seaborn~~ Altair and plotnine, this practice should stop. 

Why? 

Two words: tidy data.

Matplotlib assumes a columnar data format (probably because of its origins as a replacement for array-based MATLAB tools). Data Analytics/Science is moving quickly away from wide or column-based data and using more and more long or tidy data. While you can visualize tidy data in matplotlib/pyplot, it is a PIA. Allow be to illustrate below.

If your data is in this format:
[show pivot table]

You can generate a lineplot of TMAX and TMIN quite simply using one line of code:
[code]

However, if your data is in this format:
[show long data]

the required slicing needed to transform it to the expected pyplot input is annoyingly complex:
[code]

(Ok, yes, you could just use pandas to pivot the data back to wide format and then do as above - getting your plotitng done in just two lines, but it doesn't invalidate my point that you shouldn't have to think about transforming your data just to plot it.)


Lets compare this to the opposite situation in R/ggplot.
Here is how to create the same line plot from tidy data in ggplot:


Now, ggplot does have the opposite problem, in a way. If you have columnar data, you first have to transform it to tidy format to do anything. BUT YOUR ARE GOING TO DO THIS ANYWAY. The transformation from tidy to columnar is the more unnatural and less useful direction. Yes, there are occaisonal calculations that bennefit from operating on columns and then converting back to long-form (e.g. getting the difference between two different value serieses by row), but visualization should not be one of those cases if only because you do so much of it.

Now some people will point out that it is still useful to understand the matplotlib syntax in order to customize your python figures. This is true, and this is an area where R still has Python beat. You can do all of your customization in ggplot without having to reference the base R plotting library. (See my post on creative ggplot use for an example) Someone, someone should probably write a more userfriendly wrapper for matlabplot to do the same.

See http://pltn.ca/plotnine-superior-python-ggplot/ for a roundup of python ggplot ports: "Python users are forced to carry the extra cognitive load of learning several visualization libraries, learning their implementation details, and working around their limitations."

also https://dsaber.com/2016/10/02/a-dramatic-tour-through-pythons-data-visualization-landscape-including-ggplot-and-altair/ has a nice comparison of different python plotting methods.
