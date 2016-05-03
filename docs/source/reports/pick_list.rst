##########
Pick lists
##########

Listar
======

::

  GET /api/v1/pick_lists

Filtros
-------

O parâmetro abaixo pode ser passado como uma `query string <https://en.wikipedia.org/wiki/Query_string>`_.

* **pending_only**: pode ser *true* ou *false*. Se for *true*, apenas as pick lists pendentes serão listadas.

  * Caso não seja passado, é considerado *false*.

Retorno
-------

É retornado um `JSON <https://en.wikipedia.org/wiki/JSON>`_ contendo um array com objetos que correspondem às pick lists. O campos de cada pick list são os seguintes:

* **id**: o id da pick list
* **created_at**: a data de criação da pick list, no formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
* **updated_at**: a data de atualização da pick list, no formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
* **installation_id**: o id da instalação da pick list
* **planogram_id**: o id do planograma da pick list
* **group_id**: o id do grupo da pick list
* **pending**: *true* se pick list estiver pendente, *false* se não estiver
* **url**: o endereço da pick list no VMpay
* **items**: detalhes dos itens da pick list

Segue um exemplo de retorno de consulta:

::

  [
    {
      "id": 2692,
      "created_at": "2015-08-28T14:45:50.000-03:00",
      "updated_at": "2015-08-31T16:44:18.000-03:00",
      "installation_id": 363,
      "planogram_id": 1046,
      "group_id": 1,
      "pending": false,
      "url": "http://vmpay.vertitecnologia.com.br/api/v1/machines/235/installations/363/pick_lists/2692",
      "items": []
    },
    {
      "id": 5248,
      "created_at": "2015-12-16T16:33:23.000-02:00",
      "updated_at": "2015-12-17T17:25:24.000-02:00",
      "installation_id": 1170,
      "planogram_id": 3172,
      "group_id": 1,
      "pending": false,
      "url": "http://vmpay.vertitecnologia.com.br/api/v1/machines/643/installations/1170/pick_lists/5248",
      "items": [
        {
          "id": 208644,
          "planogram_item_id": 120523,
          "quantity": 30
        },
        {
          "id": 208645,
          "planogram_item_id": 120524,
          "quantity": 30
        },
        {
          "id": 208647,
          "planogram_item_id": 120526,
          "quantity": 30
        },
        {
          "id": 208648,
          "planogram_item_id": 120527,
          "quantity": 30
        }
      ]
    },
    {
      "id": 5560,
      "created_at": "2015-12-29T16:12:20.000-02:00",
      "updated_at": "2016-01-05T15:28:02.000-02:00",
      "installation_id": 1170,
      "planogram_id": 3172,
      "group_id": 1,
      "pending": false,
      "url": "http://vmpay.vertitecnologia.com.br/api/v1/machines/643/installations/1170/pick_lists/5560",
      "items": [
        {
          "id": 220561,
          "planogram_item_id": 120524,
          "quantity": 30
        },
        {
          "id": 220564,
          "planogram_item_id": 120527,
          "quantity": 30
        }
      ]
    }
  ]
