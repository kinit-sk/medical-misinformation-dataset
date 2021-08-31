# Medical Misinformation Dataset

In order to create a medical misinformation dataset of news articles/blogs and claims debunked by means of fact-checking articles (and to continuously obtain new data), we used our research platform MonAnt [1]. The MonAnt platform provides so called data providers to extract news articles/blogs from news/blog sites as well as fact-checking articles from fact-checking sites. General parsers (from RSS feeds, Wordpress sites, Google Fact Check Tool, etc.) as well as custom crawler and parsers were implemented (e.g., for fact checking site Snopes.com). All data is stored in the unified format in a central data storage.
 
The content of this directory consists of the dataset's descriptive analysis in a form of Jupyter notebook. In order to make the analysis replicable, it uses a "freeze time" set to August 4, 2021. As a result, only those data that were present in the MonAnt platform up to this date are considered.

Currently, the access to dataset can be provided by sending a request to ivan.srba@kinit.sk.

In order to work with this notebook (e.g. changing the freeze timestamp):
- Install python libraries:
   -  re
   -  json
   -  requests
   -  pandas
   -  numpy
   -  matplotlib
- Install jupyter software e.g. <a href="https://jupyter.org/install">Jupyter Notebook</a>
- Run Jupyter software (e.g. <a href="https://jupyter.readthedocs.io/en/latest/running.html#running">Jupyter Notebook</a>

Documentation:
- <a href="https://kinit.sk/research/medical-misinformation-dataset">the guide providing instructions how to read/write data from Monant platform</a>
- <a href="https://api.monant.kinit.sk/apidocs">API documentation</a>

<i>[1] SRBA, Ivan, et al. Monant: universal and extensible platform for monitoring, detection and mitigation of antisocial behaviour. In: Workshop on Reducing Online Misinformation Exposure–ROME. 2019.</i>
