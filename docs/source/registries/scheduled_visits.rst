#################
Visitas agendadas
#################

Listar
======

::

  GET /api/v1/scheduled_visits

Filtros
-------

Os parâmetros abaixo podem ser passados como uma
`query string <https://en.wikipedia.org/wiki/Query_string>`_. Datas devem ser
passadas no formato *yyyy-mm-dd*.

Este serviço suporta `paginação <../overview.html#paginacao>`_.

* **start_date**: filtra visitas agendadas *a partir* da data informada.

* **end_date**: filtra visitas agendadas *até* a data informada.

Retorno
-------

É retornado um `JSON <https://en.wikipedia.org/wiki/JSON>`_ contendo um array.
Cada elemento do array contém os seguintes campos:

* **id**: o id da visita agendada

* **created_at**: a data de criação da visita agendada, no formato
  `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_

* **updated_at**: a data de atualização da visita agendada, no formato
  `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_

* **date**: a data para a qual a visita foi agendada, no formato *yyyy-mm-dd*

* **completed_at**: a data em que a visita foi liberada para o *VMpay Visitor*

* **vacant_amounts_required**: se a visita exige preenchimento de espaços vazios

* **checkpoints**: lista dos checkpoints da visita; cada elemento contém:

  - **id**: o id do `checkpoint <scheduled_visit_checkpoints.html>`_

  - **installation_id**: o id da instalação

  - **restock**: se deve efetuar reabastecimento na visita

  - **cash_collect**: se deve efetuar coleta na visita

Exemplo:

::

  [
    {
      "id": 13080,
      "created_at": "2017-11-23T10:30:50.000-02:00",
      "updated_at": "2017-11-23T10:50:00.000-02:00",
      "date": "2017-11-24",
      "completed_at": null,
      "vacant_amounts_required": true,
      "checkpoints": [
        {
          "id": 84652,
          "installation_id": 1982,
          "restock": false,
          "cash_collect": false
        }
      ]
    },
    {
      "id": 13074,
      "created_at": "2017-11-14T15:33:18.000-02:00",
      "updated_at": "2017-11-16T18:14:21.000-02:00",
      "date": "2017-12-17",
      "completed_at": "2017-11-14T15:56:25.000-02:00",
      "vacant_amounts_required": true,
      "checkpoints": [
        {
          "id": 84638,
          "installation_id": 7690,
          "restock": false,
          "cash_collect": true
        },
        {
          "id": 84639,
          "installation_id": 7688,
          "restock": true,
          "cash_collect": true
        }
      ]
    }
  ]


Ver
===

::

  GET /api/v1/scheduled_visits/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da visita     sim
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
    "id": 13074,
    "created_at": "2017-11-14T15:33:18.000-02:00",
    "updated_at": "2017-11-16T18:14:21.000-02:00",
    "date": "2017-12-17",
    "completed_at": "2017-11-14T15:56:25.000-02:00",
    "vacant_amounts_required": true,
    "checkpoints": [
      {
        "id": 84638,
        "installation_id": 7690,
        "restock": false,
        "cash_collect": true
      },
      {
        "id": 84639,
        "installation_id": 7688,
        "restock": true,
        "cash_collect": true
      }
    ]
  }

Erros
-----

==========  ========================  =========================================
status      descrição                 response body
==========  ========================  =========================================
404         visita não encontrada     { "error": "Registro não encontrado" }
==========  ========================  =========================================

Criar
=====

::

  POST /api/v1/scheduled_visits

Request::

  {
    "scheduled_visit": {
      "vacant_amounts_required": true,
      "date": "2017-12-18",
      "scheduled_visit_routes_attributes": [{
        "route_id": 299
      }],
      "checkpoints_attributes": [{
        "installation_id": 7686,
        "restock": true,
        "cash_collect": false
      }, {
        "installation_id": 7690,
        "restock": false,
        "cash_collect": true
      }, {
        "installation_id": 7688,
        "restock": true,
        "cash_collect": true
      }]
    }
  }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *scheduled_visit*

  * *date*: Data do agendamento.

Opcionais
^^^^^^^^^

* *scheduled_visit*

  * *vacant_amounts_required*: Se exige preenchimento de espaços vazios.

    * Valores permitidos: *true* se exige o preenchimento ou *false* se não
      exige.

* *scheduled_visit_routes_attributes*: Array com atributos das rotas associadas

  * *route_id*: Id da rota associada ao agendamento

