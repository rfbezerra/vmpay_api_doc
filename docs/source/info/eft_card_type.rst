###############
Tipos de cartão
###############

Listar
======

::

  GET /api/v1/eft_card_types

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo::

  [
    {
      "id":1,
      "name":"Crédito"
    },
    {
      "id":2,
      "name":"Débito"
    },
    {
      "id":4,
      "name":"Indefinido"
    },
    {
      "id":3,
      "name":"Voucher"
    }
  ]
