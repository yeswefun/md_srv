

```
POST _analyze
{
  "analyzer": "keyword",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}


成功
{
  "tokens": [
    {
      "token": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone",
      "start_offset": 0,
      "end_offset": 55,
      "type": "word",
      "position": 0
    }
  ]
}
```
