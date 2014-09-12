elasticsearch-findings
======================

This is for documenting the lessons and knowledge gained out of using Elastic Search from real world projects

Findings
======================
1. About the indexing operation and real time GET and index refresh rate
http://elasticsearch-users.115913.n3.nabble.com/NRT-search-with-elastic-search-td3244655.html
https://github.com/elasticsearch/elasticsearch/issues/1060

The index is not updated asynchronously, when you index data its applied to the shard and the replicas in a sync manner including writing to a transaction log. A "fresh" view of the content to be searchable is opened every 1 second by default (thats NRT).

2. About the stored fields and _source document
That's exactly what elasticsearch does for you when a field is not stored (default) and the _source field is enabled (default too).
http://stackoverflow.com/questions/17103047/why-do-i-need-storeyes-in-elasticsearch

3. JetSlide Uses Elastic Search as Database
http://karussell.wordpress.com/2011/07/13/jetslide-uses-elasticsearch-as-database/

Videos
======================
1. Distributed Diagram
http://www.elasticsearch.org/videos/distributed-diagram/

APIs & Endpoints
=====================
1. View the current settings for all indexes
curl -XGET 'localhost:9200/_settings?pretty=true'
