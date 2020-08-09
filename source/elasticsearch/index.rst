Elasticsearch
=============

建立连接

.. code-block:: go

    import "gopkg.in/olivere/elastic.v5"

    lient, err := elastic.NewClient(elastic.SetURL("http://192.168.1.100:9296"))