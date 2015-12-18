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
            "name": "Jedi Council",
            "phone": "41-9999-8888",
            "street": "of rage",
            "number": "123",
            "complement": "ap 1",
            "neighborhood": "south central",
            "city": "Los Angeles",
            "state": "PR",
            "zip_code": "90210"
          }
        }



Campos
------

Obrigatórios
^^^^^^^^^^^^

*location*

*name*: Nome do local.

*state*: Sigla de uma das UF do Brasil, em letras maiúsculas. Ex.: PR

Opcionais:
^^^^^^^^^^

*client_id*: id do cliente situado neste endereço

*phone*: telefone

*street*: logradouro

*number*: número

*complement*: complemento

*neighborhood*: bairro

*city*: cidade

*zip_code*: CEP

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

*location* é obrigatório.

Pelo menos um campo deve ser passado para ser atualizado.

Excluir
=======

::

    DELETE /v1/locations/[id]
