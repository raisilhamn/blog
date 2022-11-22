---
title: "Twitter Scraping With Snscrape"
date: 2022-11-21T10:55:47+07:00
draft: false

tags: ["Twitter"]
author: "Rais Ilham"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
hidemeta: false
comments: false
description: "Twitter Scraping Without using API"
disableShare: false
# disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
  image: "<image path/url>" # image path/url
  alt: "<alt text>" # alt text
  caption: "<text>" # display caption under cover
  relative: false # when using page bundles set this to true
  hidden: true # only hide on current single page
---

### What Is Data Scraping ?

> Data Scraping refers to the process of extracting data from sources that are publicly available. This data can be scraped from websites, social media platforms, and databases.

### Why is twitter data easy to scrape?

> Some people believe that Twitter data is easy to scrape because the platform makes its data publicly available to developers through its APIs. Other people believe that Twitter data is easy to scrape because the platform has a lot of users who generate a lot of data.

### Is it possible to scrape Twitter data without using the API?

> Yes, we can use snscrape package that include modules scape twitter data

### How do we do it ?

> Check code below

```python
import snscrape.modules.twitter as sntwitter
# Created a list to append all tweet attributes(data)
attributes_container = []
Q = '(sambo AND polisi) OR (joshua AND polisi)'

# Using TwitterSearchScraper to scrape data and append tweets to list
for i, tweet in enumerate(sntwitter.TwitterSearchScraper(Q +
'since:2022-10-01 until:2022-10-16 -filter:retweets -filter:links').get_items()):
    if i > 10000:
        break
    attributes_container.append([tweet.date, tweet.likeCount, tweet.content])

# Creating a dataframe from the tweets list above
tweets_df = pd.DataFrame(attributes_container, columns=[
                         "Date Created", "Number of Likes", "Tweets"])
# save to csv format
tweets_df.to_csv('10k_sambo.csv')
```
- Enter your keyword in "Q"
- Enter the date of the tweet in "since: " and "until: "
- Filter with "-filter "
- "10000" is number of twitter to scrape

### Result
![alt](https://i.imgur.com/EnCE4Sq.png#center)
