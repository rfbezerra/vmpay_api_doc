#################
Provedores de TEF
#################

Listar
======

::

  GET /api/v1/eft_providers

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
      "id":3,
      "name":"Auttar"
    },
    {
      "id":4,
      "name":"Indefinido"
    },
    {
      "id":1,
      "name":"Pay\u0026Go"
    },
    {
      "id":2,
      "name":"SiTef"
    }
  ]
