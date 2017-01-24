#######
Alertas
#######

Listar
======

::

    GET /api/v1/alerts

Filtros
-------

Os parâmetros abaixo podem ser passados como uma
`query string <https://en.wikipedia.org/wiki/Query_string>`_. Mais de um filtro
pode ser passado na mesma consulta.

Este serviço suporta `paginação <../overview.html#paginacao>`_.

* **client_id**: o id do cliente dos alertas.

  * Se passado, a consulta retorna somente alertas ocorridos neste cliente.

* **location_id**: o id do local dos alertas.

  * Se passado, a consulta retorna somente alertas ocorridos neste local.

* **machine_id**: o id da máquina dos alertas.

  * Se passado, a consulta retorna somente alertas ocorridos nesta máquina.

* **machine_manufacturer_id**: o id do fabricante das máquinas dos alertas.

  * Se passado, a consulta retorna somente alertas ocorridos em máquinas deste fabricante.

* **installation_id**: o id da instalação dos alertas.

  * Se passado, a consulta retorna somente alertas ocorridos nesta instalação.

Retorno
-------

É retornado um `JSON <https://en.wikipedia.org/wiki/JSON>`_ contendo um array com objetos que correspondem aos alertas. O array é ordenado por data e hora de alerta, da mais recente para a mais antiga. O campos de cada alerta são os seguintes:

* **occurred_at**: a data e hora do alerta, no formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
* **client_id**: o id do cliente do alerta.
* **location_id**: o id do local do alerta.
* **machine_id**: o id da máquina do alerta.
* **installation_id**: o id da instalação do alerta.
* **description**: a descrição do alerta.
* **client**: detalhes do cliente do alerta.
* **location**: detalhes do local do alerta.
* **machine**: detalhes da máquina do alerta.

Segue um exemplo de retorno de consulta:

::

    [
      {
        "occurred_at":"2016-02-11T12:34:56.000-02:00",
        "client_id":1,
        "location_id":2,
        "machine_id":3,
        "installation_id":4,
        "description":"A comunicação falhou",
        "client": {
          "name":"Client X"
        },
        "location": {
          "client_id":1,
          "name":"Location X"
        },
        "machine": {
          "machine_model_id":9,
          "asset_number":"123"
        }
      },
      {
        "occurred_at":"2016-02-11T12:45:12.000-02:00",
        "client_id":1,
        "location_id":2,
        "machine_id":3,
        "installation_id":4,
        "description":"A comunicação foi restabelecida",
        "client": {
          "name":"Client X"
        },
        "location": {
          "client_id":1,
          "name":"Location X"
        },
        "machine": {
          "machine_model_id":9,
          "asset_number":"123"
        }
      }
    ]
