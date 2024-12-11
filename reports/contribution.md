# Contribution of Topic Modeling using News Articles on Coral Bleaching

## Summary of Findings

### High Level

The topics that were extracted using AI tools characterized how the scientific community, public, industry and government addresses the impact of climate change (and consequently coral bleaching events) on worldwide coral reefs. While an underlying theme of rising global tempeartures damaging global coral deposits is prevalent, the Guardian has published important stories on activities that compound and seek to offset (delay) this damage. Seven topics related to coral bleaching were identified in published articles over the last 5 years and six of these are directly related to the occurrence of or impact of coral bleaching events.

### How solution aids improves resilience, mitigates risks and aids recovery efforts

The solution developed here enhances the public's preparedness and response to occurrence of bleaching events at worldwide coral reefs.

This solution has notably identified groups of topics related to

1. ongoing global efforts to offset impact of bleaching events on coral reefs
2. obstacles that are being encountered when developing regulations to protect reefs from coral bleaching due to climate change

#### Improve Resilience

Readers who are members of the public and who are looking to understand how to maintain coral reef resilience to bleaching events brought about by climate change can read published articles within the topic about the *Impact of Declining Shark Population on Reefs* (topic 5). This topic sheds light on how the presence of apex predators such as sharks improves coral reefs' resilience to bleaching events.

Readers who are looking to understand efforts to protect the world's largest coral reef (Great Barrier Reef, GBR) from harm due to causes including coral bleaching by designating it as an in-danger heritage site can read articles within the *Scientific Recommendation for GBR as Heritage* topic (topic 1). Such a designation can allows GBR certain protections that proactively improve its resilience to bleaching events.

#### Mitigate Risks

Members of the public who are looking to get involved in reef protection initiatives can read published articles within the following topics

1. *Coral Reef Conservation Activities* (topic 0)
2. *Scientific Recommendations to Offset the Impact of Coral Bleaching* (topic 6)

in order to learn about successful practices that have been adopted worldwide to mitigate the risks from the occurrence of coral bleaching events.

Additionally, readers who are looking to understand

1. government resistence to efforts to prevent [coral bleaching events caused by wastewater (runoff)](https://oceanservice.noaa.gov/facts/coral_bleach.html)
   - can read articles within the *Agricultutal Opposition to GBR Water Protection Laws* topic (topic 4)
2. the risks and consequences of direct and harmful bleaching impact of climate change (rising temperatures) on coral reefs
   - can read articles within the *Global Impact of Record Temperatures on Reefs* topic (topic 3)

#### Aid Recovery Efforts

Members of the public who are looking to participate in or better understand recovery efforts after a coral bleaching event can read articles within the following topics

1. *Coral Reef Conservation Activities* (topic 0)
2. *Coral Reef Bleaching Event in GBR* (topic 2)

## Documentation

See text included in the following notebooks for methods and preparation processes that were used in this project.

1. [`02_get_guardian_article_urls.ipynb`](https://github.com/xlumzee/Temperature-and-Coral-Bleaching/blob/text-resources/notebooks/02_get_guardian_article_urls.ipynb)
   - use Guardian API to get links to published articles matching search term *coral bleaching event* in the *Environment* section
2. [`03_scrape_guardian_articles.ipynb`](https://github.com/xlumzee/Temperature-and-Coral-Bleaching/blob/text-resources/notebooks/03_scrape_guardian_articles.ipynb)
   - scrape text of relevant articles found in previous step
3. [`04_clean_guardian_articles.ipynb`](https://github.com/xlumzee/Temperature-and-Coral-Bleaching/blob/text-resources/notebooks/04_clean_guardian_articles.ipynb)
   - clean text of all scraped articles and combine into single file
4. [`05_topic_modeling.ipynb`](https://github.com/xlumzee/Temperature-and-Coral-Bleaching/blob/text-resources/notebooks/05_topic_modeling.ipynb)
   - perform topic modeling including logic to find optimal number of topics and model evaluation using coherence score

## Limitations

In this work, the analysis was performed but the dashboard was not constructed.
