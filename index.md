---
layout: default
---

# Overview

### Goals
My aim with this project was to use the NASA Image and Video Library to create visualizations to demonstrate the way language has been associated with images and videos over time. I wanted this project to encourage viewers to think about metadata and how we describe images.

### Process
1. I began with creating a data frame of the subjects I was interested in working with (keywords, titles, etc.).
2. I attempted to paginate through about 18 pages of search results- I later realized this did not work.
3. I created a few graphs and visualizations with the data from one page of search results (100 results total).

### Challenges
- Problems with pagination that I noticed too late.
- Unable to use matplotlib in the way I wanted, although I was able to figure it out somewhat, the graphs I was able to make with this data did not make very much sense.

## Making a Data Frame
```
import requests

key = {key}
query = 'climate change'
url = f'https://images-api.nasa.gov/search?q={query}'

r = requests.get(url)

r
parsed = r.json()
parsed.keys()
articles = parsed['collection']
items = articles['items']
items[0]['data']

titles = []
datesCreated = []
keywords = []
mediaTypes = []
descriptions = []
nasaIds = []
links = []

for i in items:
    title = (i['data'][0]['title'])
    titles.append(title)

for i in items:
    dateCreated = (i['data'][0]['date_created'])
    datesCreated.append(dateCreated)

for i in items:
    mediaType = (i['data'][0]['media_type'])
    mediaTypes.append(mediaType)

for i in items:
    description = (i['data'][0]['description'])
    descriptions.append(description)

for i in items:
    nasaId = (i['data'][0]['nasa_id'])
    nasaIds.append(nasaId)

for i in items:
    try:
        keyword = i['data'][0]['keywords']
        keywords.append(keyword)
    except:
        keyword = 'n/a'
        keywords.append(keyword)

for i in items:
    try:
        link = i['links']
        links.append(link)
    except:
        link = 'n/a'
        links.append(link)

print(len(titles), len(datesCreated), len(keywords), len(mediaTypes), len(descriptions), len(nasaIds), len(links))

import pandas as pd

df = pd.DataFrame({
    'title': titles,
    'date_created': datesCreated,
    'keywords': keywords,
    'media_type': mediaTypes,
    'description': descriptions,
    'nasa_id': nasaIds,
    'links': links
})
```

## Word Cloud

![WordCloud](https://github.com/ibobadil/nasa-image-descriptions/blob/main/nasa_wordcloud3.png)

```
import matplotlib.pyplot as plt
from wordcloud import WordCloud

text = keyword_text_plot

wordcloud = WordCloud(width=2500, height=2000, background_color='white', min_font_size=15).generate(text)

plt.figure(figsize=(15,10))
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.show()

wordcloud.to_file('nasa_wordcloud_square3.png')

from PIL import Image
import numpy as np
image = Image.open("circle.jpg")  # Load the image from a file
image

circle_mask = np.array(image)

import matplotlib.pyplot as plt
from wordcloud import WordCloud

text = keyword_text_plot

wordcloud = WordCloud(mask=circle_mask, width=2000, height=2000, background_color='white', min_font_size=2).generate(text)

plt.figure(figsize=(10,10))
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
plt.show()

wordcloud.to_file('nasa_wordcloud3.png')
```
### This is a work in progress!
### Thank you!