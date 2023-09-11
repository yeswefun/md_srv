


Elasticsearch配置
打开jvm配置文件
vi elasticsearch/config/jvm.options

修改内存空间为256m
-Xms256m
-Xmx256m

Kibana配置
打开Kibana运行文件

vi kibana/bin/kibana
在最后一行前面加上一行，修改node.js最大内存空间

NODE_OPTIONS="${NODE_OPTIONS:=--max-old-space-size=256}"
据了解，对于某些版本的node.js，内存参数横杠要改成下划线


NODE_OPTIONS="${NODE_OPTIONS:=--max_old_space_size=256}"
然后分别启动Elasticsearch和Kibana即可。

