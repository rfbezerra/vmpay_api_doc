##################
Produtos compostos
##################

Listar
======

::

    GET /api/v1/compound_products

Ver
===

::

    GET /api/v1/compound_products/[id]

Criar
=====

::

    POST /api/v1/compound_products

Request::

    {
      "compound_product": {
        "type": "Combo",
        "category_id": 12,
        "name": "Coca + Ruffles"
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *compound_product*

  * *type*: tipo do produto composto.

    * Valores permitidos: *Combo* (combos) e *Mixture* (bebidas quentes).

  * *category_id*: id da categoria.
  * *name*: Nome do produto composto.

Opcionais
^^^^^^^^^

Nenhum.

Atualizar
=========

::

    PATCH /api/v1/compound_products/[id]

Request::

    {
      "compound_product": {
        "name": "Novo nome"
      }
    }

Campos
------

Ao menos um campo interno a *compound_product* deve ser passado.

Caso o parâmetro *type* seja passado, o mesmo é desconsiderado.

Excluir
=======

::

    DELETE /api/v1/compound_products/[id]
