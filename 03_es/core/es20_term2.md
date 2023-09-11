

es 自带如下分词器
    standard
    simple
    whitespace
    stop
    keyword
    pattern
    language



中文分词
    在英文中，单词之间是以空格作为自然分界符，
    在汉语中，没有一个形式上的分界符



中文分词系统
    IK
        可自定义词库，支持热更新分词词典

    jieba
        python 中比较流行的分词系统




自定义分词
    当自带的分词无法满足需求时，可以自定义分词
    
    通过自定义以下内容实现
        Character Filters
            去掉 html标签 或 其它特殊字符

        Tokenizer
            按照一定规则切分单词

        Token Filters
            英文字母转小写
            同义词，近义词




自定义分词 - Character Filters


```
POST _analyze
{
  "tokenizer": "keyword",
  "char_filter": ["html_strip"],
  "text": "</p>I&apos;m so <b>happy</b>!</p>"
}


成功
{
  "tokens": [
    {
      "token": """

I'm so happy!

""",
      "start_offset": 0,
      "end_offset": 33,
      "type": "word",
      "position": 0
    }
  ]
}
```




自定义分词 - Tokenizer

```
POST _analyze
{
  "tokenizer": "path_hierarchy",
  "text": "/one/two/three"
}


成功
{
  "tokens": [
    {
      "token": "/one",
      "start_offset": 0,
      "end_offset": 4,
      "type": "word",
      "position": 0
    },
    {
      "token": "/one/two",
      "start_offset": 0,
      "end_offset": 8,
      "type": "word",
      "position": 0
    },
    {
      "token": "/one/two/three",
      "start_offset": 0,
      "end_offset": 14,
      "type": "word",
      "position": 0
    }
  ]
}
```



自定义分词 - Token Filters

```
    {
      "type": "ngram",
      "min_gram": 4,
      "max_gram": 4
    }
改成
    {
      "type": "ngram",
      "min_gram": 2
    }
或
    {
      "type": "ngram",
      "min_gram": 2,
      "max_gram": 4
    }
```


```
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


成功
{
  "tokens": [
    {
      "token": "hell",
      "start_offset": 2,
      "end_offset": 7,
      "type": "<ALPHANUM>",
      "position": 1
    },
    {
      "token": "ello",
      "start_offset": 2,
      "end_offset": 7,
      "type": "<ALPHANUM>",
      "position": 1
    },
    {
      "token": "worl",
      "start_offset": 8,
      "end_offset": 13,
      "type": "<ALPHANUM>",
      "position": 2
    },
    {
      "token": "orld",
      "start_offset": 8,
      "end_offset": 13,
      "type": "<ALPHANUM>",
      "position": 2
    }
  ]
}
```







自定义分词


```

```
