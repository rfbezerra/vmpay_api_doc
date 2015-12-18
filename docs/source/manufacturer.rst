##########
Fabricantes
##########

Listar fabricantes
=================

::

    GET /api/v1/manufacturers


Ver um fabricante
=================

::

    GET /api/v1/manufacturers/[id]

Criar um fabricante
===================

::

    POST /api/v1/manufacturers

Request::

    {
      "manufacturer": {
        "name": "TAURUS"
      }
    }

*manufacturer* é obrigatório.

Atualizar um fabricante
=======================

::

    PATCH /api/v1/manufacturers/[id]

Request::

    {
      "manufacturer": {
        "name": "ACME"
      }
    }

*manufacturer* é obrigatório.

Excluir uma fabricante
=====================

::

DELETE /v1/manufacturers/[id]
