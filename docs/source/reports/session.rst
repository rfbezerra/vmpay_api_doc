######
Caixas
######

Listar
======

::

    GET /api/v1/sessions

Filtros
-------

Os parâmetros abaixo podem ser passados como uma
`query string <https://en.wikipedia.org/wiki/Query_string>`_. Mais de um filtro
pode ser passado na mesma consulta.

Este serviço suporta `paginação <../overview.html#paginacao>`_.

* **started_at_from**: a data inicial de início dos caixas.

  * Se passado, a consulta retorna somente caixas cujas datas de início ocorreram a partir desta data e hora, inclusive.

    * Se não passado, considera-se como sendo 7 dias atrás, às 00:00.
  * Deve-se passar a data e também a **hora**; se não passada, considerada-se 00:00 `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Um formato possível é *dd/mm/yyyy hh:mi:ss*. Nesse caso a data e hora devem estar em `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Este campo também suporta o formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
  * Caso o formato da data seja inválido, é retornado erro com o código HTTP 400 (*bad request*).

* **started_at_to**: a data final de início dos caixas.

  * Se passado, a consulta retorna somente caixas cujas datas de início ocorreram até esta data e hora, inclusive.

    * Se não passado, considera-se como sendo hoje, às 23:59:59.
  * Deve-se passar a data e também a **hora**; se não passada, considerada-se 00:00 `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Um formato possível é *dd/mm/yyyy hh:mi:ss*. Nesse caso a data e hora devem estar em `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Este campo também suporta o formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
  * Caso o formato da data seja inválido, é retornado erro com o código HTTP 400 (*bad request*).

* **ended_at_from**: a data inicial de término dos caixas.

  * Se passado, a consulta retorna somente caixas cujas datas de término ocorreram a partir desta data e hora, inclusive.
  * Deve-se passar a data e também a **hora**; se não passada, considerada-se 00:00 `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Um formato possível é *dd/mm/yyyy hh:mi:ss*. Nesse caso a data e hora devem estar em `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Este campo também suporta o formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
  * Caso o formato da data seja inválido, é retornado erro com o código HTTP 400 (*bad request*).

* **ended_at_to**: a data final de término dos caixas.

  * Se passado, a consulta retorna somente caixas cujas datas de término ocorreram até esta data e hora, inclusive.
  * Deve-se passar a data e também a **hora**; se não passada, considerada-se 00:00 `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Um formato possível é *dd/mm/yyyy hh:mi:ss*. Nesse caso a data e hora devem estar em `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Este campo também suporta o formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
  * Caso o formato da data seja inválido, é retornado erro com o código HTTP 400 (*bad request*).

* **client_id**: o id do cliente dos caixas.

  * Se passado, a consulta retorna somente caixas deste cliente.

* **location_id**: o id do local dos caixas.

  * Se passado, a consulta retorna somente caixas deste local.

* **machine_id**: o id da máquina dos caixas.

  * Se passado, a consulta retorna somente caixas desta máquina.

* **installation_id**: o id da instalação dos caixas.

  * Se passado, a consulta retorna somente caixas desta instalação.

* **route_id**: o id da rota dos caixas.

  * Se passado, a consulta retorna somente caixas cujas instalações pertencem a esta rota.

* **active_installations_only**: pode ser *true* ou *false*. Se for *true*, apenas os caixas de instalações ativas serão listadas; se for *false*, qualquer instalação é listada.

  * Caso não seja passado, é considerado *true*.

* **status**: pode ser *open* ou *closed*. Se for *open*, apenas os caixas abertos são listados; se for *closed*, somente caixas fechados são listados.

  * Caso não seja passado, qualquer caixa é listado.

Retorno
-------

É retornado um `JSON <https://en.wikipedia.org/wiki/JSON>`_ contendo um array com objetos que correspondem aos caixas. O array é ordenado por data e hora de início do caixa, da mais recente para a mais antiga. O campos de cada caixa são os seguintes:

* **id**: o id do caixa.
* **started_at**: a data e hora de início do caixa, no formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
* **ended_at**: a data e hora do término do caixa, no formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
* **last_audit_began_at**: a data e hora da última auditoria da instalação do caixa, no formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
* **client_id**: o id do cliente do caixa.
* **location_id**: o id do local do caixa.
* **machine_id**: o id da máquina do caixa.
* **installation_id**: o id da instalação do caixa.

* **cashbox_amount**: o valor no cofre.
* **bill_validator_amount**: o valor no noteiro.
* **collectible_amount**: o valor a coletar.
* **changer_amount**: o valor de giro de troco.
* **supplied_cash_amount**: o valor de carga/retirada.
* **cashless_transaction_amount**: o valor de transações cashless.
* **product_value_amount**: o valor do total de vendas.
* **difference_amount**: o valor da diferença no caixa.
* **total_in_coin_changer**: o valor de troco no moedeiro.
* **total_in_bill_changer**: o valor de troco no reciclador.
* **total_in_changer**: o valor total de troco.
* **client**: detalhes do cliente do caixa.
* **location**: detalhes do local do caixa.
* **machine**: detalhes da máquina do caixa.

Segue um exemplo de retorno de consulta:

::

    [
      {
        "id":110408,
        "started_at":"2017-04-26T13:00:26.000-03:00",
        "ended_at":"2017-04-26T13:08:08.000-03:00",
        "last_audit_began_at":"2017-04-26T17:30:29.000Z",
        "client_id":949,
        "location_id":2325,
        "machine_id":1687,
        "installation_id":2865,
        "cashbox_amount":0.0,
        "bill_validator_amount":0.0,
        "collectible_amount":0.0,
        "changer_amount":0.0,
        "supplied_cash_amount":0.0,
        "cashless_transaction_amount":0.0,
        "product_value_amount":0.0,
        "difference_amount":0.0,
        "total_in_coin_changer":69.3,
        "total_in_bill_changer":0.0,
        "total_in_changer":69.3,
        "client":{
          "name":"Cliente 1"
        },
        "location":{
          "client_id":949,
          "name":"Local 1"
        },
        "machine":{
          "machine_model_id":82,
          "asset_number":"1234"
        }
      },
      {
        "id":110407,
        "started_at":"2017-04-26T12:53:44.000-03:00",
        "ended_at":null,
        "last_audit_began_at":"2017-04-26T17:30:29.000Z",
        "client_id":1047,
        "location_id":1216,
        "machine_id":335,
        "installation_id":561,
        "cashbox_amount":0.0,
        "bill_validator_amount":4.0,
        "collectible_amount":4.0,
        "changer_amount":0.0,
        "supplied_cash_amount":0.0,
        "cashless_transaction_amount":5.0,
        "product_value_amount":9.0,
        "difference_amount":0.0,
        "total_in_coin_changer":43.15,
        "total_in_bill_changer":0.0,
        "total_in_changer":43.15,
        "client":{
          "name":"CLiente 1"
        },
        "location":{
          "client_id":1047,
          "name":"Local 2"
        },
        "machine":{
          "machine_model_id":81,
          "asset_number":"4321"
        }
      }
    ]
