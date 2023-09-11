

索引 (Index)
    创建
    查询
    删除
    注: 索引不可被更新




查询

```
GET _cat/indices
GET _cat/indices?v

health status index      uuid                   pri rep docs.count docs.deleted store.size pri.store.size
yellow open   account    LfeCduH2ToWjWizimbdPtw   5   1          2            0       10kb           10kb
green  open   orders     eDdLB5DRSAa3ENW8kzRi4Q   1   0          0            0       230b           230b
yellow open   test_index Xz3r0DgfR5K_dG4p-314kA   5   1          3            0     11.5kb         11.5kb
yellow open   products   Cn77vCONQtSWXYlNhjR54Q   5   1          0            0      1.1kb          1.1kb



pri: primary, 主分片
rep: replica, 副本分片

health -> yellow 是因为 es  在创建 索引 时，默认会给 索引 作备份
    单机启动
        主，副 数据 放在 同一台机器，不安全，所以 health -> yellow
```




创建

```
PUT /products

成功
{
    "acknowledged": true,
    "shards_acknowledged": true,
    "index": "products"
}


PUT /orders
{
    "settings": {
        "number_of_shards": 1,
        "number_of_replicas": 0
    }
}

成功
{
    "acknowledged": true,
    "shards_acknowledged": true,
    "index": "products"
}
```




删除
```
DELETE /products

成功
{
  "acknowledged": true
}


DELETE /*
代表删除所有索引
```






```
GET _cat/indices
GET _cat/indices?v


PUT /products

PUT /orders
{
  "settings": {
    "number_of_shards": 1,
    "number_of_replicas": 0
  }
}


DELETE /products
```
