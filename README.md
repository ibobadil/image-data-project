# nasa-image-data

## Examining Visuals of 'climate change' from the NASA Image and Video Library

### Project Description
  This project uses the [NASA Image and Video Library](https://images.nasa.gov/) API to collect data about the keywords associated with the images in this library. The query used to select images was 'climate change', as the goal is to examine what kinds of photos are associated with this term and what other metadata surrounds these items, such as dates, descriptions, titles, and keywords. In addition to this metadata I also collected the NASA ID and links associated with each photo. This information was all brought together in a csv file. From there, this metadata will be used to create several graphs that illustrate the usage of different keywords, how these words are related to one another, and how they are related to the images and videos they describe.

### Rationale Statement
  I was initially interested in the language used to discuss climate and the environment, and began by focusing on headlines and keywords about these topics. Over time and through exploring the NASA Image and Video Library I ultimately thought it would be interesting to look at both the linguistic and visual associations with 'climate change'. The aim of this work is to consider how an organization presents information on a pressing topic through both language and imagery, and how that information has evolved over time. The NASA Image and Video Library is one example of an institution that has published information on climate change over many years, but this kind of observation could be applied to various institutions and their work.

### Workflow
1. I began by making a request to the API to get results related to 'climate change'.
2. I looped through the results and made a data frame including the information I was interested in analyzing. I saved this data frame to a csv using the **pandas** library.
4. I used **OpenRefine** to help organize the data in a way that would be useful for making graphs and visualizations of the data. This process included using facets and text editing funtions to filter out information I did not need or that made the data unclear.
5. I made a few simple bar charts in python to depict the data. I also tried to use **seaborn** to create some of these graphs.
6. I used **matplotlib**, **Pillow**, **numpy**, and **wordcloud** to create visualizations of the keywords, titles, and descriptions in this data in the form of word clouds.
7. I used **matplotlib** and **networkx** to create text networks describing keywords, titles, and NASA IDs using data from the csv.

### Further Uses
  In the future this code could be used to access metadata from the NASA Image and Video Library API, as I could not find this documentation online. This could include using similar loops to examine different search querys, keywords, and images on the website. This data could also be compared to the visual and written publications of other scientific institutions. Initially my focus had been on working with headlines or other kinds of text from various sources, it could be interesting to see how the NASA Library data compares to other discussions about climate change in its titles and keywords. Through working on this project, I gained a lot of interest in the images themselves and the visual component of this data. I hope to continue working with this data could be used to consider how language and metadata is ascribed to images, and how this influences what kind of results appear from different search queries.

### File list:
- charts_final.ipynb
- description_wordcloud.png
- finalproject.ipynb
- finalproject_visualizations.ipynb
- finalproject_wordcloud.ipynb
- keywords_chart.png
- keywords_display.png
- keywords_titles_display.png
- media_type_chart.png
- nasa_data.csv
- nasa_data_keywords.csv
- nasa_data_repeats.csv
- nasa_data_wordcloud3.png
- text_network.csv
- titles_chart.png
- titles_wordcloud.png