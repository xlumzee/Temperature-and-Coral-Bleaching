# Coral Bleaching and Climate Change

## About

### Title

Identifying Topics of the Guardian's News Articles on Coral Bleaching

### Direction

Assess the aspects of news reporting on occurrences of, consequences of and policy related to coral bleaching events triggered by climate change.

### Description

Create a dashboard to list published articles within all identified topics. Articles can be read by members of the public to better understand the damage caused by coral bleaching. The project will identify types of activities being adopted to protect coral reefs from major bleaching events.

### Objective

Use AI tools to understand the topics of the published news articles related to coral bleaching.

### Analysis

Topic modeling was performed using articles published by the Guardian online related to coral bleaching events.

### Who benefits

Our proposed end-user is a member of the public who has an interest in learning about (a) how climate change damages worldwide coral deposits or (b) activities being deployed to protect coral reefs from damage caused by bleaching events.

Specifically, the revealed topics in our AI-based solution are beneficial to members of public who are looking to read published news articles in order understand how to

1. contribute to recovery efforts to preserve this natural resource (coral reefs)
2. understand factors involved in implementing governmental reforms to counter the impact of coral bleaching brought on by climate change

### Core Features

1. Analysis of text in published articles to learn topics using Non-negative Matrix Factorization (NMF)
2. Data visualizations to illustrate attributes of topics of news articles that are related to coral bleaching

### Deliverable

Dashboard that displays top 10 articles and top 10 terms per topic. The user selects their topic of interest and they are presented with a list of the top 10 articles for further reading

The top 10 articles are selected as those with the 10 smallest NMF residuals, between the training and reconstructed data using the fitted NMF, model per topic. For technical detail regarding residual, see the `reconstruction_err_` attribute from [here](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.NMF.html).

## Notes About Data Privacy

1. All news article texts were retrieved by web-scraping and storing the scraped texts in a `.parquet` file. All `.parquet` files with raw article texts are stored locally and were deleted on November 30, 2024.
2. Raw or processed text outputs are not shown here.

## Findings and Contribution

See [here](https://github.com/xlumzee/Temperature-and-Coral-Bleaching/blob/text-resources/reports/contribution.md).
