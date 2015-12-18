###########
Fabricantes
###########

Listar
======

::

    GET /api/v1/manufacturers


Ver
===

::

    GET /api/v1/manufacturers/[id]

Criar
=====

::

    POST /api/v1/manufacturers

Request::

    {
      "manufacturer": {
        "name": "TAURUS"
      }
    }

*manufacturer* é obrigatório.

Atualizar
=========

::

    PATCH /api/v1/manufacturers/[id]

Request::

    {
      "manufacturer": {
        "name": "ACME"
      }
    }

*manufacturer* é obrigatório.

Excluir
=======

::

    DELETE /v1/manufacturers/[id]
