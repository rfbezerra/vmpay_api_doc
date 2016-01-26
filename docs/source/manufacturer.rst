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

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *manufacturer*

  * *name*: nome do fabricante.

Opcionais
^^^^^^^^^

Nenhum.

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

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *manufacturer*

  * *name*: nome do fabricante.

Opcionais
^^^^^^^^^

Nenhum.

Excluir
=======

::

    DELETE /api/v1/manufacturers/[id]
