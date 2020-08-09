Elasticsearch
=============

建立连接
--------

.. code-block:: go

    import "gopkg.in/olivere/elastic.v5"

    // 返回的是 *elastic.Client 类型
    client, err := elastic.NewClient(elastic.SetURL("http://127.0.0.1:9200"))

    // 如果es 在容器中运行，需要加上 SetSniff, 否则连不上
    client, err := elastic.NewClient(elastic.SetSniff(false), elastic.SetURL("http://127.0.0.1:9200"))


查询
----

.. code-block:: go

    query := elastic.NewBoolQuery()
    query = query.Must(elastic.NewTermQuery("user", "olivere"))
    query = query.Filter(elastic.NewTermQuery("account", 1))

    // 通过 Source 可以查看 query 语句
    src, _ := query.Source()

query 语句如下：

.. code-block:: json

    {
      "bool": {
        "filter": {
          "term": {
            "account": 1
          }
        },
        "must": {
          "term": {
            "user": "olivere"
          }
        }
      }
    }

插入
----

.. code-block:: go

    client.Index().Index(index).Type("default").BodyJson(&document).Do(context.Background())