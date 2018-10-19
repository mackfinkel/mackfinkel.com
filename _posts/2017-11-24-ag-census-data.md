---
title: Importing USDA Census of Agriculture Data into R
layout: default
image: https://steemitimages.com/DQmZBTHdhGcN64hLeDGKmUxSbqrxyFmY3a4tBwhFpjHCLwM/Precision_Farming_in_Minnesota_-_Natural_Colour.jpg
description: Post-Thanksgiving, America is experiencing a different kind of hunger – a hunger for agricultural data that is easy to process in the programming language R.
categories: [agriculture, statistics, r]
crossposts:
  - name: steemit
    url: https://steemit.com/education/@somethingburger/importing-usda-census-of-agriculture-data-into-r-1511564625-3931718
published: true
---

[![Precision_Farming_in_Minnesota_-_Natural_Colour.jpg](https://steemitimages.com/DQmZBTHdhGcN64hLeDGKmUxSbqrxyFmY3a4tBwhFpjHCLwM/Precision_Farming_in_Minnesota_-_Natural_Colour.jpg)<center>Farms in Minnesota as seen by Satellite</center>](https://commons.wikimedia.org/wiki/File:Precision_Farming_in_Minnesota_-_Natural_Colour.jpg)

# Finding Data

The [USDA Census of Agriculture ](https://www.agcensus.usda.gov/) (or "Ag Census") is an incredible source of pretty much any kind of agricultural data that you might be looking for, and I've used this census in two [previous](https://steemit.com/food/@somethingburger/the-tragedy-of-pork-agriculture) [posts](https://steemit.com/food/@somethingburger/walking-through-data-hog-and-pig-farms). In those posts, I copied and pasted relevant information from a .pdf file. This was fine because I wasn't working with that much data, but this definitely wouldn't work if I were doing something bigger, like looking at [factory farms by county](http://factoryfarmmap.org/).

Browsing through the Ag Census site, there seems to be no clear way to get all of the census information at once. There are [.pdf files](https://www.agcensus.usda.gov/Publications/2012/Full_Report/Volume_1,_Chapter_1_US/usv1.pdf) and [.txt files](https://www.agcensus.usda.gov/Publications/2012/Full_Report/Volume_1,_Chapter_1_US/usv1.txt) with information and tables, but none of those are easily importable. There is also a [Quick Stats database](https://quickstats.nass.usda.gov/?source_desc=CENSUS) with this information, which you can query on the website or through [an API](https://quickstats.nass.usda.gov/api). This was more promising but still wasn't not quite what I was looking for. I wanted all of the raw data, without any processing done. Then I noticed a link at the bottom of the API page, which lead to [all the raw Ag Census data in tabular format](ftp://ftp.nass.usda.gov/quickstats/). This was exactly what I was looking for.

[![all the data](https://steemitimages.com/DQmNo2UV3LXX7xKEeMqxGr1qe82DCqRRfqK15QuQo7Fgbi1/Screen%20Shot%202017-11-24%20at%203.32.49%20PM.png)<br><center>All Ag Census Data</center>](ftp://ftp.nass.usda.gov/quickstats/)

# Importing Data

After finding the data, I wrote an R script that downloads all Ag Census data from the internet, converts it to R, and saves it in a folder.

```
#download, convert, import US Census of Agriculture Data into R

#set up
dir.create("raw")
dir.create("rImported")

#all files from USDA FTP quickstats site ftp://ftp.nass.usda.gov/quickstats/
#best way for of downloadable tabular census data I know of
#download to censusData
setwd("raw")
download.file("ftp://ftp.nass.usda.gov/quickstats/qs.census2002.txt.gz", "2002.txt.gz")
download.file("ftp://ftp.nass.usda.gov/quickstats/qs.census2007.txt.gz", "2007.txt.gz")
download.file("ftp://ftp.nass.usda.gov/quickstats/qs.census2012.txt.gz", "2012.txt.gz")

#convert to r
cag2002 <- read.table(gzfile("2002.txt.gz"), sep="\t", header=TRUE)
cag2007 <- read.table(gzfile("2007.txt.gz"), sep="\t", header=TRUE)
cag2012 <- read.table(gzfile("2012.txt.gz"), sep="\t", header=TRUE)

#save
setwd("../rImported")
save(cag2002,file="cag2002.Rda")
save(cag2007,file="cag2007.Rda")
save(cag2012,file="cag2012.Rda")
```
<br>

Here's what this looks like imported (in RStudio):

<center><img src="https://steemitimages.com/DQmaBS3S5A7CpuJ279MZ8Fzev6cLFPwuRt53qRHfTMEc5iD/Screen%20Shot%202017-11-24%20at%203.32.20%20PM.png" alt="imported"><br> In R: Ag Census data by year</center>
<br>

Now I have a many millions of instances of data that spans across 3 different years to work with. Variable names are listed in the [Quick Stats API documentation](https://quickstats.nass.usda.gov/api). I'm also ready as soon as the 2017 Ag Census comes out, [which is soon](https://www.agcensus.usda.gov/Newsroom/2017/09_25_2017.php). When I work with this data in the future, I will be able to analyze it in a pipeline: everything I post will be immediately reproducible by anyone else, and there won't be any room for potential copy-paste errors!

As always, this code is on [GitHub](https://github.com/mackfinkel/agricultureData). The data files themselves are too large to be uploaded there (> 25 mb).