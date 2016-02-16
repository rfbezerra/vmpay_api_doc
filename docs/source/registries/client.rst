########
Clientes
########

Listar
======

::

    GET /api/v1/clients

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
      "id": 21,
      "name": "Verti Tecnologia",
      "corporate_name": "VERTI TECNOLOGIA COMERCIO E LOCACAO DE EQUIPAMENTOS LTDA - ME",
      "cpf": null,
      "cnpj": "09.019.291/0001-34",
      "contact_name": "Luiz Alberto Schwab Jr.",
      "contact_phone": "41-9876-5432",
      "contact_email": "luiz@vertitecnologia.com.br",
      "notes": null,
      "legal_type": "corporation",
      "main_location_id": 28
    },
    {
      "id": 24,
      "name": "Pão de Açúcar",
      "corporate_name": "Cia. Brasileira de Distribuição",
      "cpf": null,
      "cnpj": "047508411000156",
      "contact_name": "João Silva",
      "contact_phone": "11-98765-4321",
      "contact_email": "joao@grupopaodeacucar.com.br",
      "notes": null,
      "legal_type": "corporation",
      "main_location_id": 34
    }
  ]

Ver
===

::

    GET /api/v1/clients/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do cliente    sim
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
    "id": 21,
    "name": "Verti Tecnologia",
    "corporate_name": "VERTI TECNOLOGIA COMERCIO E LOCACAO DE EQUIPAMENTOS LTDA - ME",
    "cpf": null,
    "cnpj": "09.019.291/0001-34",
    "contact_name": "Luiz Alberto Schwab Jr.",
    "contact_phone": "41-9876-5432",
    "contact_email": "luiz@vertitecnologia.com.br",
    "notes": null,
    "legal_type": "corporation",
    "main_location_id": 28
  }

Erros
-----

==========  ========================  =========================================
status      descrição                 response body
==========  ========================  =========================================
404         cliente não encontrado    { "status": "404", "error": "Not Found" }
==========  ========================  =========================================

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

* *client*

  * *name*: nome do cliente.
  * *legal_type*: indica o tipo de pessoa.

    * Valores permitidos: *person* (pessoa física) ou *corporation* (pessoa jurídica).

  * *cpf*: CPF (obrigatório apenas quando for pessoa física).
  * *cnpj*: CNPJ (obrigatório apenas quando for pessoa jurídica).

Opcionais
^^^^^^^^^

* *client*

  * *corporate_name*: razão social.
  * *contact_name*: Nome para contato.
  * *contact_phone*: Telefone para contato.
  * *contact_email*: email para contato.
  * *notes*: Observação.
  * *main_location_id*: id do endereço principal do cliente.

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
    "id": 1187,
    "name": "Novo Cliente",
    "corporate_name": null,
    "cpf": null,
    "cnpj": "54173174000185",
    "contact_name": null,
    "contact_phone": null,
    "contact_email": null,
    "notes": null,
    "legal_type": "corporation",
    "main_location_id": null
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
    "cnpj": [
      "não pode ficar em branco"
    ]
  }

Atualizar
=========

::

    PATCH /api/v1/clients/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do cliente    sim
=========  ===============  ===========

Request::

  {
    "client": {
      "name": "Novo nome"
    }
  }

Campos
------

Ao menos um campo interno a *client* deve ser passado.

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
    "id": 1186,
    "name": "Novo nome",
    "corporate_name": null,
    "cpf": null,
    "cnpj": "54173174000185",
    "contact_name": null,
    "contact_phone": null,
    "contact_email": null,
    "notes": null,
    "legal_type": "corporation",
    "main_location_id": null
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
404         cliente não encontrado                { "status": "404", "error": "Not Found" }
422         erro ao atualizar                     ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao atualizar

::

  {
    "name": [
      "é muito longo (máximo: 255 caracteres)"
    ]
  }

Excluir
=======

::

    DELETE /api/v1/clients/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id do cliente    sim
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
404         cliente não encontrado                { "status": "404", "error": "Not Found" }
==========  ====================================  ====================================================
