##########
Categorias
##########

Listar
======

::

    GET /api/v1/categories


Ver
===

::

    GET /api/v1/categories/[id]

Criar
=====

::

    POST /api/v1/categories

Request::

    {
      "category": {
        "name": "Refrigerantes"
      }
    }

*category* é obrigatório.

Atualizar
=========

::

    PATCH /api/v1/categories/[id]

Request::

    {
      "category": {
        "name": "Refrigerantes"
      }
    }

*category* é obrigatório.

Excluir
=======

::

    DELETE /v1/categories/[id]
