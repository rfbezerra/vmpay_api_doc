##########
Categorias
##########

Listar categorias
=================

::

    GET /api/v1/categories


Ver uma categoria
=================

::

    GET /api/v1/categories/[id]

Criar uma categoria
===================

::

    POST /api/v1/categories

Request::

    {
      "category": {
        "name": "Refrigerantes"
      }
    }

*category* é obrigatório.

Atualizar uma categoria
=======================

::

    PATCH /api/v1/categories/[id]

Request::

    {
      "category": {
        "name": "Refrigerantes"
      }
    }

*category* é obrigatório.

Excluir uma categoria
=====================

::

DELETE /v1/categories/[id]
