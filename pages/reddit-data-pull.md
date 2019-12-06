## Amtrak Ridership Visualization

**Overall Context**



**Project description:** This is a web scraper to download PDFs on Amtrak usage at stations across the U.S. from 2012-2018. Raw PDFs were downloaded at the station level and the state level (both csv’s included here). From there, the program will scrape the graph for the last 6 years of ridership from each PDF document. Some stations have discontinued services in the last 6 years, and the program will flag these stations. Final data is posted as data visuals.




### 1. Data Collection

Data was collected from railpassengers.org where similar fact sheets are available for all stations and states. In these fact sheets, there are graphs showing passenger arrivals and departures from 2012-2018. The jupyter notebooks in the data collection folder show the process for downloading all of the PDFs simultaneously and scraping the data from the PDFs using the Tabula package. The final products are the state and station level CSV files.


###     a. Find Links

Although we know generally where the fact sheets are, we

```python

# import libraries
%matplotlib inline
import numpy as np
import scipy as sp
import matplotlib as mpl
import matplotlib.cm as cm
import matplotlib.pyplot as plt
import pandas as pd
import time
pd.set_option('display.width', 500)
pd.set_option('display.max_columns', 100)
pd.set_option('display.notebook_repr_html', True)
import seaborn as sns
import html
from bs4 import BeautifulSoup
import requests

```

```python

```


### 2. Analysis

```python

```

This is the immage that is generated:
<img src="./../images/micromobility-word-cloud.png?raw=true"/>



#### b. N-bigrams

Word clouds offer some high-level information on the text, but they are more helpful for a very high-level first view. Another first step that is a bit more detailed is to create n-grams. These are words that show up next to each other. Two words together are bigrams, three words are trigrams, etc. The bigger the n-gram, generally the more processing power is necessary.

```python
import nltk
bigrams = nltk.collocations.BigramAssocMeasures()
trigrams = nltk.collocations.TrigramAssocMeasures()


bigramFinder = nltk.collocations.BigramCollocationFinder.from_words(token_list)
trigramFinder = nltk.collocations.TrigramCollocationFinder.from_words(token_list)

#bigrams
bigram_freq = bigramFinder.ngram_fd.items()
bigramFreqTable = pd.DataFrame(list(bigram_freq),
  columns=['bigram','freq']).sort_values(by='freq',
                                ascending=False)

#trigrams
trigram_freq = trigramFinder.ngram_fd.items()
trigramFreqTable = pd.DataFrame(list(trigram_freq),
        columns=['trigram','freq']).sort_values(by='freq',
                                        ascending=False)
```

Once we've created these functions, we can call on them to create our ngrams and make some tables showing the frequency that each n-gram appears in all of our articles.


```python

#function to filter for ADJ/NN bigrams
def rightTypes(ngram):
    if '-pron-' in ngram or 't' in ngram:
        return False
    for word in ngram:
        if word in stopwords or word.isspace():
            return False
    acceptable_types = ('JJ', 'JJR',
                        'JJS', 'NN',
                        'NNS', 'NNP',
                        'NNPS')

    second_type = ('NN', 'NNS',
                  'NNP', 'NNPS')
    tags = nltk.pos_tag(ngram)
    if tags[0][1] in acceptable_types and tags[1][1] in second_type:
        return True
    else:
        return False

#filter bigrams
filtered_bi = bigramFreqTable[bigramFreqTable.bigram.map(lambda x: rightTypes(x))]

#function to filter for trigrams
def rightTypesTri(ngram):
    if '-pron-' in ngram or 't' in ngram:
        return False
    for word in ngram:
        if word in stopwords or word.isspace():
            return False
    first_type = ('JJ', 'JJR',
                  'JJS', 'NN',
                  'NNS', 'NNP',
                  'NNPS')

    third_type = ('JJ', 'JJR',
                  'JJS', 'NN',
                  'NNS', 'NNP',
                  'NNPS')

    tags = nltk.pos_tag(ngram)
    if tags[0][1] in first_type and tags[2][1] in third_type:
        return True
    else:
        return False
#filter trigrams
filtered_tri = trigramFreqTable[trigramFreqTable.trigram.map(lambda x: rightTypesTri(x))]
```

Trigram Table:

| Trigram | # of Times Seen |
|-------|--------|---------|
| split, phase | 30 |
| crash rates | 21 |
| camden, nj | 14 |
| crash rate | 13 |
| red line | 13 |
| pbl installation | 12 |
| comfort, safety | 11 |
| transit feeder | 10 |
| linear regression | 9 |
| los angeles | 8 |
| auto lanes | 8 |
| higher turn | 7 |
| main effects | 7 |
| sample size | 7 |
| pogo sticks | 7 |
| united states | 7 |
| masoud, et | 6 |
| electric bikes | 6 |


Bigram Table:

| Bigram | # of Times Seen |
|-------|--------|---------|
| camden,, nj, — | 14 |
| metro, red, line | 7  |
| pbl, installation, table | 6  |
| appropriate, software, installed | 6  |
| lean, library, here | 6  |
| download, article, citation | 6  |
| masoud, et, al. | 5  |
| study, sample, size | 4  |
| split, phase, intersections | 4  |
| higher, turn, volume | 4  |
| crashes, per, bicyclist | 4  |
| international, municipal, lawyers | 4 |
| bicyclist, injury, crashes | 4 |
| split, phase, locations | 4 |
| energy,, green, building | 3 |
| building,, transportation,, waste | 3 |




### 3. Collect more data

#### A. Google News API

The Bigram and Trigrams give a little bit more information, but this definitely isn't sufficient to have an understanding of micromobility news happening in any given quarter. Now it is clear that we'll need collect more data. We'll do this by calling on the Google News API and trying to grab as many articles as we can -- the Google News API only allows information for the last 30 days, so we will want to grab as many articles as possible in this timeframe.


```python

from newsapi.newsapi_client import NewsApiClient
# Init
newsapi = NewsApiClient(api_key=api_key['App Key'].iloc[0])

from datetime import datetime, timedelta
from_time = datetime.strftime(datetime.now() - timedelta(31), '%Y-%m-%d')
to_time = datetime.strftime(datetime.now(), '%Y-%m-%d')

# Free plan only allows up to 100 articles taken at one time
from datetime import datetime, timedelta

title = []
url = []
author = []
publish_date = []
content = []

for num in range(1,30):

    from_time = datetime.strftime(datetime.now() - timedelta(num+1),
                                                  '%Y-%m-%d')
    to_time = datetime.strftime(datetime.now() - timedelta(num),
                                                  '%Y-%m-%d')

    for page_num in range(1,5):
        top_headlines = newsapi.get_everything(q='scooter',
                                           from_param=from_time,
                                          to=to_time,
                                           page=page_num,
                                              language='en')       
    for x in top_headlines['articles']:
        title.append(x['title'])
        url.append(x['url'])
        author.append(x['source']['id'])
        publish_date.append(x['publishedAt'])
        content.append(x['content'])

#make dataframe
df = pd.DataFrame({
    'Title':title,
    'URL':url,
    'Author':author,
    'Date Published':publish_date,
    'Content':content})

```

### 4. Next Steps: Machine Learning Classification

This Google News API allowed us to get 497 articles for the month of October. We will want to recreate our scraper from above and grab our contents again. However, rather than jumping into a WordCloud and N-gram tokens, we'll want to go a step further. For a subsection of these articles, I want to create classifications of the articles based on content area. From here, we can use these to create more precise NLP analyses that will allow us to look at new text being used in each specific area. For example, we'll want to know what terms are newly being used in safety articles compared to technology articles.

More to come on this front!