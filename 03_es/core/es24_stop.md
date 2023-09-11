

```
POST _analyze
{
  "analyzer": "stop",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}


成功
{
  "tokens": [
    {
      "token": "quick",
      "start_offset": 6,
      "end_offset": 11,
      "type": "word",
      "position": 1
    },
    {
      "token": "brown",
      "start_offset": 12,
      "end_offset": 17,
      "type": "word",
      "position": 2
    },
    {
      "token": "foxes",
      "start_offset": 18,
      "end_offset": 23,
      "type": "word",
      "position": 3
    },
    {
      "token": "jumped",
      "start_offset": 24,
      "end_offset": 30,
      "type": "word",
      "position": 4
    },
    {
      "token": "over",
      "start_offset": 31,
      "end_offset": 35,
      "type": "word",
      "position": 5
    },
    {
      "token": "lazy",
      "start_offset": 40,
      "end_offset": 44,
      "type": "word",
      "position": 7
    },
    {
      "token": "dog",
      "start_offset": 45,
      "end_offset": 48,
      "type": "word",
      "position": 8
    },
    {
      "token": "s",
      "start_offset": 49,
      "end_offset": 50,
      "type": "word",
      "position": 9
    },
    {
      "token": "bone",
      "start_offset": 51,
      "end_offset": 55,
      "type": "word",
      "position": 10
    }
  ]
}
```
