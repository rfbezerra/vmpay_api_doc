########
Produtos
########

Listar
======

::

  GET /api/v1/products

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
      "id": 163,
      "created_at": "2014-10-17T14:50:15.000-03:00",
      "updated_at": "2014-10-17T14:50:15.000-03:00",
      "type": "Product",
      "manufacturer_id": 56,
      "category_id": 23,
      "name": "Ruffles 50 g",
      "upc_code": "91",
      "url": "http://localhost:4000/api/v1/products/163"
    },
    {
      "id": 164,
      "created_at": "2014-10-17T14:50:50.000-03:00",
      "updated_at": "2014-10-17T14:50:50.000-03:00",
      "type": "Product",
      "manufacturer_id": 56,
      "category_id": 23,
      "name": "Doritos 55 g",
      "upc_code": "110",
      "url": "http://localhost:4000/api/v1/products/164"
    },
    {
      "id": 165,
      "created_at": "2014-10-17T14:51:30.000-03:00",
      "updated_at": "2014-10-17T14:51:30.000-03:00",
      "type": "Product",
      "manufacturer_id": 56,
      "category_id": 23,
      "name": "Torcida Queijo 50 g",
      "upc_code": "93",
      "url": "http://localhost:4000/api/v1/products/165"
    }
  ]

Ver
===

::

  GET /api/v1/products/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do produto    sim
=========  ===============  ===========

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo::

  {
    "id": 163,
    "created_at": "2014-10-17T14:50:15.000-03:00",
    "updated_at": "2014-10-17T14:50:15.000-03:00",
    "type": "Product",
    "manufacturer_id": 56,
    "category_id": 23,
    "name": "Ruffles 50 g",
    "upc_code": "91",
    "url": "http://localhost:4000/api/v1/products/163"
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

  POST /api/v1/products

Request::

  {
    "product": {
      "type": "Product",
      "name": "Schweppes Citrus",
      "manufacturer_id": 56,
      "category_id": 21,
      "upc_code": 111
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *product*

  * *name*: nome do produto.
  * *manufacturer_id*: id do fabricante.
  * *category_id*: id da categoria.

Opcionais
^^^^^^^^^

* *product*

  * *upc_code*: código do produto.

Retorno
-------

======  ==================
status  descrição
======  ==================
201     Criado com sucesso
======  ==================

Exemplo::

  {
    "id": 2830,
    "created_at": "2016-02-16T10:20:11.018-02:00",
    "updated_at": "2016-02-16T10:20:11.018-02:00",
    "type": "Product",
    "manufacturer_id": 56,
    "category_id": 21,
    "name": "Schweppes Citrus",
    "upc_code": "111",
    "url": "http://localhost:4000/api/v1/products/2830"
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

  PATCH /api/v1/products/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do produto    sim
=========  ===============  ===========

Request::

  {
    "product": {
      "name": "Schweppes Guaraná"
    }
  }

Campos
------

Ao menos um campo interno a *product* deve ser passado.

Retorno
-------

======  ======================
status  descrição
======  ======================
200     Atualizado com sucesso
======  ======================

Exemplo::

  {
    "id": 2830,
    "created_at": "2016-02-16T10:20:11.000-02:00",
    "updated_at": "2016-02-16T10:27:07.000-02:00",
    "type": "Product",
    "manufacturer_id": 56,
    "category_id": 21,
    "name": "Schweppes Guaraná",
    "upc_code": "111",
    "url": "http://localhost:4000/api/v1/products/2830"
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
    "name": [
      "não pode ficar em branco"
    ]
  }

Excluir
=======

::

  DELETE /api/v1/products/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do produto    sim
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

API obsoleta
============

A API abaixo tornou-se obsoleta em favor de uma API mais simples, documentada acima. A API abaixo ainda funciona, mas o seu uso é desencorajado.

Listar (obsoleto)
-----------------

::

    GET /api/v1/vendibles

Ver (obsoleto)
--------------

::

    GET /api/v1/vendibles/[id]

Criar (obsoleto)
----------------

::

    POST /api/v1/vendibles

Request::

    {
      "vendible": {
        "type": "Product",
        "name": "Vanilla Coke",
        "manufacturer_id": 56,
        "category_id": 21,
        "upc_code": 111
      }
    }

Campos
^^^^^^

Obrigatórios
^^^^^^^^^^^^

* *vendible*

  * *name*: nome do produto.
  * *type*: valor deve ser sempre *Product*.
  * *manufacturer_id*: id do fabricante.
  * *category_id*: id da categoria.

Opcionais
^^^^^^^^^

* *vendible*

  * *upc_code*: código do produto.

Atualizar (obsoleto)
--------------------

::

    PATCH /api/v1/vendibles/[id]

Request::

    {
      "vendible": {
        "name": "New Vanilla Coke",
        "manufacturer_id": 521
      }
    }

Campos
^^^^^^

Ao menos um campo interno a *vendible* deve ser passado.

O parâmetro *type* é ignorado.

Excluir (obsoleto)
------------------

::

    DELETE /api/v1/vendibles/[id]
