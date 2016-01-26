########
Máquinas
########

Listar
======

::

    GET /api/v1/machines

Ver
===

::

    GET /api/v1/machines/[id]

Criar
=====

::

    POST /api/v1/machines

Request::

    {
      "machine": {
        "asset_number": "987654321",
        "machine_model_id": "69"
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *machine*

  * *asset number*: número de patrimônio.
  * *machine_model_id*: id do modelo da máquina.

Opcionais
^^^^^^^^^

Nenhum.

Atualizar
=========

::

    PATCH /api/v1/machines/[id]

Request::

    {
      "machine": {
        "asset_number": "998877"
      }
    }

Campos
------

Ao menos um campo interno a *machine* deve ser passado.

Excluir
=======

::

    DELETE /api/v1/machines/[id]
