########
Produtos
########

Listar
======

::

    GET /api/v1/products

Ver
===

::

    GET /api/v1/products/[id]

Criar
=====

::

    POST /api/v1/products

Request::

    {
      "product": {
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

* *product*

  * *name*: nome do produto.
  * *manufacturer_id*: id do fabricante.
  * *category_id*: id da categoria.

Opcionais
^^^^^^^^^

* *product*

  * *upc_code*: código do produto.

Atualizar
=========

::

    PATCH /api/v1/products/[id]

Request::

    {
      "vendible": {
        "name": "New Vanilla Coke",
        "manufacturer_id": 521
      }
    }

Campos
------

Ao menos um campo interno a *product* deve ser passado.

Excluir
=======

::

    DELETE /api/v1/products/[id]

API obsoleta
============

A API abaixo tornou-se obsoleta em favor de uma API mais simples, documentada acima. A API abaixo ainda funciona, mas o seu uso é desencorajado.

Listar (obsoleto)
-----------------

::

    GET /api/v1/vendibles

Ver (obsoleto)
--------------

::

    GET /api/v1/vendibles/[id]

Criar (obsoleto)
----------------

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
^^^^^^

Obrigatórios
^^^^^^^^^^^^

* *vendible*

  * *name*: nome do produto.
  * *type*: valor deve ser sempre *Product*.
  * *manufacturer_id*: id do fabricante.
  * *category_id*: id da categoria.

Opcionais
^^^^^^^^^

* *vendible*

  * *upc_code*: código do produto.

Atualizar (obsoleto)
--------------------

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
^^^^^^

Ao menos um campo interno a *vendible* deve ser passado.

O parâmetro *type* é ignorado.

Excluir (obsoleto)
------------------

::

    DELETE /api/v1/vendibles/[id]
