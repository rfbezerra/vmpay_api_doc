######
Locais
######

Listar
======

::

    GET /api/v1/locations

Ver
===

::

    GET /api/v1/locations/[id]

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

Atualizar
=========

::

    PATCH /api/v1/locations/[id]

Request::

    {
      "location": {
        "name": "Matriz"
      }
    }

Campos
------

Ao menos um campo interno a *location* deve ser passado.

Excluir
=======

::

    DELETE /api/v1/locations/[id]
