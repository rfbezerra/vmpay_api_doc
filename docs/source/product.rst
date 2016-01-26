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

* *vendible*

  * *name*: nome do produto.
  * *type*: valor deve ser sempre *Product*.

Opcionais
^^^^^^^^^

* *vendible*

  * *manufacturer_id*: id do fabricante.
  * *category_id*: id da categoria.
  * *upc_code*: código do produto.

Atualizar
=========

::

    PATCH /api/v1/vendibles/[id]

Request::

    {
      "vendible": {
        "name": "New Vanilla Coke",
        "manufacturer_id": 521
      }
    }

Campos
------

Ao menos um campo interno a *vendible* deve ser passado.

O parâmetro *type* não deve ser passado na atualização. Caso esteja presente, o servidor retornará um erro 400.

Excluir
=======

::

    DELETE /api/v1/vendibles/[id]
