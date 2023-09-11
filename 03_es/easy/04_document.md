


文档 (Document)
    添加
    查询
    更新
    删除




添加文档

```
#指定 _id
POST /products/_doc/1
{
  "title": "redmi note11",
  "price": 8999.9,
  "created": "2020-10-30",
  "brief": "redmi note11 5000毫安 LCD屏幕"
}


成功
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}
```



```
#自动生成 _id
POST /products/_doc
{
  "title": "redmi note12",
  "price": 6666.9,
  "created": "2021-10-30",
  "brief": "redmi note12 5000毫安 OLED屏幕"
}


成功
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "ODUEUYYBI3-_pG9DQRGk",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 1,
  "_primary_term" : 1
}
```




查询文档

```
GET /products/_doc/1

成功
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 1,
  "_seq_no" : 0,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "title" : "redmi note11",
    "price" : 8999.9,
    "created" : "2020-10-30",
    "brief" : "redmi note11 5000毫安 LCD屏幕"
  }
}
```


```
GET /products/_doc/_search

成功
{
  "took" : 586,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 1,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "products",
        "_type" : "_doc",
        "_id" : "ODUEUYYBI3-_pG9DQRGk",
        "_score" : 1.0,
        "_source" : {
          "title" : "redmi note12",
          "price" : 6666.9,
          "created" : "2021-10-30",
          "brief" : "redmi note12 5000毫安 OLED屏幕"
        }
      }
    ]
  }
}
```




删除文档

```
DELETE /products/_doc/1

成功
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 2,
  "result" : "deleted",
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 2,
  "_primary_term" : 1
}

失败
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 3,
  "result" : "not_found",
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 3,
  "_primary_term" : 1
}
```




更新文档


先删除文档，再添加文档
    需要传入原始文档的全部字段

```
PUT /products/_doc/1
{
  "title" : "redmi note12 pro"
}


成功
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 2,
  "result" : "updated",
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 4,
  "_primary_term" : 1
}



GET /products/_doc/1

成功
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 2,
  "_seq_no" : 4,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "title" : "redmi note12 pro"
  }
}


#这种方式需要以下形式才能保持原始的mapping
PUT /products/_doc/1
{
  "title" : "redmi note12",
  "price" : 6666.9,
  "created" : "2021-10-30",
  "brief" : "redmi note12 5000毫安 OLED屏幕"
}


GET /products/_doc/1

{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 4,
  "_seq_no" : 6,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "title" : "redmi note12",
    "price" : 6666.9,
    "created" : "2021-10-30",
    "brief" : "redmi note12 5000毫安 OLED屏幕"
  }
}
```




更新部分字段

```
POST /products/_doc/1/_update
{
  "doc": {
    "title" : "redmi note12 pro"
  }
}

成功
{
  "_index" : "products",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 2,
  "result" : "noop",
  "_shards" : {
    "total" : 0,
    "successful" : 0,
    "failed" : 0
  },
  "_seq_no" : 4,
  "_primary_term" : 1
}
```
