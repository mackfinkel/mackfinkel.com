---
title: Mapping Animals in US Agriculture
layout: default
image: https://cdn.steemitimages.com/DQmQvNwQ9iCETM6um7SgmKVvsxFxDwg5orAq8o7X7wtLNSv/Screen%20Shot%202018-09-03%20at%209.55.11%20PM.png
description: This interactive map lets you investigate where animals are in the United States.
categories: [agriculture, statistics, animals]
published: true
---

This post is a continuation of my writing on rise of factory farming of [hogs](https://steemit.com/agriculture/@somethingburger/data-more-hogs-are-on-factory-farms-than-ever-before) and [cattle](https://steemit.com/education/@somethingburger/data-trends-in-beef-industry-1512418549-7278), the [waste](https://steemit.com/sndbox/@somethingburger/big-increases-in-animal-agriculture-waste) this industry creates, and the [burdens](https://steemit.com/health/@somethingburger/animal-agriculture-exacerbates-human-inequality-1513109831-4859874) faced by people [impacted](https://steemit.com/agriculture/@somethingburger/animal-agriculture-waste-mirrors-income-inequality-1533877034) by it. This map lets people explore some data for themselves.

The [2012 USDA Census of Agriculture](https://agcensus.usda.gov/Publications/2012/) contains county-level livestock head counts for several different types of animals. This census also records how much each type of animal weighs. US counties are extremely varied in size, and so are their animals. In 2012 the average American chicken weighed 6 pounds while the average cow weighed 1249.

In each county, the head count of each animal is multiplied by that animal's average weight, creating an estimate for the total amount of pounds of that animal in that county. Cattle, hogs, chickens, goats, ducks, and turkeys are counted in this map. All county animal weight totals are summed, and this total weight is divided to yield an estimate for pounds of animal per square mile for each county. This number is scaled by percentile and used to color code the map:

<center><img src="https://cdn.steemitimages.com/DQmQvNwQ9iCETM6um7SgmKVvsxFxDwg5orAq8o7X7wtLNSv/Screen%20Shot%202018-09-03%20at%209.55.11%20PM.png"><br>
<i>Data from 2012 USDA Census of Agriculture. Yellow counties have the greatest animal mass per area, while the purple counties have the least.</i></center>
<br>
An [interactive](http://mackfinkel.com/counties.html) version of this map is available (note: this loads slowly and displays poorly on mobile). There are some missing counties, and it seems that a technical issue left out data on Alaska entirely. On the interactive map, hovering over an individual county will show its their livestock counts:

<center><img src="https://cdn.steemitimages.com/DQmQXGMEETVSNBGiax5ZHzg9v5FVEyyosAMzFSiAkgeqHLo/Screen%20Shot%202018-09-03%20at%209.18.46%20PM.png"></center>
<br>
It was not surprising to see Duplin, NC rank at the top of this metric, because Duplin's hog industry is well known for [reckless pollution](https://qz.com/433750/the-world-eats-cheap-bacon-at-the-expense-of-north-carolinas-rural-poor/) that harms the health of the disproportionately poor, non-white county. Duplin was also the focus of a previous [article](https://steemit.com/health/@somethingburger/animal-agriculture-exacerbates-human-inequality-1513109831-4859874) and a [visualization](https://steemit.com/agriculture/@somethingburger/animal-agriculture-waste-mirrors-income-inequality-1533877034) I posted that discusses the strong presence of animal agriculture pollution in low income communities.

<center><img src="https://cdn.steemitimages.com/DQmeoBdDUX6VPCrV7KhvEy4w3dhCx2nUXsAHdEhVuL247Nd/Screen%20Shot%202018-09-03%20at%209.50.41%20PM.png"></center>
<br>
This data can also be revealing about random counties as well. For instance, Lancaster, PA had over 20 million chickens in 2012. It's not surprising that this county has had its own issues with [waste pollution](http://www.mcall.com/news/nationworld/pennsylvania/mc-nws-chicken-sludge-road-closure-lancaster-20170721-story.html) as well.

<p class="text-muted">All code used to process data and create graphs is on <a href="https://github.com/mackfinkel/misc/tree/master/posts/2018-09-04-animal-density-map">GitHub</a>. Content crossposted on <a href="https://steemit.com/agriculture/@somethingburger/mapping-animals-in-us-agriculture-1536029438">Steemit</a>.</p>