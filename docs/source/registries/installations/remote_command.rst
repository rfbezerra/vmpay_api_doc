################
Comandos remotos
################

Listar
======

Lista os últimos 10 comandos remotos de determinada máquina e instalação.

::

  GET /api/v1/machines/[machine_id]/installations/[installation_id]/remote_commands

Parâmetros de URL:
------------------

===============  ================  ===========
parâmetro        descrição         obrigatório
===============  ================  ===========
machine_id       id da máquina     sim
installation_id  id da instalação  sim
===============  ================  ===========

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
      "id": 6127,
      "created_at": "2016-07-22T13:42:51.000-03:00",
      "kind": "audit",
      "user_input": null,
      "status": "success"
    },
    {
      "id": 5117,
      "created_at": "2016-06-27T15:44:16.000-03:00",
      "kind": "audit",
      "user_input": null,
      "status": "success"
    },
    {
      "id": 5038,
      "created_at": "2016-06-24T15:48:45.000-03:00",
      "kind": "credit",
      "user_input": 10.0,
      "status": "success"
    },
    {
      "id": 4970,
      "created_at": "2016-06-23T15:01:10.000-03:00",
      "kind": "restart_vm",
      "user_input": null,
      "status": "success"
    },
    {
      "id": 4629,
      "created_at": "2016-06-15T15:31:52.000-03:00",
      "kind": "audit",
      "user_input": null,
      "status": "error"
    },
    {
      "id": 4535,
      "created_at": "2016-06-13T14:55:38.000-03:00",
      "kind": "audit",
      "user_input": null,
      "status": "success"
    },
    {
      "id": 4385,
      "created_at": "2016-06-08T16:09:28.000-03:00",
      "kind": "restart_vm",
      "user_input": null,
      "status": "success"
    },
    {
      "id": 4313,
      "created_at": "2016-06-06T10:03:50.000-03:00",
      "kind": "audit",
      "user_input": null,
      "status": "success"
    },
    {
      "id": 4312,
      "created_at": "2016-06-06T09:51:27.000-03:00",
      "kind": "audit",
      "user_input": null,
      "status": "success"
    },
    {
      "id": 4311,
      "created_at": "2016-06-06T09:49:56.000-03:00",
      "kind": "audit",
      "user_input": null,
      "status": "error"
    }
  ]

Ver
===

Mostra determinado comando remoto enviado a uma máquina e instalação.

::

  GET /api/v1/machines/[machine_id]/installations/[installation_id]/remote_commands/[id]

Parâmetros de URL:
------------------

===============  ====================  ===========
parâmetro        descrição             obrigatório
===============  ====================  ===========
machine_id       id da máquina         sim
installation_id  id da instalação      sim
id               id do comando remoto  sim
===============  ====================  ===========

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo::

  {
    "id": 4312,
    "created_at": "2016-07-28T010:34:31.000-03:00",
    "kind": "audit",
    "user_input": null,
    "status": "success"
  }

Campos
------

  * *id*: id do comando.
  * *created_at*: data de criação do comando.
  * *kind*: tipo do comando.

    * Valores permitidos: *audit* (Auditar), *restart_vm* (Reiniciar) ou *credit* (Dar crédito).

  * *user_input*: parâmetros do comando. Atualmente só é utilizado se o *kind* for *credit*. Nesse caso, indica o valor o crédito concedido.
  * *status*: o estado do comando. Pode ser: *in_queue* (aguardando execução na fila), *success* ( executado com sucesso) ou *error* (executado com erro).

Erros
-----

======  ================================================  =========================================
status  descrição                                         response body
======  ================================================  =========================================
404     máquina/instalação/comando remoto não encontrado  { "status": "404", "error": "Not Found" }
======  ================================================  =========================================

Criar
=====

Envia um comando para execução remota.

::

  POST /api/v1/machines/[machine_id]/installations/[installation_id]/remote_command

Parâmetros de URL:
------------------

===============  ================  ===========
parâmetro        descrição         obrigatório
===============  ================  ===========
machine_id       id da máquina     sim
installation_id  id da instalação  sim
===============  ================  ===========

Request::

  {
    "remote_command": {
      "kind": "credit",
      "user_input": 5.0
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *remote_command*

  * *kind*: tipo do comando.

    * Valores permitidos: *audit* (Auditar), *restart_vm* (Reiniciar) ou *credit* (Dar crédito).

  * *user_input*: parâmetros do comando. Atualmente só é obrigatório se o *kind* for *credit*. Nesse caso, indica o valor o crédito concedido.

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
    "id": 7890,
    "created_at": "2016-06-06T09:51:27.000-03:00",
    "kind": "credit",
    "user_input": 5.0
    "status":"in_queue"
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
404         máquina/instalação não encontrada     { "status": "404", "error": "Not Found" }
422         erro ao criar                         ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao criar

::

  {
    "kind": [
      "não pode ficar em branco"
    ]
  }
