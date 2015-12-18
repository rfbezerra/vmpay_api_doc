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

*vendible* é obrigatório.

*type* é obrigatório e deve sempre ser 'Product'. Se for outro valor, ou
o parâmetro 'type' estiver ausente, a request retornará um erro 400.

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

*vendible* é obrigatório.

Ao contrário da criação do produto, **ao atualizar não se passa o
parâmetro type**. Caso esteja presente, a request retornará um erro 400.


Excluir
=======

::

    DELETE /v1/vendibles/[id]
