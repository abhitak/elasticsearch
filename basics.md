#### Analyzer:
Three things that analyzer can do:
- Charatcter Filters : Remove HTML encoding, convert '&' to 'and'
- Tokenizer: Split strings on whitespace/punctuation/ non-letters
- Token Filter: Lowercasing, stemming(Stemming is the process of reducing a word to its stem that affixes to suffixes and prefixes or to the roots), synonyms, stopwords.

  ![image](https://github.com/abhitak/elasticsearch/assets/46652509/cfd4f15f-1da4-467c-b828-066192947076)

**Mapping** is a schema definition.

Create Mapping for "year" to be treated as date instead of text:
curl -XPUT https://localhost:9200/movies -d '
{
 "movies": {
   "properties": {
     "year": {"type": "date"}
   }
}'

Common Mappings:
 - Field types : int, string, byte, short, integer, long, float, double, boolean, date
   e.g.
   "properties": {
     "user_id": {
       "type": "long"
     }
   }
 - Field Index: do you want this field to be indexed for full-text search? analized/not_analyzed/ no
   e.g.
   "properties": {
     "genre": {
       "index": "not_analyzed"
     }
   }
 - Field Analyzer: Define your tokenizer and token filter.
   standard(split on word boundaries)/whitespace/simple(split on anything that isn't a letter and lowercases)/emglish(language) etc.
   e.g.
     "properties": {
     "description": {
       "analyzer": "english"
     }
   }

#### CRUD Operations:

**C:** Insert new element:
curl -XPUT https://localhost:9200/movies/_doc/109487?pretty -d '

{
"genre" : ["IMAX", "Sci-Fi"],
"title": "Interstellar foo",
"year" :2014
}'



**R:** Read a specific document data:
curl -XGET https://localhost:9200/movies/_doc/109487?pretty

Read all data under an index:
Curl -XGET https://localhost:9200/movies/_search?pretty

**U:** Update partial data:
curl -XPOST https://localhost:9200/movies/_update/109487?pretty -d '

{
"doc":{
"title": "Interstellar"
}
}'


