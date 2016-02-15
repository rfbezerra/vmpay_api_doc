###########
Fabricantes
###########

Listar
======

::

    GET /api/v1/manufacturers

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
      "id": 56,
      "name": "Pepsico"
    },
    {
      "id": 57,
      "name": "Jasmine"
    },
    {
      "id": 59,
      "name": "Lacta"
    },
    {
      "id": 60,
      "name": "Nutrimental"
    },
    {
      "id": 61,
      "name": "Kraft Foods"
    },
    {
      "id": 62,
      "name": "Mars"
    },
    {
      "id": 726,
      "name": "ACME"
    }
  ]


Ver
===

::

    GET /api/v1/manufacturers/[id]

Parâmetros de URL:
------------------

=========  ================  ===========
parâmetro  descrição         obrigatório
=========  ================  ===========
id         id do fabricante  sim
=========  ================  ===========

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
    "id": 56,
    "name": "Pepsico"
  }

Erros
-----

==========  =========================  =========================================
status      descrição                  response body
==========  =========================  =========================================
404         fabricante não encontrado  { "status": "404", "error": "Not Found" }
==========  =========================  =========================================

Criar
=====

::

    POST /api/v1/manufacturers

Request

::

  {
    "manufacturer": {
      "name": "Havanna"
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

Retorno
-------

======  ==================
status  descrição
======  ==================
201     Criado com sucesso
======  ==================

Exemplo:

::

  {
    "id": 727,
    "name": "Havanna"
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
422         erro ao criar                         ver exemplo abaixo
==========  ====================================  ====================================================

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

    PATCH /api/v1/manufacturers/[id]

Parâmetros de URL:
------------------

=========  ================  ===========
parâmetro  descrição         obrigatório
=========  ================  ===========
id         id do fabricante  sim
=========  ================  ===========

Request::

    {
      "manufacturer": {
        "name": "Havanna SA"
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

Retorno
-------

======  ======================
status  descrição
======  ======================
200     Atualizado com sucesso
======  ======================

Exemplo:

::

  {
    "id": 725,
    "name": "Havanna SA"
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
404         fabricante não encontrado             { "status": "404", "error": "Not Found" }
422         erro ao atualizar                     ver exemplo abaixo
==========  ====================================  ====================================================

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

  DELETE /api/v1/manufacturers/[id]

Parâmetros de URL:
------------------

=========  ================  ===========
parâmetro  descrição         obrigatório
=========  ================  ===========
id         id do fabricante  sim
=========  ================  ===========

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
404         fabricante não encontrado              { "status": "404", "error": "Not Found" }
==========  ====================================  ====================================================
