##########
Pick lists
##########

Listar
======

Lista os pick lists de determinada máquina e instalação.

::

  GET /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists

Parâmetros de URL:
------------------

===============  ================  ===========
parâmetro        descrição         obrigatório
===============  ================  ===========
machine_id       id da máquina     sim
installation_id  id da instalação  sim
===============  ================  ===========

É possível filtrar as pick lists com uma *query string*. Veja na API do
`relatório de pick lists <../../reports/pick_list.html>`_ os campos possíveis.

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
      "id": 4164,
      "created_at": "2015-11-09T07:49:34.000-02:00",
      "updated_at": "2015-11-09T12:40:13.000-02:00",
      "installation_id": 857,
      "planogram_id": 2477,
      "group_id": 1,
      "distribution_center_id": 1,
      "machine_id": 49
      "pending": false,
      "url": "http://vmpay.vertitecnologia.com.br/api/v1/machines/49/installations/857/pick_lists/4164"
    },
    {
      "id": 4302,
      "created_at": "2015-11-12T12:51:04.000-02:00",
      "updated_at": "2015-11-12T15:46:32.000-02:00",
      "installation_id": 857,
      "planogram_id": 2563,
      "group_id": 1,
      "distribution_center_id": 1,
      "machine_id": 49
      "pending": false,
      "url": "http://vmpay.vertitecnologia.com.br/api/v1/machines/49/installations/857/pick_lists/4302"
    }
  ]

Ver
===

Mostra determinado pick list de uma máquina e instalação.

::

  GET /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists/[id]

Parâmetros de URL:
------------------

===============  ================  ===========
parâmetro        descrição         obrigatório
===============  ================  ===========
machine_id       id da máquina     sim
installation_id  id da instalação  sim
id               id da pick list   sim
===============  ================  ===========

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

Exemplo::

  {
    "id": 4164,
    "created_at": "2015-11-09T07:49:34.000-02:00",
    "updated_at": "2015-11-09T12:40:13.000-02:00",
    "planogram_id": 2477,
    "group_id": 1,
    "distribution_center_id": 1,
    "pending": false,
    "items": [
      {
        "id": 167188,
        "planogram_item_id": 93477,
        "quantity": 8,
        "ignored": false,
        "good_id": 2229
      },
      {
        "id": 167190,
        "planogram_item_id": 93479,
        "quantity": 3,
        "ignored": false,
        "good_id": 543
      },
      {
        "id": 167191,
        "planogram_item_id": 93480,
        "quantity": 3,
        "ignored": false,
        "good_id": 533
      },
      {
        "id": 167192,
        "planogram_item_id": 93481,
        "quantity": 2,
        "ignored": false,
        "good_id": 533
      }
    ]
  }

Erros
-----

======  ===========================================  =========================================
status  descrição                                    response body
======  ===========================================  =========================================
404     máquina/instalação/pick list não encontrada  { "status": "404", "error": "Not Found" }
======  ===========================================  =========================================


Criar
=====

Cria uma novo pick list em determinada máquina e instalação.

O pick list criado fica pendente e pode ser atualizado. O mesmo só entra em atividade no próximo reabastecimento da máquina.

Uma instalação pode ter somente um pick list pendente. Se houver uma tentativa de cadastro de um outro pick list, será retornado um erro de validação, código HTTP 422.

Deve-se indicar o planograma da instalação ao qual o pick list se aplica. O planograma deve ser o atual da máquina ou o pendente a entrar no próximo reabastecimento. Se houver uma tentativa de cadastro de um pick list relacionado a um planograma inativo, será retornado um erro de validação, código HTTP 422.

Caso algum item do planograma não faça parte do reabastecimento correspondente, não há a necessidade de indicá-lo com a quantidade zerada no pick list; o mesmo pode ser omitido.

