# Natural Language Processing



## NLP Engine

Creating a Search Engine and NLP recommendation System

How to Being with searching and what topics to lookup

* Predictive Search algorithm 
* Perplexity/Word Error Rate Metrics for Model Evaluation  
* Realtime user Suggestion ?  
* Preprocessing of Corpus to make auto complete
* How to make search engine using logstash and Elasticseach \(ELK stack\)
* predict next word in a sentence from given text 

#### Cloud API choice

* Algolia Seach API  
* Azure Cognitive Search
* AWS Cloud Search
* Google cloud search
* AWS Kendra 

**Popular Frameworks**

* Elasticsearch  
* Solr

| Solr | ElasticSearch |
| :--- | :--- |
| Solr is distributed full-text distributed search, high availability, powerful query DSL, multitenancy, Geo Search, and horizontal scaling | Elasticsearch is completely based on JSON and is suitable for time series and NoSQL data. |
| Solr needs at least 512MB of HEAP memory to allocate to instances | Elasticsearch is easy to install and configure, but it’s quite a bit heavier than Solr. |
| Solr supports XML-based configuration files | Configuration files in Elasticsearch are written in YML format |
| Solr uses request handlers to ingest data from XML files, CSV files, databases, Microsoft Word documents, and PDFs. With native support for the [Apache Tika](https://tika.apache.org/) library, it supports extraction and indexing from over one thousand file types. Solr ships with a simple command line post. To ingest CSV-based data in a collection named `testcollection` | Elasticsearch, on the other hand, is completely JSON-based. It supports data ingestion from multiple sources using the Beats family |
| While both products are document-oriented search engines, Solr has always been more focused on enterprise-directed text searches with advanced information retrieval.Consequently, it’s more suited for search applications that use massive amounts of static dataAdditionally, Solr stands out in handling Rich Text Format \(RTF\) documents. To compete with Elasticsearch, recent Solr releases have offered new features such as Parallel SQL Interface and streaming expression | Elasticsearch is focused more on scaling, data analytics, and processing time series data to obtain meaningful insights and patterns. Its large-scale log analytics performance makes it quite popular. Elasticsearch is more suited to modern web applications where data is carried in and out in JSON format. Elasticsearch has also put a lot of development effort into making its tool more resilient. This turns it into a primary data store. |
| Both Solr and Elasticsearch support NRT \(near real-time\) searches and take advantage of all of Lucene’s search capabilities |  |
| Solr includes a sample search UI, called Velocity Search, that offers powerful features such as searching, faceting, highlighting, autocomplete, and Geo Search | Elasticsearch’s DSL is native. The aggregation framework in [Elasticsearch is powerful with aggregation queries](https://logz.io/blog/elasticsearch-queries/) in the APIs with better caching. The more recent releases of the tool offer better management of memory footprints. |
| Solr now supports a schemaless mode. | Because Elasticsearch is schemaless, it is easy to index unstructured data and dynamic fields without defining the schema of the index in advance. |
| Both Elasticsearch and SolrCloud provide support for sharding. But, since Elasticsearch’s design has horizontal scaling in mind, it has better support for scaling and cluster management. Its disadvantage is that the shards cannot increase once they’ve been created, although you can use a shrink API to reduce the shards of an index. SolrCloud supports further splitting of an existing shard but not the shrinking of shards |  |

**Choice of Databases**

* Reddis : in memory dictionary
* HBase : coulmn pair \(dictioary  with list as value and list index as columns\) , CQL  , Time series data , like watch history
* Mongo DB : document database , not suitable for disconnected but related and updated often , suitable for reads
* Relataionl Database  : Mysql
* Graph Based  : Neo4j \(best for knowledge graph\) \(recommendation Engine\)
* Search Engines  : Meili Search, Elastisearch  \(Index based Searching\) + algo+ .... \#\#" Typeahead search "
* MultiModel Database : ex Fauna DB  , combo of all db

