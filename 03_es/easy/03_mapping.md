


映射 (Mapping)
    创建
    查询
    更新
    删除



字段类型
    字符串类型
        text / keyword
        text 分词
        keyword 不分词
    
    数字类型
        integer / long

    小数类型
        float / double

    布尔类型
        boolean

    日期类型
        date



映射 不能脱离 索引 单独使用，需要配合 索引 一起使用

映射信息不能删除，不能更新



创建索引和映射

```
GET _cat/indices
GET _cat/indices?v

# mapping {id, title, price, created, brief}
PUT /products
{
  "settings": {
    "number_of_shards": 1,
    "number_of_replicas": 0
  },
  "mappings": {
    "properties": {
      "id": {
        "type": "integer"
      },
      "title": {
        "type": "keyword"
      },
      "price": {
        "type": "double"
      },
      "created": {
        "type": "date"
      },
      "brief": {
        "type": "text"
      }
    }
  }
}


成功
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "products"
}
```




查看索引的映射信息

```
GET /products/_mapping

成功
{
  "products" : {
    "mappings" : {
      "properties" : {
        "brief" : {
          "type" : "text"
        },
        "created" : {
          "type" : "date"
        },
        "id" : {
          "type" : "integer"
        },
        "price" : {
          "type" : "double"
        },
        "title" : {
          "type" : "keyword"
        }
      }
    }
  }
}
```






```
GET _cat/indices
GET _cat/indices?v

# mapping {id, title, price, created, brief}
PUT /products
{
  "settings": {
    "number_of_shards": 1,
    "number_of_replicas": 0
  },
  "mappings": {
    "properties": {
      "id": {
        "type": "integer"
      },
      "title": {
        "type": "keyword"
      },
      "price": {
        "type": "double"
      },
      "created": {
        "type": "date"
      },
      "brief": {
        "type": "text"
      }
    }
  }
}


GET /products/_mapping
```

