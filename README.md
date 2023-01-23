# Dataset for the paper: "Monant Medical Misinformation Dataset: Mapping Articles to Fact-Checked Claims"


## Overview

This dataset of medical misinformation was collected and is published by <a href="https://kinit.sk/">Kempelen Institute of Intelligent Technologies (KInIT)</a>. It consists of approx. 317k news articles and blog posts on medical topics published between January 1, 1998 and February 1, 2022 from a total of 207 reliable and unreliable sources.  The dataset contains full-texts of the articles, their original source URL and other extracted metadata. If a source has a credibility score available (e.g., from Media Bias/Fact Check), it is also included in the form of annotation. Besides the articles, the dataset contains around 3.5k fact-checks and extracted verified medical claims with their unified veracity ratings published by fact-checking organisations such as Snopes or FullFact. Lastly and most importantly, the dataset contains 573 manually and more than 51k automatically labelled mappings between previously verified claims and the articles; mappings consist of two values: claim presence (i.e., whether a claim is contained in the given article) and article stance (i.e., whether the given article supports or rejects the claim or provides both sides of the argument).

The dataset is primarily intended to be used as a training and evaluation set for machine learning methods for claim presence detection and article stance classification, but it enables a range of other misinformation related tasks, such as misinformation characterisation or analyses of misinformation spreading.

Its novelty and our main contributions lie in (1) focus on medical news article and blog posts as opposed to social media posts or political discussions; (2) providing multiple modalities (beside full-texts of the articles, there are also images and videos), thus enabling research of multimodal approaches; (3) mapping of the articles to the fact-checked claims (with manual as well as predicted labels); (4) providing source credibility labels for 95% of all articles and other potential sources of weak labels that can be mined from the articles' content and metadata.

The dataset is associated with the research paper <a href="https://dl.acm.org/doi/10.1145/3477495.3531726?cid=81474695895">"Monant Medical Misinformation Dataset: Mapping Articles to Fact-Checked Claims"</a> accepted and presented at ACM SIGIR Conference on Research and Development in Information Retrieval (SIGIR '22). 

This repository provides a small static sample of the dataset and the dataset's descriptive analysis in a form of Jupyter notebooks.



## Options to access the dataset

There are two ways how to get access to the dataset:

1. Static dump of the dataset available in the CSV format
2. Continuously updated dataset available via REST API

In order to obtain an access to the dataset (either to full static dump or REST API), please, request the access <a href="https://doi.org/10.5281/zenodo.5996864">via Zenodo portal</a>.

Dataset can be shared and used under the following conditions:

- You will use dataset (including this sample) strictly only for research purposes. The request for access to the dataset must be sent from the official and existing e-mail address of the relevant university, faculty or other scientific or research institution (for verification purposes).
- You will not re-share the dataset obtained from Zenodo portal with anyone else not included in your request.
- You will appropriately cite the papers mentioned in the dataset description in any publication, project, tool using this dataset.
- You understand how the dataset was created and that the manual or automatically predicted annotations may not be 100% correct. 
- You acknowledge that you are fully responsible for the use of the dataset (data) and for any infringement of rights of third parties (in particular copyright) that may arise from its use beyond the intended purposes. Neither the authors nor Kempelen Institute of Intelligent Technologies (KInIT) are responsible for your actions.

If you require also access to REST API, please, state it explicitly in your access request at Zenodo and elaborate in details how do you intend to use the REST API access (please, note that using the static dump is a preferable option due to performance reasons).



## References

If you use this dataset in any publication, project, tool or in any other form, please, cite the following papers:

```
@inproceedings{SrbaMonantPlatform,
   author = {Srba, Ivan and Moro, Robert and Simko, Jakub and Sevcech, Jakub and Chuda, Daniela and Navrat, Pavol and Bielikova, Maria},
   booktitle = {Proceedings of Workshop on Reducing Online Misinformation Exposure (ROME 2019)},
   pages = {1--7},
   title = {Monant: Universal and Extensible Platform for Monitoring, Detection and Mitigation of Antisocial Behavior},
   year = {2019}
}

@inproceedings{SrbaMonantMedicalDataset,
   author = {Srba, Ivan and Pecher, Branislav and Tomlein Matus and Moro, Robert and Stefancova, Elena and Simko, Jakub and Bielikova, Maria},
   booktitle = {Proceedings of the 45th International ACM SIGIR Conference on Research and Development in Information Retrieval (SIGIR '22)},
   numpages = {11},
   title = {Monant Medical Misinformation Dataset: Mapping Articles to Fact-Checked Claims},
   year = {2022},
   doi = {10.1145/3477495.3531726},
   publisher = {Association for Computing Machinery},
   address = {New York, NY, USA},
   url = {https://doi.org/10.1145/3477495.3531726},
}
```


## Dataset creation process

In order to create this dataset (and to continuously obtain new data), we used our research platform <a href="https://rome2019.github.io/papers/Srba_etal_ROME2019.pdf">Monant</a>. The Monant platform provides so called data providers to extract news articles/blogs from news/blog sites as well as fact-checking articles from fact-checking sites. General parsers (from RSS feeds, Wordpress sites, Google Fact Check Tool, etc.) as well as custom crawler and parsers were implemented (e.g., for fact checking site Snopes.com). All data is stored in the unified format in a central data storage.
 
   
   
## Ethical considerations

The dataset was collected and is published for research purposes only. We collected only publicly available content of news/blog articles. The dataset contains identities of authors of the articles if they were stated in the original source; we left this information, since the presence of an author's name can be a strong credibility indicator. However, we anonymised the identities of the authors of discussion posts included in the dataset. 

The main identified ethical issue related to the presented dataset lies in the risk of mislabelling of an article as supporting a false fact-checked claim and, to a lesser extent, in mislabelling an article as not containing a false claim or not supporting it when it actually does. To minimise these risks, we developed a labelling methodology and require an agreement of at least two independent annotators to assign a claim presence or article stance label to an article. It is also worth noting that we do not label an article as a whole as false or true. Nevertheless, we provide partial article-claim pair veracities based on the combination of claim presence and article stance labels.

As to the veracity labels of the fact-checked claims and the credibility (reliability) labels of the articles' sources, we take these from the fact-checking sites and external listings such as Media Bias/Fact Check as they are and refer to their methodologies for more details on how they were established.

Lastly, the dataset also contains automatically predicted labels of claim presence and article stance using our baselines described in the next section. These methods have their limitations and work with certain accuracy as reported in this paper. This should be taken into account when interpreting them. 
   
   
## Reporting mistakes in the dataset
   
The mean to report considerable mistakes in raw collected data or in manual annotations is by creating a new issue in this repository. Alternately, general enquiries or requests can be sent at info [at] kinit.sk.
   
   
## Dataset structure

### Raw data

At first, the dataset contains so called raw data (i.e., data extracted by the Web monitoring module of Monant platform and stored in exactly the same form as they appear at the original websites). Raw data consist of articles from news sites and blogs (e.g. naturalnews.com), discussions attached to such articles, fact-checking articles from fact-checking portals (e.g. snopes.com). In addition, the dataset contains feedback (number of likes, shares, comments) provided by users on social network Facebook which is regularly extracted for all news/blogs articles.

Raw data are contained in these CSV files (and corresponding REST API endpoints):

- sources.csv
- articles.csv
- article_media.csv
- article_authors.csv
- discussion_posts.csv
- discussion_post_authors.csv
- fact_checking_articles.csv
- fact_checking_article_media.csv
- claims.csv
- feedback_facebook.csv

_Note: Personal information about discussion posts' authors (name, website, gravatar) are anonymised._


### Annotations

Secondly, the dataset contains so called annotations. Entity annotations describe the individual raw data entities (e.g., article, source). Relation annotations describe relation between two of such entities.

Each annotation is described by the following attributes:

1) category of annotation (`annotation_category`). Possible values: label (annotation corresponds to ground truth, determined by human experts) and prediction (annotation was created by means of AI method).
2) type of annotation (`annotation_type_id`). Example values: Source reliability (binary), Claim presence. The list of possible values can be obtained from enumeration in annotation_types.csv.
3) method which created annotation (`method_id`). Example values: Expert-based source reliability evaluation, Fact-checking article to claim transformation method. The list of possible values can be obtained from enumeration methods.csv.
4) its value (`value`). The value is stored in JSON format and its structure differs according to particular annotation type.


