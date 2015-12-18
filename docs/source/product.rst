########
Produtos
########

Listar
======

::

    GET /api/v1/vendibles


Ver
===

::

    GET /api/v1/vendibles/[id]

Criar
=====

::

    POST /api/v1/vendibles

Request::

    {
      "vendible": {
        "type": "Product",
        "name": "Vanilla Coke",
        "manufacturer_id": 56,
        "category_id": 21,
        "upc_code": 111
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

*vendible*

*name*: Nome do produto.

*type*: valor deve ser sempre *Product*.

Opcionais:
^^^^^^^^^^

*manufacturer_id*: id do fabricante

*category_id*: id da categoria

*upc_code*: código do produto

Atualizar
=========

::

    PATCH /api/v1/vendibles/[id]

Request::

    {
      "vendible": {
        "name": "Vanilla Coke",
        "manufacturer_id": 521,
        "category_id": 253,
        "upc_code": 999
      }
    }

Campos
------

Proibidos:
^^^^^^^^^^

*type*: Este parâmetro não é passado na atualização· Caso esteja
presente, a request retornará um erro 400.

Obrigatórios
^^^^^^^^^^^^

*vendible*

Pelo menos um campo deve ser passado.

Excluir
=======

::

    DELETE /v1/vendibles/[id]
