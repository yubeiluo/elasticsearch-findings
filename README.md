elasticsearch-findings
======================

This is for documenting the lessons and knowledge gained out of using Elastic Search from real world projects

Findings
======================

- About the indexing operation and real time GET and index refresh rate
  - The index is not updated asynchronously, when you index data its applied to the shard and the replicas in a sync manner including writing to a transaction log. A "fresh" view of the content to be searchable is opened every 1 second by default (thats NRT).
  - [NRT-search-with-elastic-search][1]
  - [Realtime GET #1060][2]
  
- About the stored fields and _source document
  - That's exactly what elasticsearch does for you when a field is not stored (default) and the _source field is enabled (default too). 
  - [why-do-i-need-storeyes-in-elasticsearch][3] 

- JetSlide Uses Elastic Search as Database
  - [jetslide-uses-elasticsearch-as-database][4]

- When and why to use routing in ES for indexing/searching?
  - [Over-allocation of shards][5]
  - [When-Why-to-use-Routing-for-indexing-searching][6]
  - [some-ES-stats-at-yfrog-com][7]

- Index alias use cases
  - [I'm loving ElasticSearch index alias feature][8]

- Aggregations
  - [elasticsearch-aggregations](http://blog.qbox.io/elasticsearch-aggregations)
- Null Values
  - [null value mapping in ElasticSearch](http://stackoverflow.com/questions/22796103/null-value-mapping-in-elasticsearch)

Geo Spatial Search
======
1. [Spatial Search ElasticSearch tutorial](http://www.elasticsearchtutorial.com/spatial-search-tutorial.html)
2. [Using Elastic Search for geo-spatial search](http://www.jillesvangurp.com/2013/03/20/using-elastic-search-for-geo-spatial-search/)

Videos
======================
- Distributed Diagram
  - [distributed-diagram][9]

APIs & Endpoints
=====================
- View the current settings for all indexes
curl -XGET 'localhost:9200/_settings?pretty=true'

SysAdmins
=====================
- How to create backup of Elastic Search using rsync?
  - [how-to-backup-elasticsearch-with-rsync][10]
- How to leverage index aliases when making changes to indexes like configuration changes without any production glitches?
  - [indices-aliases][11]
  - [the-use-of-aliases-in-elasticsearch][12]
- How to provision ES in a cost effective manner?
  - [qbox.io][13]
- [is-there-a-smarter-way-to-reindex-elasticsearch](http://stackoverflow.com/questions/13851044/is-there-a-smarter-way-to-reindex-elasticsearch)
- [re-index](http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/reindex.html)
- [changing mapping with zero downtime](http://www.elasticsearch.org/blog/changing-mapping-with-zero-downtime/)
- [elasticsearch-curls](http://davektech.wordpress.com/2014/10/17/elasticsearch-curls-2/)
- [A full feature elasticsearch reindex tool](https://github.com/garbin/elasticsearch-reindex)
- [Reindexing Content in Elasticsearch](http://blog.florian-hopf.de/2013/11/reindexing-content-in-elasticsearch.html)
[1]: http://elasticsearch-users.115913.n3.nabble.com/NRT-search-with-elastic-search-td3244655.html
[2]: https://github.com/elasticsearch/elasticsearch/issues/1060
[3]: http://stackoverflow.com/questions/17103047/why-do-i-need-storeyes-in-elasticsearch
[4]: http://karussell.wordpress.com/2011/07/13/jetslide-uses-elasticsearch-as-database/
[5]: https://groups.google.com/forum/?fromgroups#!searchin/elasticsearch/data$20flow/elasticsearch/49q-_AgQCp8/MRol0t9asEcJ
[6]: http://elasticsearch-users.115913.n3.nabble.com/When-Why-to-use-Routing-for-indexing-searching-td3789570.html
[7]: http://elasticsearch-users.115913.n3.nabble.com/some-ES-stats-at-yfrog-com-td3759891.html
[8]: https://twitter.com/otisg/status/160128277497913345
[9]: http://www.elasticsearch.org/videos/distributed-diagram/
[10]: http://karussell.wordpress.com/2011/07/10/how-to-backup-elasticsearch-with-rsync/
[11]: http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/indices-aliases.html
[12]: http://paulsabou.com/blog/2012/04/15/the-use-of-aliases-in-elasticsearch/
[13]: http://qbox.io/
