


```
PUT /test_index

GET /test_index

GET _cat/indices

DELETE /test_index
```





```
PUT /test_index

成功
{
  "acknowledged": true,
  "shards_acknowledged": true,
  "index": "test_index"
}
```





```
GET /test_index

成功
{
  "test_index": {
    "aliases": {},
    "mappings": {},
    "settings": {
      "index": {
        "creation_date": "1674454638835",
        "number_of_shards": "5",
        "number_of_replicas": "1",
        "uuid": "Xz3r0DgfR5K_dG4p-314kA",
        "version": {
          "created": "6020499"
        },
        "provided_name": "test_index"
      }
    }
  }
}
```






```
DELETE /test_index

成功
{
  "acknowledged": true
}
```