::

  POST /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists

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
    "pick_list": {
      "planogram_id": 2563,
      "items_attributes": [
        {
          "planogram_item_id": 96633,
          "quantity": 4
        },
        {
          "planogram_item_id": 96632,
          "quantity": 9
        }
      ]
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *pick_list*

  * *planogram_id*: o id do planograma. Deve estar ativo ou pedente.
  * *items_attributes*: um array contendo os items do pick list.

    * *planogram_item_id*: o id do item de planograma correspondente.
    * *quantity*: a quantidade a ser reabastecida.

Opcionais
^^^^^^^^^

Nenhum.

Retorno
-------

======  ==================
status  descrição
======  ==================
201     Criado com sucesso
======  ==================

Exemplo::

  {
    "id": 4794,
    "created_at": "2016-02-16T15:22:26.519-02:00",
    "updated_at": "2016-02-16T15:22:26.519-02:00",
    "planogram_id": 2563,
    "pending": true,
    "items": [
      {
        "id": 191350,
        "planogram_item_id": 96633,
        "quantity": 4
      },
      {
        "id": 191351,
        "planogram_item_id": 96632,
        "quantity": 9
      }
    ]
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
    "base": [
      "Já existe um pick list cadastrado para o próximo reabastecimento"
    ]
  }


Atualizar
=========

Atualiza um pick list de determinada máquina e instalação.

Somente pick lists pendentes podem ser atualizados. Se houver uma tentativa de atualização de um pick list já utilizado em algum reabastecimento, será retornado um erro de validação, código HTTP 422.

Os items podem ser criados, atualizados ou excluídos. Os items omitidos não são alterados.

::

  PATCH /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists/[id]

Parâmetros de URL:
------------------

===============  ================  ===========
parâmetro        descrição         obrigatório
===============  ================  ===========
machine_id       id da máquina     sim
installation_id  id da instalação  sim
id               id da pick list   sim
===============  ================  ===========

Request::

  {
    "pick_list": {
      "items_attributes": [
        {
          "id": 191350,
          "quantity": 11
        },
        {
          "id": 191351,
          "quantity": 12
        }
      ]
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *pick_list*

  * *items_attributes*: um array contendo os items do pick list.

    * *id*: o id do item a ser atualizado ou excluído. Se omitido, considera-se como um item sendo inserido.
    * *planogram_item_id*: o id do item de planograma correspondente. Somente necessário na inserção de um novo item.
    * *quantity*: a quantidade a ser reabastecida.
    * *_destroy*: parâmetro passado para excluir o item do pick list. Para tanto, valor deve ser *true*.

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

Exemplo:

::

  {
    "id": 4794,
    "created_at": "2016-02-16T15:22:26.000-02:00",
    "updated_at": "2016-02-16T15:22:26.000-02:00",
    "planogram_id": 2563,
    "pending": true,
    "items": [
      {
        "id": 191350,
        "planogram_item_id": 96633,
        "quantity": 11
      },
      {
        "id": 191351,
        "planogram_item_id": 96632,
        "quantity": 12
      }
    ]
  }

Erros
-----

==========  ===========================================  =============================================
status      descrição                                    response body
==========  ===========================================  =============================================
400         parâmetros faltando                          { "status": "400", "error": "Bad Request" }
401         não autorizado                               (vazio)
404         máquina/instalação/pick list não encontrada  { "status": "404", "error": "Not Found" }
422         erro ao atualizar                            ver exemplo abaixo
==========  ===========================================  =============================================

422 - erro ao atualizar:

::

  {
    "base": "Pick list deve estar pendente"
  }

Excluir
=======

Exclui um pick list de determinada máquina e instalação.

Somente pick lists pendentes podem ser excluídos. Se houver uma tentativa de exclusão de um pick list já utilizado em algum reabastecimento, será retornado um erro de validação, código HTTP 422.

::

  DELETE /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists/[id]

Parâmetros de URL:
------------------

===============  ================  ===========
parâmetro        descrição         obrigatório
===============  ================  ===========
machine_id       id da máquina     sim
installation_id  id da instalação  sim
id               id da pick list   sim
===============  ================  ===========

Retorno
-------

======  ====================  =============
status  descrição             response body
======  ====================  =============
204     Excluído com sucesso  (vazio)
======  ====================  =============


Erros
-----

==========  ===========================================  =============================================
status      descrição                                    response body
==========  ===========================================  =============================================
404         máquina/instalação/pick list não encontrada  { "status": "404", "error": "Not Found" }
==========  ===========================================  =============================================
