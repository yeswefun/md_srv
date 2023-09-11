


```
POST _analyze
{
  "analyzer": "pattern",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}


成功
{
  "tokens": [
    {
      "token": "the",
      "start_offset": 0,
      "end_offset": 3,
      "type": "word",
      "position": 0
    },
    {
      "token": "2",
      "start_offset": 4,
      "end_offset": 5,
      "type": "word",
      "position": 1
    },
    {
      "token": "quick",
      "start_offset": 6,
      "end_offset": 11,
      "type": "word",
      "position": 2
    },
    {
      "token": "brown",
      "start_offset": 12,
      "end_offset": 17,
      "type": "word",
      "position": 3
    },
    {
      "token": "foxes",
      "start_offset": 18,
      "end_offset": 23,
      "type": "word",
      "position": 4
    },
    {
      "token": "jumped",
      "start_offset": 24,
      "end_offset": 30,
      "type": "word",
      "position": 5
    },
    {
      "token": "over",
      "start_offset": 31,
      "end_offset": 35,
      "type": "word",
      "position": 6
    },
    {
      "token": "the",
      "start_offset": 36,
      "end_offset": 39,
      "type": "word",
      "position": 7
    },
    {
      "token": "lazy",
      "start_offset": 40,
      "end_offset": 44,
      "type": "word",
      "position": 8
    },
    {
      "token": "dog",
      "start_offset": 45,
      "end_offset": 48,
      "type": "word",
      "position": 9
    },
    {
      "token": "s",
      "start_offset": 49,
      "end_offset": 50,
      "type": "word",
      "position": 10
    },
    {
      "token": "bone",
      "start_offset": 51,
      "end_offset": 55,
      "type": "word",
      "position": 11
    }
  ]
}
```
