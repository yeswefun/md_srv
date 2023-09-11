



```
POST _analyze
{
  "tokenizer": "keyword",
  "char_filter": ["html_strip"],
  "text": "</p>I&apos;m so <b>happy</b>!</p>"
}


POST _analyze
{
  "tokenizer": "path_hierarchy",
  "text": "/one/two/three"
}


POST _analyze
{
  "text": "a Hello World",
  "tokenizer": "standard",
  "filter": [
    "stop",
    "lowercase",
    {
      "type": "ngram",
      "min_gram": 4,
      "max_gram": 4
    }
  ]
}


PUT test_index_1
{
  
}
```
