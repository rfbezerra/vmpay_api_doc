######
Locais
######

Listar
======

::

  GET /api/v1/locations

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
      "id": 28,
      "client_id": 21,
      "name": "Lorem Ipsum",
      "phone": "41-3114-7080",
      "street": "Rodovia BR-277",
      "number": "1",
      "complement": null,
      "neighborhood": "São Sebastião",
      "city": "São José dos Pinhais",
      "state": "PR",
      "zip_code": "696969"
    },
    {
      "id": 34,
      "client_id": 24,
      "name": "Dolor sit",
      "phone": "41-31147080",
      "street": "Rua Engenheiro João Bley Filho",
      "number": "560",
      "complement": "Barracão 04 Fundos",
      "neighborhood": "Pinheirinho",
      "city": "Curitiba",
      "state": "PR",
      "zip_code": "81870370"
    },
    {
      "id": 36,
      "client_id": 25,
      "name": "amet consectetur",
      "phone": "41-3315-1986",
      "street": "Rua Alferes Angelo Sampaio",
      "number": "1896",
      "complement": null,
      "neighborhood": "Batel",
      "city": "Curitiba",
      "state": "PR",
      "zip_code": "80420160"
    }
  ]

Ver
===

::

  GET /api/v1/locations/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do local      sim
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
    "id": 28,
    "client_id": 21,
    "name": "Lorem Ipsum",
    "phone": "41-3114-7080",
    "street": "Rodovia BR-277",
    "number": "1",
    "complement": null,
    "neighborhood": "São Sebastião",
    "city": "São José dos Pinhais",
    "state": "PR",
    "zip_code": "696969"
  }

Erros
-----

==========  ========================  =========================================
status      descrição                 response body
==========  ========================  =========================================
404         local não encontrado      { "status": "404", "error": "Not Found" }
==========  ========================  =========================================

Criar
=====

::

  POST /api/v1/locations

Request::

  {
    "location": {
      "name": "Nome do local",
      "phone": "41-9999-8888",
      "street": "Rua das Flores",
      "number": "123",
      "complement": "loja 1",
      "neighborhood": "Centro",
      "city": "Curitiba",
      "state": "PR",
      "zip_code": "80140110"
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *location*

  * *name*: Nome do local.
  * *state*: Sigla de uma das UF do Brasil, em letras maiúsculas. Ex.: "PR".

Opcionais
^^^^^^^^^

* *location*

  * *client_id*: id do cliente do qual esse local faz parte.
  * *phone*: telefone.
  * *street*: logradouro.
  * *number*: número.
  * *complement*: complemento.
  * *neighborhood*: bairro.
  * *city*: cidade.
  * *zip_code*: CEP.

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
    "id": 1393,
    "client_id": null,
    "name": "Nome do local",
    "phone": "41-9999-8888",
    "street": "Rua das Flores",
    "number": "123",
    "complement": "loja 1",
    "neighborhood": "Centro",
    "city": "Curitiba",
    "state": "PR",
    "zip_code": "80140110"
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

  PATCH /api/v1/locations/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do local      sim
=========  ===============  ===========

Request::

    {
      "location": {
        "name": "Novo nome"
      }
    }

Campos
------

Ao menos um campo interno a *location* deve ser passado.

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
    "id": 28,
    "client_id": 21,
    "name": "Novo nome",
    "phone": "41-3114-7080",
    "street": "Rodovia BR-277",
    "number": "1",
    "complement": null,
    "neighborhood": "São Sebastião",
    "city": "São José dos Pinhais",
    "state": "PR",
    "zip_code": "696969"
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
401         não autorizado                        (vazio)
404         local não encontrado                  { "status": "404", "error": "Not Found" }
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

  DELETE /api/v1/locations/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do local      sim
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
404         local não encontrado                  { "status": "404", "error": "Not Found" }
==========  ====================================  ====================================================
