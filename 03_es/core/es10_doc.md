


```
PUT /test_index/doc/1
{
  "username": "Jerry",
  "age": 1
}


POST /test_index/doc
{
  "username": "Steven",
  "age": 66
}

POST /test_index/doc/2
{
  "username": "tony",
  "age": 99
}


GET /test_index/doc/2
GET /test_index/doc/_search
GET /test_index/doc/_search
{
  "query": {
    "term": {
      "_id": {
        "value": "6"
      }
    }
  }
}



GET /test_index/doc/_search


POST _bulk
{"index":{"_index":"test_index","_type":"doc","_id":"3"}}
{"username":"gogo","age":88}
{"delete":{"_index":"test_index","_type":"doc","_id":"1"}}
{"update":{"_index":"test_index","_type":"doc","_id":"2"}}
{"doc":{"username":"tony22","age":22}}




GET /_mget
{
  "docs": [
    {
      "_index": "test_index",
      "_type": "doc",
      "_id": "1"
    },
    {
      "_index": "test_index",
      "_type": "doc",
      "_id": "2"
    }
  ]
}

```



批量操作 _bulk, action_type
    index
        文档已经存在，则覆盖，不存在，则创建
    create
        文档已经存在，则报错
    update
    delete













```
PUT /test_index/doc/1
{
  "username": "Jerry",
  "age": 1
}

成功
{
  "_index": "test_index",
  "_type": "doc",
  "_id": "1",
  "_version": 1,
  "result": "created",
  "_shards": {
    "total": 2,
    "successful": 1,
    "failed": 0
  },
  "_seq_no": 0,
  "_primary_term": 1
}
```




```
POST /test_index/doc
{
  "username": "Steven",
  "age": 66
}

成功
{
  "_index": "test_index",
  "_type": "doc",
  "_id": "loFP3YUBQvP0hHdfOcPQ",
  "_version": 1,
  "result": "created",
  "_shards": {
    "total": 2,
    "successful": 1,
    "failed": 0
  },
  "_seq_no": 0,
  "_primary_term": 1
}
```




```
GET /test_index/doc/1

成功
{
  "_index": "test_index",
  "_type": "doc",
  "_id": "1",
  "_version": 1,
  "found": true,
  "_source": {
    "username": "Jerry",
    "age": 1
  }
}

失败
{
  "_index": "test_index",
  "_type": "doc",
  "_id": "2",
  "found": false
}
```




```
GET /test_index/doc/_search
{
  "query": {
    "term": {
      "_id": {
        "value": "1"
      }
    }
  }
}

成功
{
  "took": 15,
  "timed_out": false,
  "_shards": {
    "total": 5,
    "successful": 5,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": 1,
    "max_score": 1,
    "hits": [
      {
        "_index": "test_index",
        "_type": "doc",
        "_id": "1",
        "_score": 1,
        "_source": {
          "username": "Jerry",
          "age": 1
        }
      }
    ]
  }
}


失败
{
  "took": 1,
  "timed_out": false,
  "_shards": {
    "total": 5,
    "successful": 5,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": 0,
    "max_score": null,
    "hits": []
  }
}
```




```
GET /test_index/doc/_search

成功
{
  "took": 54,
  "timed_out": false,
  "_shards": {
    "total": 5,
    "successful": 5,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": 2,
    "max_score": 1,
    "hits": [
      {
        "_index": "test_index",
        "_type": "doc",
        "_id": "loFP3YUBQvP0hHdfOcPQ",
        "_score": 1,
        "_source": {
          "username": "Steven",
          "age": 66
        }
      },
      {
        "_index": "test_index",
        "_type": "doc",
        "_id": "1",
        "_score": 1,
        "_source": {
          "username": "Jerry",
          "age": 1
        }
      }
    ]
  }
}
```




```
GET /test_index/doc/_search

POST _bulk
{"index":{"_index":"test_index","_type":"doc","_id":"3"}}
{"username":"gogo","age":88}
{"delete":{"_index":"test_index","_type":"doc","_id":"1"}}
{"update":{"_index":"test_index","_type":"doc","_id":"2"}}
{"doc":{"username":"tony22","age":22}}


成功
{
  "took": 63,
  "errors": false,
  "items": [
    {
      "index": {
        "_index": "test_index",
        "_type": "doc",
        "_id": "3",
        "_version": 1,
        "result": "created",
        "_shards": {
          "total": 2,
          "successful": 1,
          "failed": 0
        },
        "_seq_no": 0,
        "_primary_term": 1,
        "status": 201
      }
    },
    {
      "delete": {
        "_index": "test_index",
        "_type": "doc",
        "_id": "1",
        "_version": 2,
        "result": "deleted",
        "_shards": {
          "total": 2,
          "successful": 1,
          "failed": 0
        },
        "_seq_no": 1,
        "_primary_term": 1,
        "status": 200
      }
    },
    {
      "update": {
        "_index": "test_index",
        "_type": "doc",
        "_id": "2",
        "_version": 2,
        "result": "updated",
        "_shards": {
          "total": 2,
          "successful": 1,
          "failed": 0
        },
        "_seq_no": 1,
        "_primary_term": 1,
        "status": 200
      }
    }
  ]
}
```






```
GET /_mget
{
  "docs": [
    {
      "_index": "test_index",
      "_type": "doc",
      "_id": "1"
    },
    {
      "_index": "test_index",
      "_type": "doc",
      "_id": "2"
    }
  ]
}


成功
{
  "docs": [
    {
      "_index": "test_index",
      "_type": "doc",
      "_id": "1",
      "found": false
    },
    {
      "_index": "test_index",
      "_type": "doc",
      "_id": "2",
      "_version": 2,
      "found": true,
      "_source": {
        "username": "tony22",
        "age": 22
      }
    }
  ]
}
```
