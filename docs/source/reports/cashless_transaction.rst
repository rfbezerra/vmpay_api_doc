###################
Transações cashless
###################

Listar
======

::

    GET /api/v1/cashless_transactions

Filtros
-------

Os parâmetros abaixo podem ser passados como uma
`query string <https://en.wikipedia.org/wiki/Query_string>`_. Mais de um filtro
pode ser passado na mesma consulta.

Este serviço suporta `paginação <../overview.html#paginacao>`_.

* **start_date**: a data de início das transações cashless.

  * Se passado, a consulta retorna somente transações cashless ocorridas a partir desta data e hora, inclusive.
  * Deve-se passar a data e também a **hora**; se não passada, considerada-se 00:00 `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Um formato possível é *dd/mm/yyyy hh:mi:ss*. Nesse caso a data e hora devem estar em `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Este campo também suporta o formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
  * Caso o formato da data seja inválido, é retornado erro com o código HTTP 400 (*bad request*).

* **end_date**: a data final das transações cashless.

  * Se passado, a consulta retorna somente transações cashless ocorridas até esta data e hora, inclusive.
  * Deve-se passar a data e também a **hora**; se não passada, considerada-se 00:00 `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Um formato possível é *dd/mm/yyyy hh:mi:ss*. Nesse caso a data e hora devem estar em `UTC <https://en.wikipedia.org/wiki/Coordinated_Universal_Time>`_.
  * Este campo também suporta o formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
  * Caso o formato da data seja inválido, é retornado erro com o código HTTP 400 (*bad request*).

* **client_id**: o id do cliente das transações cashless.

  * Se passado, a consulta retorna somente transações cashless ocorridas para este cliente.

* **location_id**: o id do local das transações cashless.

  * Se passado, a consulta retorna somente transações cashless ocorridas neste local.

* **machine_id**: o id da máquina das transações cashless.

  * Se passado, a consulta retorna somente transações cashless ocorridas nesta máquina.

* **installation_id**: o id da instalação das transações cashless.

  * Se passado, a consulta retorna somente transações cashless ocorridas nesta instalação.

* **category_id**: a categoria dos produtos das transações cashless.

  * Se passado, a consulta retorna somente transações cashless de produtos desta categoria.

* **manufacturer_id**: o fabricante dos produtos das transações cashless.

  * Se passado, a consulta retorna somente transações cashless de produtos deste fabricante.

* **good_id**: o produto das transações cashless.

  * Se passado, a consulta retorna somente transações cashless deste produto.
  * Tal produto pode ser composto (combo ou bebidas quentes) ou não (produtos vendidos por unidade).
  * `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.

* **eft_provider_id**: o provedor de TEF das transações cashless.

  * Se passado, a consulta retorna somente transações cashless desse provedor TEF.

* **eft_authorizer_id**: o adquirente de TEF das transações cashless.

  * Se passado, a consulta retorna somente transações cashless desse adquirente.

* **eft_card_brand_id**: o cartão utilizado nas transações cashless.

  * Se passado, a consulta retorna somente transações cashless desse cartão.

* **eft_card_type_id**: o tipo de cartão utilizado nas transações cashless.

  * Se passado, a consulta retorna somente transações cashless desse tipo de cartão.

Retorno
-------

É retornado um `JSON <https://en.wikipedia.org/wiki/JSON>`_ contendo um array com objetos que correspondem às transações cashless. O array é ordenado por data e hora das transações, da mais recente para a mais antiga. O campos de cada transação cashless são os seguintes:

* **id**: o id da transação cashless.
* **occurred_at**: a data e hora da transação cashless, no formato `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_.
* **client_id**: o id do cliente da transação cashless.
* **location_id**: o id do local da transação cashless.
* **machine_id**: o id da máquina da transação cashless.
* **installation_id**: o id da instalação da transação cashless.
* **planogram_item_id**: o id do item de planograma em que ocorreu a transação cashless (canaleta, seleção ou combo).
* **good_id**: o id do produto (composto ou não) vendido.

  * * `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.

* **eft_provider_id**: o id do provedor de TEF das transações cashless.
* **eft_authorizer_id**: o id do adquirente de TEF das transações cashless.
* **eft_card_brand_id**: o id do cartão utilizado nas transações cashless.
* **eft_card_type_id**: o id do tipo de cartão utilizado nas transações cashless.
* **coil**: o número do item de planograma em que ocorreu a transação cashless (canaleta, seleção ou combo).
* **transaction_value**: o valor total da transação cashless.
* **remote_credit**: um booleano indicando se a transação foi ou não um crédito remoto.
* **client**: detalhes do cliente da transação cashless.
* **location**: detalhes do local da transação cashless.
* **machine**: detalhes da máquina da transação cashless.
* **good**: detalhes do produto vendido.
* **eft_provider**: detalhes do provedor de TEF das transações cashless.
* **eft_authorizer**: detalhes do adquirente de TEF das transações cashless.
* **eft_card_brand**: detalhes do cartão utilizado nas transações cashless.
* **eft_card_type**: detalhes do tipo de cartão utilizado nas transações cashless.

Segue um exemplo de retorno de consulta:

::

    [
      {
        "id":123489,
        "occurred_at":"2016-01-26T07:45:36.000-02:00",
        "client_id":1,
        "location_id":2,
        "machine_id":3,
        "installation_id":4,
        "planogram_item_id":5,
        "good_id":7,
        "eft_provider_id":1,
        "eft_authorizer_id":1,
        "eft_card_brand_id":21,
        "eft_card_type_id":1,
        "coil":"1",
        "transaction_value":2.5,
        "remote_credit":false,
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
        },
        "good": {
          "type":"Product",
          "category_id":1,
          "manufacturer_id":2,
          "name":"Product X",
          "upc_code":"333"
        },
        "eft_provider": {
          "name":"Pay&Go"
        },
        "eft_authorizer_id": {
          "name":"Cielo"
        },
        "eft_card_brand": {
          "name": "Visa"
        },
        "eft_card_type": {
          "name": "Crédito"
        }
      },
      {
        "id":123456,
        "occurred_at":"2016-01-26T07:14:24.000-02:00",
        "client_id":1,
        "location_id":2,
        "machine_id":3,
        "installation_id":4,
        "planogram_item_id":6,
        "good_id":8,
        "eft_provider_id":2,
        "eft_authorizer_id":4,
        "eft_card_brand_id":12,
        "eft_card_type_id":2,
        "coil":"3",
        "transaction_value":2.5,
        "remote_credit":false,
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
        },
        "good": {
          "type":"Product",
          "category_id":1,
          "manufacturer_id":3,
          "name":"Product Y",
          "upc_code":"444"
        },
        "eft_provider": {
          "name":"SiTef"
        },
        "eft_authorizer_id": {
          "name":"Rede"
        },
        "eft_card_brand": {
          "name": "Mastercard"
        },
        "eft_card_type": {
          "name": "Débito"
        }
      }
    ]
