#### Analyzer:
Mapping is a schema definition
Create Mapping for "year" to be treated as date instead of text:



#### CRUD Operations:

C: Insert new element:
curl -XPUT https://localhost:9200/movies/_doc/109487?pretty -d '
{
"genre" : ["IMAX", "Sci-Fi"],
"title": "Interstellar foo",
"year" :2014
}'



R: Read a specific document data:
curl -XGET https://localhost:9200/movies/_doc/109487?pretty

Read all data under an index:
Curl -XGET https://localhost:9200/movies/_search?pretty

U: Update partial data:
 curl -XPOST https://localhost:9200/movies/_update/109487?pretty -d '
{
"doc":{
"title": "Interstellar"
}
}'


