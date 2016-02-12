##########
Categorias
##########

Listar
======

::

    GET /api/v1/categories

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
      "id": 199,
      "name": "Bebidas"
    },
    {
      "id": 200,
      "name": "Doces"
    },
    {
      "id": 201,
      "name": "Salgados"
    },
    {
      "id": 208,
      "name": "Combo Promocional"
    },
    {
      "id": 235,
      "name": "Barras de Cereal"
    },
    {
      "id": 236,
      "name": "Achocolatados"
    },
    {
      "id": 237,
      "name": "Sucos "
    },
    {
      "id": 238,
      "name": "Água Mineral"
    },
    {
      "id": 239,
      "name": "Higiene e Limpeza"
    },
    {
      "id": 252,
      "name": "Livros"
    },
    {
      "id": 363,
      "name": "Picolés"
    },
    {
      "id": 470,
      "name": "Insumos solúveis"
    },
    {
      "id": 471,
      "name": "Cafés solúveis"
    }
  ]

Ver
===

::

    GET /api/v1/categories/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da categoria  sim
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
    "id": 236,
    "name": "Achocolatados"
  }

Erros
-----

==========  ========================  =========================================
status      resultado                 response body
==========  ========================  =========================================
404         categoria não encontrada  { "status": "404", "error": "Not Found" }
==========  ========================  =========================================

Criar
=====

::

    POST /api/v1/categories

Request::

    {
      "category": {
        "name": "Refrigerantes"
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *category*

  * *name*: nome da categoria.

Opcionais
^^^^^^^^^

Nenhum.

Retorno
-------

======  =========
status  descrição
======  =========
201     Created
======  =========

Exemplo:

::

  {
    "id": 387,
    "name": "oasis"
  }

Erros
-----

==========  ====================================  ====================================================
status      resultado                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
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

    PATCH /api/v1/categories/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da categoria  sim
=========  ===============  ===========

Request::

    {
      "category": {
        "name": "Novo nome"
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *category*

  * *name*: nome da categoria.

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

::

  {
    "id": 385,
    "name": "Novo nome"
  }

Erros
-----

==========  ====================================  ====================================================
status      resultado                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
404         categoria não encontrada              { "status": "404", "error": "Not Found" }
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

    DELETE /api/v1/categories/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da categoria  sim
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
status      resultado                             response body
==========  ====================================  ====================================================
404         categoria não encontrada              { "status": "404", "error": "Not Found" }
==========  ====================================  ====================================================