At the same time, annotations are associated with a particular object identified by:

1) entity type (parameter `entity_type` in case of entity annotations, or `source_entity_type` and `target_entity_type` in case of relation annotations). Possible values: sources, articles, fact-checking-articles.
2) entity id (parameter `entity_id` in case of entity annotations, or `source_entity_id` and `target_entity_id` in case of relation annotations).


The dataset provides specifically these entity annotations:

- Source reliability (binary). Determines validity of source (website) at a binary scale with two options: reliable source and unreliable source.
- Article veracity. Aggregated information about veracity from article-claim pairs.

The dataset provides specifically these relation annotations:

- Fact-checking article to claim mapping. Determines mapping between fact-checking article and claim.
- Claim presence. Determines presence of claim in article.
- Claim stance. Determines stance of an article to a claim. 


Annotations are contained in these CSV files (and corresponding REST API endpoints):

- entity_annotations.csv
- relation_annotations.csv

_Note: Identification of human annotators authors (email provided in the annotation app) is anonymised._

### Enumerations

Finally, the dataset provides additional CSV files with enumerations:

- media_types.csv
- source_types.csv
- annotation_types.csv
- methods.csv




## Jupyter notebooks with descriptive analyses

Descriptive analyses of the dataset are done by means of two Jupyter notebook. Notebooks analyze the same attributes of the dataset, nevertheless one works with the static CSV dump and second works with REST API. In this way, the notebooks illustrate how the dataset can be processed.


In order to work with these notebook:
- Install python libraries (utilization of the attached `requirements.txt` is possible):
   -  re
   -  json
   -  requests
   -  pandas
   -  numpy
   -  matplotlib
- Install <a href="https://jupyter.org/install">Jupyter Notebook</a>
- Run <a href="https://jupyter.readthedocs.io/en/latest/running.html#running">Jupyter Notebook</a>


_Note: In order to make the descriptive analysis replicable, REST API version of the Jupyter notebook uses a "freeze time" set to February 1, 2022. As a result, only those data that were present in the Monant platform up to this date are considered._