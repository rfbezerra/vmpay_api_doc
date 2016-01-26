#######
Insumos
#######

Listar
======

::

    GET /api/v1/inputs

Ver
===

::

    GET /api/v1/inputs/[id]

Criar
=====

::

    POST /api/v1/inputs

Request::

    {
      "input": {
        "category_id": 11,
        "name": "Leite em pó",
        "unit": "gram"
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *input*

  * *category_id*: id da categoria.
  * *name*: Nome do insumo.
  * *unit*: A unidade de medida do insumo.

    * Valores permitidos: *default* (Unidade), milliliter (Mililitro) e *gram* (Grama).

Opcionais
^^^^^^^^^

Nenhum.

Atualizar
=========

::

    PATCH /api/v1/inputs/[id]

Request::

    {
      "input": {
        "name": "Novo nome"
      }
    }

Campos
------

Ao menos um campo interno a *input* deve ser passado.

Excluir
=======

::

    DELETE /api/v1/inputs/[id]
