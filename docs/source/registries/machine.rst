########
Máquinas
########

Listar
======

::

  GET /api/v1/machines

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo:

::

  [
    {
      "id": 42,
      "machine_model_id": 82,
      "asset_number": "M010 - 0037",
      "installation": {
        "id": 1106,
        "location_id": 1391,
        "machine_id": 42,
        "equipment_id": 999,
        "place": "the bad place",
        "cash_mode": "cash_and_cashless",
        "restock_mode": "restock_and_cash_collect",
        "notifications_enabled": false
      }
    },
    {
      "id": 222,
      "machine_model_id": 75,
      "asset_number": "M003 - 0009"
    }
  ]

Ver
===

::

  GET /api/v1/machines/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da máquina    sim
=========  ===============  ===========

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo:

::

  {
    "id": 42,
    "machine_model_id": 82,
    "asset_number": "M010 - 0037",
    "installation": {
      "id": 1106,
      "location_id": 1391,
      "machine_id": 42,
      "equipment_id": 999,
      "place": "the bad place",
      "cash_mode": "cash_and_cashless",
      "restock_mode": "restock_and_cash_collect",
      "notifications_enabled": false
    }
  }

Erros
-----

==========  ========================  =========================================
status      descrição                 response body
==========  ========================  =========================================
404         categoria não encontrada  { "status": "404", "error": "Not Found" }
==========  ========================  =========================================

Criar
=====

::

  POST /api/v1/machines

Request::

  {
    "machine": {
      "asset_number": "01234",
      "machine_model_id": "12"
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

Retorno
-------

======  ==================
status  descrição
======  ==================
201     Criado com sucesso
======  ==================

Exemplo::

  {
    "id": 614,
    "machine_model_id": 12,
    "asset_number": "01234"
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
401         não autorizado                        (vazio)
422         erro ao criar                         ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao criar

::

  {
    "machine_model_id": [
      "não pode ficar em branco"
    ],
    "asset_number": [
      "já está em uso"
    ]
  }

Atualizar
=========

::

  PATCH /api/v1/machines/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da máquina    sim
=========  ===============  ===========

Request::

  {
    "machine": {
      "asset_number": "998877"
    }
  }

Campos
------

Ao menos um campo interno a *machine* deve ser passado.

Retorno
-------

======  ======================
status  descrição
======  ======================
200     Atualizado com sucesso
======  ======================

Exemplo::

  {
    "id": 612,
    "machine_model_id": 69,
    "asset_number": "998877",
    "installation": {
      "id": 1119,
      "location_id": 185,
      "machine_id": 612,
      "equipment_id": 314,
      "place": "Recepção 2",
      "cash_mode": "cash_and_cashless",
      "restock_mode": "restock_and_cash_collect",
      "notifications_enabled": false
    }
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
401         não autorizado                        (vazio)
404         categoria não encontrada              { "status": "404", "error": "Not Found" }
422         erro ao atualizar                     ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao atualizar

::

  {
    "asset_number": [
      "não pode ficar em branco"
    ]
  }

Excluir
=======

::

  DELETE /api/v1/machines/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da máquina    sim
=========  ===============  ===========

Retorno
-------

======  ====================  =============
status  descrição             response body
======  ====================  =============
204     Excluído com sucesso  (vazio)
======  ====================  =============


Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
404         categoria não encontrada              { "status": "404", "error": "Not Found" }
==========  ====================================  ====================================================
