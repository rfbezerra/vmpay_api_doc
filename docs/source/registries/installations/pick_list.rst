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
      "planogram_id": 2477,
      "pending": false,
      "url": "http://localhost:4000/api/v1/machines/49/installations/857/pick_lists/4164",
      "items": [
        {
          "id": 167188,
          "planogram_item_id": 93477,
          "quantity": 8
        },
        {
          "id": 167190,
          "planogram_item_id": 93479,
          "quantity": 3
        },
        {
          "id": 167191,
          "planogram_item_id": 93480,
          "quantity": 3
        },
        {
          "id": 167192,
          "planogram_item_id": 93481,
          "quantity": 2
        },
        {
          "id": 167193,
          "planogram_item_id": 93482,
          "quantity": 1
        },
        {
          "id": 167194,
          "planogram_item_id": 93483,
          "quantity": 1
        },
        {
          "id": 167195,
          "planogram_item_id": 93484,
          "quantity": 3
        },
        {
          "id": 167196,
          "planogram_item_id": 93485,
          "quantity": 4
        },
        {
          "id": 167197,
          "planogram_item_id": 93486,
          "quantity": 4
        },
        {
          "id": 167199,
          "planogram_item_id": 93488,
          "quantity": 3
        },
        {
          "id": 167200,
          "planogram_item_id": 93489,
          "quantity": 1
        },
        {
          "id": 167201,
          "planogram_item_id": 93490,
          "quantity": 5
        },
        {
          "id": 167202,
          "planogram_item_id": 93491,
          "quantity": 2
        },
        {
          "id": 167203,
          "planogram_item_id": 93492,
          "quantity": 8
        },
        {
          "id": 167204,
          "planogram_item_id": 93493,
          "quantity": 2
        },
        {
          "id": 167205,
          "planogram_item_id": 93494,
          "quantity": 8
        },
        {
          "id": 167206,
          "planogram_item_id": 93495,
          "quantity": 1
        },
        {
          "id": 167207,
          "planogram_item_id": 93496,
          "quantity": 1
        },
        {
          "id": 167208,
          "planogram_item_id": 93497,
          "quantity": 3
        },
        {
          "id": 167209,
          "planogram_item_id": 93498,
          "quantity": 6
        },
        {
          "id": 167210,
          "planogram_item_id": 93499,
          "quantity": 6
        },
        {
          "id": 167211,
          "planogram_item_id": 93500,
          "quantity": 1
        },
        {
          "id": 167212,
          "planogram_item_id": 93501,
          "quantity": 4
        },
        {
          "id": 167213,
          "planogram_item_id": 93502,
          "quantity": 1
        },
        {
          "id": 167214,
          "planogram_item_id": 93503,
          "quantity": 1
        },
        {
          "id": 167216,
          "planogram_item_id": 93505,
          "quantity": 1
        },
        {
          "id": 167218,
          "planogram_item_id": 93507,
          "quantity": 1
        },
        {
          "id": 167219,
          "planogram_item_id": 93508,
          "quantity": 3
        },
        {
          "id": 167220,
          "planogram_item_id": 93509,
          "quantity": 1
        },
        {
          "id": 167221,
          "planogram_item_id": 93510,
          "quantity": 2
        },
        {
          "id": 167222,
          "planogram_item_id": 93511,
          "quantity": 2
        },
        {
          "id": 167224,
          "planogram_item_id": 93513,
          "quantity": 2
        },
        {
          "id": 167225,
          "planogram_item_id": 93514,
          "quantity": 1
        },
        {
          "id": 167226,
          "planogram_item_id": 93515,
          "quantity": 1
        }
      ]
    },
    {
      "id": 4302,
      "created_at": "2015-11-12T12:51:04.000-02:00",
      "updated_at": "2015-11-12T15:46:32.000-02:00",
      "planogram_id": 2563,
      "pending": false,
      "url": "http://localhost:4000/api/v1/machines/49/installations/857/pick_lists/4302",
      "items": [
        {
          "id": 172498,
          "planogram_item_id": 96595,
          "quantity": 2
        },
        {
          "id": 172499,
          "planogram_item_id": 96596,
          "quantity": 3
        },
        {
          "id": 172500,
          "planogram_item_id": 96597,
          "quantity": 1
        },
        {
          "id": 172502,
          "planogram_item_id": 96599,
          "quantity": 1
        },
        {
          "id": 172503,
          "planogram_item_id": 96600,
          "quantity": 1
        },
        {
          "id": 172504,
          "planogram_item_id": 96601,
          "quantity": 4
        },
        {
          "id": 172505,
          "planogram_item_id": 96602,
          "quantity": 1
        },
        {
          "id": 172511,
          "planogram_item_id": 96608,
          "quantity": 1
        },
        {
          "id": 172513,
          "planogram_item_id": 96610,
          "quantity": 4
        },
        {
          "id": 172515,
          "planogram_item_id": 96612,
          "quantity": 1
        },
        {
          "id": 172516,
          "planogram_item_id": 96613,
          "quantity": 2
        },
        {
          "id": 172518,
          "planogram_item_id": 96615,
          "quantity": 3
        },
        {
          "id": 172519,
          "planogram_item_id": 96616,
          "quantity": 2
        },
        {
          "id": 172520,
          "planogram_item_id": 96617,
          "quantity": 4
        },
        {
          "id": 172521,
          "planogram_item_id": 96618,
          "quantity": 2
        },
        {
          "id": 172522,
          "planogram_item_id": 96619,
          "quantity": 2
        },
        {
          "id": 172524,
          "planogram_item_id": 96621,
          "quantity": 1
        },
        {
          "id": 172525,
          "planogram_item_id": 96622,
          "quantity": 2
        },
        {
          "id": 172526,
          "planogram_item_id": 96623,
          "quantity": 2
        },
        {
          "id": 172528,
          "planogram_item_id": 96625,
          "quantity": 1
        },
        {
          "id": 172529,
          "planogram_item_id": 96626,
          "quantity": 2
        },
        {
          "id": 172530,
          "planogram_item_id": 96627,
          "quantity": 1
        },
        {
          "id": 172531,
          "planogram_item_id": 96628,
          "quantity": 2
        },
        {
          "id": 172532,
          "planogram_item_id": 96629,
          "quantity": 4
        },
        {
          "id": 172533,
          "planogram_item_id": 96630,
          "quantity": 4
        },
        {
          "id": 172534,
          "planogram_item_id": 96631,
          "quantity": 1
        },
        {
          "id": 172535,
          "planogram_item_id": 96632,
          "quantity": 3
        },
        {
          "id": 172536,
          "planogram_item_id": 96633,
          "quantity": 3
        }
      ]
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
    "pending": false,
    "items": [
      {
        "id": 167188,
        "planogram_item_id": 93477,
        "quantity": 8
      },
      {
        "id": 167190,
        "planogram_item_id": 93479,
        "quantity": 3
      },
      {
        "id": 167191,
        "planogram_item_id": 93480,
        "quantity": 3
      },
      {
        "id": 167192,
        "planogram_item_id": 93481,
        "quantity": 2
      },
      {
        "id": 167193,
        "planogram_item_id": 93482,
        "quantity": 1
      },
      {
        "id": 167194,
        "planogram_item_id": 93483,
        "quantity": 1
      },
      {
        "id": 167195,
        "planogram_item_id": 93484,
        "quantity": 3
      },
      {
        "id": 167196,
        "planogram_item_id": 93485,
        "quantity": 4
      },
      {
        "id": 167197,
        "planogram_item_id": 93486,
        "quantity": 4
      },
      {
        "id": 167199,
        "planogram_item_id": 93488,
        "quantity": 3
      },
      {
        "id": 167200,
        "planogram_item_id": 93489,
        "quantity": 1
      },
      {
        "id": 167201,
        "planogram_item_id": 93490,
        "quantity": 5
      },
      {
        "id": 167202,
        "planogram_item_id": 93491,
        "quantity": 2
      },
      {
        "id": 167203,
        "planogram_item_id": 93492,
        "quantity": 8
      },
      {
        "id": 167204,
        "planogram_item_id": 93493,
        "quantity": 2
      },
      {
        "id": 167205,
        "planogram_item_id": 93494,
        "quantity": 8
      },
      {
        "id": 167206,
        "planogram_item_id": 93495,
        "quantity": 1
      },
      {
        "id": 167207,
        "planogram_item_id": 93496,
        "quantity": 1
      },
      {
        "id": 167208,
        "planogram_item_id": 93497,
        "quantity": 3
      },
      {
        "id": 167209,
        "planogram_item_id": 93498,
        "quantity": 6
      },
      {
        "id": 167210,
        "planogram_item_id": 93499,
        "quantity": 6
      },
      {
        "id": 167211,
        "planogram_item_id": 93500,
        "quantity": 1
      },
      {
        "id": 167212,
        "planogram_item_id": 93501,
        "quantity": 4
      },
      {
        "id": 167213,
        "planogram_item_id": 93502,
        "quantity": 1
      },
      {
        "id": 167214,
        "planogram_item_id": 93503,
        "quantity": 1
      },
      {
        "id": 167216,
        "planogram_item_id": 93505,
        "quantity": 1
      },
      {
        "id": 167218,
        "planogram_item_id": 93507,
        "quantity": 1
      },
      {
        "id": 167219,
        "planogram_item_id": 93508,
        "quantity": 3
      },
      {
        "id": 167220,
        "planogram_item_id": 93509,
        "quantity": 1
      },
      {
        "id": 167221,
        "planogram_item_id": 93510,
        "quantity": 2
      },
      {
        "id": 167222,
        "planogram_item_id": 93511,
        "quantity": 2
      },
      {
        "id": 167224,
        "planogram_item_id": 93513,
        "quantity": 2
      },
      {
        "id": 167225,
        "planogram_item_id": 93514,
        "quantity": 1
      },
      {
        "id": 167226,
        "planogram_item_id": 93515,
        "quantity": 1
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
