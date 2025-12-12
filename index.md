---
layout: default
---

# Overview

### Goals
My aim with this project was to use the NASA Image and Video Library to create visualizations to demonstrate the way language has been associated with images and videos over time. I wanted this project to encourage viewers to think about metadata and how we describe images.

### Process
1. I began with creating a data frame of the subjects I was interested in working with (keywords, titles, etc.).
2. I attempted to paginate through about 18 pages of search results- I later realized this did not work.
3. I used **OpenRefine** to organize the data and remove unecessary punctuation and text. I returned to OpenRefine frequently throughout this process to create various graphs.
4. I created a few graphs and visualizations with the data from one page of search results (100 results total). I began by trying to make various bar charts, byt these did not work well with my data frame or in demonstrating how words were related to each other.
5. I learned how to make word clouds, which guided my the visualizations I chose to make moving forward.
6. I attempted to create a text network graph with **networkx**, it was successful but very messy, so I returned to working with the data.
7. I created a new data frame that separated all of the keywords.
8. I used this to create multiple text networks that displayed relationships between keywords, titles, and NASA IDs.

### Challenges
- Unable to paginate through the results.
- Because I could not get thorough data on the dates created for each image/video, it did not seem like I could create graphs that demonstrated anything accurate about the quantity of images/videos posted over time.
- It took a while to figure out what graphs I could create interesting visualizations with using this data.
- Had issues achieving some of the things I had hoped to do (connecting keywords or IDs to links to the photos, creating a hover feature over the text network graphs so that the text would be less cluttered, creating bar graphs that depicted the data in an interesting way)

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
## Bar Graphs
I created a few simple bar graphs that depict the counts of some of the data.

![Bar chart of the frequency of creation dates](images/dates_chart.png) ![Bar chart of the media types](images/media_type_chart.png)

![Bar chart of the most frequent titles](images/titles_chart.png) ![Bar chart of the most frequently appearing keywords](images/keywords_chart.png)

## Word Clouds
I learned how to create word clouds. This was a fun step in this process. It helped me better understand the data I was working with and some more direction on what I could create with it.

### Word cloud based on keywords
![Text from keywords](images/nasa_wordcloud3.png)

### Word cloud based on titles
![Text from titles](images/titles_wordcloud.png)

### Word cloud based on descriptions
![Text from descriptions](images/description_wordcloud.png)


## Text Networks
I ultimately decided to create text networks visualizations as a way to depict the connections between the many keywords in this data frame. This was another fun step that took some trial and error, and that gave me some practice with different libraries in python including...

### Text network connecting keywords and NASA IDs (displaying keywords)

![Text network displaying keywords](images/keywords_display.png)

### Text network connecting keywords and titles

![Text network displaying keywords and titles](images/keywords_titles_display.png)

---

## Further steps
- Improving the text network visualizations.
- Continue to work on adding links and hover features.
- Create more detailed bar graphs to display the data.
- Paginate through more pages to create more extensive data frames and create interesting graphs based on dates.

## Thank you!