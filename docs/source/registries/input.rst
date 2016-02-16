#######
Insumos
#######

Listar
======

::

  GET /api/v1/inputs

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
      "id": 3044,
      "created_at": "2016-01-20T16:27:55.000-02:00",
      "updated_at": "2016-01-20T16:27:55.000-02:00",
      "category_id": 470,
      "name": "Leite em pó",
      "unit": "gram",
      "url": "http://vmpay.vertitecnologia.com.br/api/v1/inputs/3044"
    },
    {
      "id": 3045,
      "created_at": "2016-01-20T16:28:04.000-02:00",
      "updated_at": "2016-01-20T16:28:04.000-02:00",
      "category_id": 470,
      "name": "Café em pó",
      "unit": "gram",
      "url": "http://vmpay.vertitecnologia.com.br/api/v1/inputs/3045"
    }
  ]

Ver
===

::

  GET /api/v1/inputs/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do insumo     sim
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
    "id": 3044,
    "created_at": "2016-01-20T16:27:55.000-02:00",
    "updated_at": "2016-01-20T16:27:55.000-02:00",
    "category_id": 470,
    "name": "Leite em pó",
    "unit": "gram",
    "url": "http://vmpay.vertitecnologia.com.br/api/v1/inputs/3044"
  }

Erros
-----

==========  ========================  =========================================
status      descrição                 response body
==========  ========================  =========================================
404         insumo não encontrado     { "status": "404", "error": "Not Found" }
==========  ========================  =========================================

Criar
=====

::

    POST /api/v1/inputs

Request::

  {
    "input": {
      "category_id": 11,
      "name": "Leite em pó",
      "unit": "gram"
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *input*

  * *category_id*: id da categoria.
  * *name*: Nome do insumo.
  * *unit*: A unidade de medida do insumo.

    * Valores permitidos: *default* (Unidade), milliliter (Mililitro) e *gram* (Grama).

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
    "id": 2829,
    "created_at": "2016-02-16T08:53:54.731-02:00",
    "updated_at": "2016-02-16T08:53:54.731-02:00",
    "category_id": 11,
    "name": "Leite em pó",
    "unit": "gram",
    "url": "http://localhost:4000/api/v1/inputs/2829"
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
    "name": [
      "já está em uso"
    ]
  }

Atualizar
=========

::

  PATCH /api/v1/inputs/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do insumo     sim
=========  ===============  ===========

Request::

    {
      "input": {
        "name": "Novo nome"
      }
    }

Campos
------

Ao menos um campo interno a *input* deve ser passado.

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
    "id": 2829,
    "created_at": "2016-02-16T08:53:54.000-02:00",
    "updated_at": "2016-02-16T08:59:35.600-02:00",
    "category_id": 11,
    "name": "Novo nome",
    "unit": "gram",
    "url": "http://localhost:4000/api/v1/inputs/2829"
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
401         não autorizado                        (vazio)
404         insumo não encontrado                 { "status": "404", "error": "Not Found" }
422         erro ao atualizar                     ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao atualizar

::

  {
    "name": [
      "não pode ficar em branco"
    ]
  }

Excluir
=======

::

  DELETE /api/v1/inputs/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do insumo     sim
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
404         insumo não encontrado                 { "status": "404", "error": "Not Found" }
==========  ====================================  ====================================================
