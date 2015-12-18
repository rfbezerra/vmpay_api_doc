##########
Clientes
##########

Listar
======

::

    GET /api/v1/clients


Ver
===

::

    GET /api/v1/clients/[id]

Criar
=====

::

    POST /api/v1/clients

Request::

    {
      "client": {
        "name": "Cliente fictício",
        "legal_type": "corporation",
        "corporate_name": "Razão social Ltda.",
        "cnpj": "63271298000194",
        "contact_name": "João Silva",
        "contact_phone": "41-9999-8888",
        "contact_email": "joao@example.org",
        "notes": "observação"
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

*client*

*name*: Nome do cliente.

*legal_type*: Indica o tipo de pessoa. Valores permitidos: *person*
(pessoa física) ou *corporation* (pessoa jurídica).

Opcionais:
^^^^^^^^^^

*corporate_name*: razão social

*cpf*: CPF

*cnpj*: CNPJ

*contact_name*: Nome para contato

*contact_phone*: Telefone para contato

*contact_email*: email para contato

*notes*: Observação

*main_location_id*: id do endereço principal do cliente

Atualizar
=========

::

    PATCH /api/v1/clients/[id]

Request::

    {
      "category": {
        "name": "Refrigerantes"
      }
    }

Campos
------

*category* é obrigatório.

Todos os demais campos são opcionais.

Excluir
=======

::

    DELETE /v1/clients/[id]