* *scheduled_visit_checkpoints*: Array com atributos dos checkpoints associados
  ao agnedamento

  * *installation_id*: Id da instalação
  * *restock*: Se deve efetuar o reabastecimento na visita

    * Valores permitidos: *true* para efetuar o reabastecimento ou *false* se
      não.

  * *cash_collect*: Se deve efetuar a coleta na visita

    * Valores permitidos: *true* para efetuar a coleta ou *false* se não.


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
    "id": 13081,
    "created_at": "2017-11-23T11:01:24.000-02:00",
    "updated_at": "2017-11-23T11:01:24.000-02:00",
    "date": "2017-12-18",
    "completed_at": null,
    "vacant_amounts_required": true,
    "checkpoints": [
      {
        "id": 84653,
        "installation_id": 7686,
        "restock": true,
        "cash_collect": false
      },
      {
        "id": 84654,
        "installation_id": 7690,
        "restock": false,
        "cash_collect": true
      },
      {
        "id": 84655,
        "installation_id": 7688,
        "restock": true,
        "cash_collect": true
      }
    ]
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
==========  ====================================  ====================================================

Atualizar
=========

::

  PATCH /api/v1/scheduled_visits/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da visita     sim
=========  ===============  ===========

Request::

  {
    "scheduled_visit": {
      "vacant_amounts_required": false
    }
  }

Campos
------

Ao menos um campo interno a *scheduled_visit* deve ser passado.

É possível passar valores referentes a rotas (*scheduled_visit_routes_attributes*)
e também aos checkpoints (*checkpoints_attributes*)

Exemplo atualização::

  {
    "scheduled_visit": {
      "id:" 13081,
      "checkpoints_attributes": [{
        "id": 84653,
        "cash_collect": true
      }, {
        "id": 84654,
        "restock": false
      }]
    }
  }

Caso se deseje remover uma rota, deve-se adicionar o atributo *_destroy* com
valor *true* à chamada como no exemplo abaixo:

Exemplo exclusão de rota::

  {
    "scheduled_visit": {
      "id:" 13081,
      "scheduled_visit_routes_attributes": [{
        "id": 4421,
        "_destroy": true
      }]
    }
  }

Da mesma forma, é possível remover checkpoints associados a visita passando o
mesmo atributo *_destroy* aos atributos dos checkpoints

Exemplo exclusão de checkpoint::

  {
    "scheduled_visit": {
      "id:" 13081,
      "checkpoints_attributes": [{
        "id": 84653,
        "_destroy": true
      }]
    }
  }


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
    "id": 13081,
    "created_at": "2017-11-23T11:01:24.000-02:00",
    "updated_at": "2017-11-23T11:01:24.000-02:00",
    "date": "2017-12-18",
    "completed_at": null,
    "vacant_amounts_required": true,
    "checkpoints": [
      {
        "id": 84654,
        "installation_id": 7690,
        "restock": false,
        "cash_collect": true
      },
      {
        "id": 84655,
        "installation_id": 7688,
        "restock": true,
        "cash_collect": true
      }
    ]
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
404         visita não encontrada                 "error": "Registro não encontrado"
422         erro ao atualizar                     ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao atualizar

::

  {
    "error": "Não é possível atualizar uma visita concluída liberada."
  }

Excluir
=======

::

  DELETE /api/v1/scheduled_visits/[id]

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da visita     sim
=========  ===============  ===========

Retorno
-------

======  ====================  =============
status  descrição             response body
======  ====================  =============
204     Excluída com sucesso  (vazio)
======  ====================  =============

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
404         visita não encontrada                 { "error": "Registro não encontrado" }
422         erro ao excluir                       veja exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao excluir

::

  {
    "error": "Não é possível excluir um agendamento já liberado."
  }



Liberar para o *VMpay Visitor*
==============================

::

  PATCH /api/v1/scheduled_visits/[id]/complete

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da visita     sim
=========  ===============  ===========

Retorno
-------

======  ====================  =============
status  descrição             response body
======  ====================  =============
204     Excluído com sucesso  (vazio)
======  ====================  =============

Desfazer liberação
==================

É possível desfazer uma liberação de visita para o *VMpay Visitor* se a
liberação ocorreu no último minuto, caso contrário não é mais possível desfazer
uma liberação.

::

  PATCH /api/v1/scheduled_visits/[id]/undo_complete

Parâmetros de URL:
------------------

=========  ===============  ===========
parâmetro  descrição        obrigatório
=========  ===============  ===========
id         id da visita     sim
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
422         não é possível desfazer a liberação   {vazios}
==========  ====================================  ====================================================
