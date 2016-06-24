#####
Rotas
#####

Listar
======

::

    GET /api/v1/routes

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
      "id": 3,
      "name": "Rota 1"
    },
    {
      "id": 4,
      "name": "Rota 2"
    },
    {
      "id": 5,
      "name": "Rota 3"
    },
    {
      "id": 7,
      "name": "Rota 4"
    },
    {
      "id": 10,
      "name": "Rota 5"
    }
  ]


Ver
===

::

    GET /api/v1/routes/[id]

Parâmetros de URL:
------------------

=========  ==========  ===========
parâmetro  descrição   obrigatório
=========  ==========  ===========
id         id da rota  sim
=========  ==========  ===========

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
    "id": 4,
    "name": "Rota 1",
    "installation_ids": [23, 56, 66, 81, 99, 101]
  }

Erros
-----

==========  ===================  =========================================
status      descrição            response body
==========  ===================  =========================================
404         rota não encontrada  { "status": "404", "error": "Not Found" }
==========  ===================  =========================================

Criar
=====

::

    POST /api/v1/routes

Request

::

  {
    "route": {
      "name": "Rota 66",
      "installation_ids": [19, 22, 78, 79]
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *route*

  * *name*: nome da rota.
  * *installation_ids*: um array contendo os id's das instalações que farão parte desta rota.

Opcionais
^^^^^^^^^

Nenhum.

Retorno
-------

======  ==================
status  descrição
======  ==================
201     criada com sucesso
======  ==================

Exemplo:

::

  {
    "id": 56,
    "name": "Rota 66",
    "installation_ids": [19, 22, 78, 79]
  }

Erros
-----

==========  ===================  ====================================================
status      descrição            response body
==========  ===================  ====================================================
400         parâmetros faltando  { "status": "400", "error": "Bad Request" }
422         erro ao criar        ver exemplo abaixo
==========  ===================  ====================================================

422 - erro ao criar

::

  {
    "name": [
      "não pode ficar em branco"
    ]
  }



Atualizar
=========

::

    PATCH /api/v1/routes/[id]

Parâmetros de URL:
------------------

=========  ==========  ===========
parâmetro  descrição   obrigatório
=========  ==========  ===========
id         id da rota  sim
=========  ==========  ===========

Request::

    {
      "route": {
        "name": "Rota 1",
        "installation_ids": [23, 56, 66, 81, 101, 105, 111]
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *route*

  * *name*: nome da rota.
  * *installation_ids*: um array contendo os id's das instalações que farão parte desta rota.

Opcionais
^^^^^^^^^

Nenhum.

Retorno
-------

======  ======================
status  descrição
======  ======================
200     atualizada com sucesso
======  ======================

Exemplo:

::

  {
    "id": 4,
    "name": "Rota 1",
    "installation_ids": [23, 56, 66, 81, 101, 105, 111]
  }

Erros
-----

==========  ===================  ====================================================
status      descrição            response body
==========  ===================  ====================================================
400         parâmetros faltando  { "status": "400", "error": "Bad Request" }
404         rota não encontrada  { "status": "404", "error": "Not Found" }
422         erro ao atualizar    ver exemplo abaixo
==========  ===================  ====================================================

422 - erro ao atualizar:

::

  {
    "name": [
      "não pode ficar em branco"
    ]
  }

Excluir
=======

::

  DELETE /api/v1/routes/[id]

Parâmetros de URL:
------------------

=========  ==========  ===========
parâmetro  descrição   obrigatório
=========  ==========  ===========
id         id da rota  sim
=========  ==========  ===========

Retorno
-------

======  ====================  =============
status  descrição             response body
======  ====================  =============
204     Excluída com sucesso  (vazio)
======  ====================  =============

Erros
-----

==========  ===================  ====================================================
status      descrição            response body
==========  ===================  ====================================================
404         rota não encontrada  { "status": "404", "error": "Not Found" }
==========  ===================  ====================================================
