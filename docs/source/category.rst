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

Campos
------

Obrigatórios
^^^^^^^^^^^^

*category*

*name*: Nome da categoria.

Opcionais:
^^^^^^^^^^

Nenhum.

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

Campos
------

Obrigatórios
^^^^^^^^^^^^

*category*

*name*: Nome da categoria.

Opcionais:
^^^^^^^^^^

Nenhum.

Excluir
=======

::

    DELETE /v1/categories/[id]
