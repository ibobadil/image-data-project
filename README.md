# nasa-image-data

## Examining Visuals of 'climate change' from the NASA Image and Video Library

### Project Description
  This project uses the [NASA Image and Video Library](https://images.nasa.gov/) API to collect data about the keywords associated with the images in this library. The query used to select images was 'climate change', as the goal is to examine what kinds of photos are associated with this term and what other metadata surrounds these items, such as dates, descriptions, titles, and other keywords. In addition to this metadata I also collected the NASA ID and links associated with each photo. This information was all brought together in a csv file. From there, this metadata will be used to create several graphs that illustrate the usage of different keywords over time, the quantitity of images over time, and what these images depict.

### Rationale Statement
I was initially interested in the language used to discuss climate and the environment, and began by focusing on headlines and keywords about these topics. Over time and through exploring the NASA Image and Video Library I ultimately thought it would be interesting to look at both the linguistic and visual associations with 'climate change'. The aim of this work is to consider how an organization presents information on a pressing topic through both language and imagery, and how that information has evolved over time. The NASA Image and Video Library is one example of an institution that has published information on climate change over many years, but this kind of observation could be applied to various institutions and their work.

### Workflow
1. I began by making a request to the API to get results related to 'climate change'.
2. I looped through the data and created lists of the information I wanted to include in this project.
3. I made a data frame out of these lists and saved it to a csv using the **pandas** library.
4. I used **OpenRefine** to help organize the data in a way that would be useful for making graphs and visualizations of the data. This process included using facets and text editing funtions to filter out information I did not need or that made the data unclear.
5. I used **matplotlib**, **Pillow**, **numpy**, and **wordcloud** to create a visualization in the form of a word cloud of the keywords in this data.
6. I used **matplotlib** and **numpy** to create the graphs using data from the csv (TO DO).

### Further Uses
In the future this code could be used to access metadata from the NASA Image and Video Library API, as I could not find this documentation online. This could include using similar loops to examine different search querys, keywords, and images on the website. This data could also be compared to the visual and written publications of other scientific institutions. Initially my focus had been on working with headlines or other kinds of text from various sources, it could be interesting to see how the NASA Library data compares to other discussions about climate change in its titles and keywords. Through working on this project, I gained a lot of interest in the images themselves and the visual component of this data. This data could possible be used to consider how language and metadata is ascribed to images, and how this influences what kind of results appear from different search queries. This applies to the NASA Image and Video Library, but could also be a part of a wider discussion about this topic.

### File list:
- finalproject.ipynb
- charts_final.ipynb
- finalproject_wordcloud.ipynb
- nasa_data.csv
- nasa_data_keywords.csv
- nasa_data_repeats.csv