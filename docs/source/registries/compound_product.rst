##################
Produtos compostos
##################

Listar
======

::

    GET /api/v1/compound_products

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo::

  [
    {
      "id": 2928,
      "created_at": "2015-12-18T17:23:20.000-02:00",
      "updated_at": "2015-12-18T17:23:20.000-02:00",
      "type": "Combo",
      "category_id": 236,
      "name": "Nescau + Leite",
      "external_id": "qwe111"
    },
    {
      "id": 3046,
      "created_at": "2016-01-20T16:28:18.000-02:00",
      "updated_at": "2016-01-20T16:28:18.000-02:00",
      "type": "Mixture",
      "category_id": 471,
      "name": "Capuccino brasileiro",
      "external_id": "qwe222"
    }
  ]


Ver
===

::

  GET /api/v1/compound_products/[id]

Parâmetros de URL:
------------------

=========  ======================  ===========
parâmetro  descrição               obrigatório
=========  ======================  ===========
id         id do produto composto  sim
=========  ======================  ===========

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
    "id": 3046,
    "created_at": "2016-01-20T16:28:18.000-02:00",
    "updated_at": "2016-01-20T16:28:18.000-02:00",
    "type": "Mixture",
    "category_id": 471,
    "name": "Capuccino brasileiro",
    "external_id": "qwe222"
  }

Erros
-----

==========  ===============================  =========================================
status      descrição                        response body
==========  ===============================  =========================================
404         produto composto não encontrado  { "status": "404", "error": "Not Found" }
==========  ===============================  =========================================

Criar
=====

::

    POST /api/v1/compound_products

Request::

  {
    "compound_product": {
      "type": "Combo",
      "category_id": 12,
      "name": "Coca + Ruffles",
      "external_id": "qwe123"
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *compound_product*

  * *type*: tipo do produto composto.

    * Valores permitidos: *Combo* (combos) e *Mixture* (bebidas quentes).

  * *category_id*: id da categoria.
  * *name*: Nome do produto composto.

Opcionais
^^^^^^^^^

* *compound_product*

  * *external_id*: identificador externo do produto composto.

Retorno
-------

======  ==================
status  descrição
======  ==================
201     Criado com sucesso
======  ==================

Exemplo::

  {
    "id": 2831,
    "created_at": "2016-02-16T11:19:06.003-02:00",
    "updated_at": "2016-02-16T11:19:06.003-02:00",
    "type": "Combo",
    "category_id": 12,
    "name": "Coca + Ruffles",
    "external_id": "qwe123"
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
      "não pode ficar em branco"
    ]
  }


Atualizar
=========

::

  PATCH /api/v1/compound_products/[id]

Parâmetros de URL:
------------------

=========  ======================  ===========
parâmetro  descrição               obrigatório
=========  ======================  ===========
id         id do produto composto  sim
=========  ======================  ===========

Request::

    {
      "compound_product": {
        "name": "Novo nome"
      }
    }

Campos
------

Ao menos um campo interno a *compound_product* deve ser passado.

Caso o parâmetro *type* seja passado, o mesmo é desconsiderado.

Retorno
-------

======  ======================
status  descrição
======  ======================
200     Atualizado com sucesso
======  ======================

Exemplo::

  {
    "id": 2831,
    "created_at": "2016-02-16T11:19:06.000-02:00",
    "updated_at": "2016-02-16T11:25:01.944-02:00",
    "type": "Combo",
    "category_id": 12,
    "name": "Novo produto composto",
    "external_id": null
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
401         não autorizado                        (vazio)
404         produto composto não encontrado       { "status": "404", "error": "Not Found" }
422         erro ao atualizar                     ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao atualizar:

::

  {
    "name": [
      "já está em uso"
    ]
  }

Excluir
=======

::

  DELETE /api/v1/compound_products/[id]

Parâmetros de URL:
------------------

=========  ======================  ===========
parâmetro  descrição               obrigatório
=========  ======================  ===========
id         id do produto composto  sim
=========  ======================  ===========

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
404         produto composto não encontrado       { "status": "404", "error": "Not Found" }
==========  ====================================  ====================================================
