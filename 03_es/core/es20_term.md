


分词 : analysis

分词器 : analyzer
    Character Filters
        去掉 html标签 或 其它特殊字符

    Tokenizer
        按照一定规则切分单词

    Token Filters
        英文字母转小写
        同义词，近义词

analyze api
    可以指定以下内容进行测试
        analyzer
        索引中的字段
        自定义分词器


```

POST _analyze
{
  "analyzer": "standard",
  "text": "hello world"
}


POST test_index/_analyze
{
  "field": "username",
  "text": "hello world"
}


POST _analyze
{
  "tokenizer": "standard",
  "text": "Hello World!"
}


POST _analyze
{
  "tokenizer": "standard",
  "filter": ["lowercase"],
  "text": "Hello World!"
}


POST _analyze
{
  "analyzer": "standard",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}


POST _analyze
{
  "analyzer": "simple",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}

POST _analyze
{
  "analyzer": "whitespace",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}

POST _analyze
{
  "analyzer": "stop",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}


POST _analyze
{
  "analyzer": "keyword",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}

POST _analyze
{
  "analyzer": "pattern",
  "text": "The 2 QUICK Brown-Foxes jumped over the lazy dog's bone"
}
```







```
# 指定 analyzer 进行测试
        
POST _analyze
{
  "analyzer": "standard",
  "text": "hello world"
}

成功
{
  "tokens": [
    {
      "token": "hello",
      "start_offset": 0,
      "end_offset": 5,
      "type": "<ALPHANUM>",
      "position": 0
    },
    {
      "token": "world",
      "start_offset": 6,
      "end_offset": 11,
      "type": "<ALPHANUM>",
      "position": 1
    }
  ]
}
```



```
# 指定索引中的字段

POST test_index/_analyze
{
  "field": "username",
  "text": "hello world"
}

成功
{
  "tokens": [
    {
      "token": "hello",
      "start_offset": 0,
      "end_offset": 5,
      "type": "<ALPHANUM>",
      "position": 0
    },
    {
      "token": "world",
      "start_offset": 6,
      "end_offset": 11,
      "type": "<ALPHANUM>",
      "position": 1
    }
  ]
}
```



```
# 指定自定义分词器，filter

POST _analyze
{
  "tokenizer": "standard",
  "text": "Hello World!"
}

成功
{
  "tokens": [
    {
      "token": "Hello",
      "start_offset": 0,
      "end_offset": 5,
      "type": "<ALPHANUM>",
      "position": 0
    },
    {
      "token": "World",
      "start_offset": 6,
      "end_offset": 11,
      "type": "<ALPHANUM>",
      "position": 1
    }
  ]
}



POST _analyze
{
  "tokenizer": "standard",
  "filter": ["lowercase"],
  "text": "Hello World!"
}

成功
{
  "tokens": [
    {
      "token": "hello",
      "start_offset": 0,
      "end_offset": 5,
      "type": "<ALPHANUM>",
      "position": 0
    },
    {
      "token": "world",
      "start_offset": 6,
      "end_offset": 11,
      "type": "<ALPHANUM>",
      "position": 1
    }
  ]
}
```
