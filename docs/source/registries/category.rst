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
status      descrição                 response body
==========  ========================  =========================================
404         categoria não encontrada  { "status": "404", "error": "Not Found" }
==========  ========================  =========================================
