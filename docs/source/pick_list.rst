##########
Pick lists
##########

Listar
======

Lista os pick lists de determinada máquina e instalação.

::

    GET /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists

Ver
===

Mostra determinado pick list de uma máquina e instalação.

::

    GET /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists/[id]

Criar
=====

Cria uma novo pick list em determinada máquina e instalação.

O pick list criado fica pendente e pode ser atualizado. O mesmo só entra em atividade no próximo reabastecimento da máquina.

Uma instalação pode ter somente um pick list pendente. Se houver uma tentativa de cadastro de um outro pick list, será retornado um erro de validação, código HTTP 422.

Deve-se indicar o planograma da instalação ao qual o pick list se aplica. O planograma deve ser o atual da máquina ou o pendente a entrar no próximo reabastecimento. Se houver uma tentativa de cadastro de um pick list relacionado a um planograma inativo, será retornado um erro de validação, código HTTP 422.

Caso algum item do planograma não faça parte do reabastecimento correspondente, não há a necessidade de indicá-lo com a quantidade zerada no pick list; o mesmo pode ser omitido.

::

    POST /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists

Request::

    {
      "pick_list": {
        "planogram_id": 7533,
        "items_attributes": [
          {
            "planogram_item_id": 16781,
            "quantity": 4
          },
          {
            "planogram_item_id": 16782,
            "quantity": 9
          },
          {
            "planogram_item_id": 16784,
            "quantity": 8
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

Atualizar
=========

Atualiza um pick list de determinada máquina e instalação.

Somente pick lists pendentes podem ser atualizados. Se houver uma tentativa de atualização de um pick list já utilizado em algum reabastecimento, será retornado um erro de validação, código HTTP 422.

Os items podem ser criados, atualizados ou excluídos. Os items omitidos não são alterados.

::

    PATCH /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists/[id]

Request::

    {
      "pick_list": {
        "items_attributes": [
          {
            "id": 3680,
            "_destroy": true
          },
          {
            "id": 3681,
            "quantity": 8
          },
          {
            "planogram_item_id": 16785,
            "quantity": 8
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

Excluir
=======

Exclui um pick list de determinada máquina e instalação.

Somente pick lists pendentes podem ser excluídos. Se houver uma tentativa de exclusão de um pick list já utilizado em algum reabastecimento, será retornado um erro de validação, código HTTP 422.

::

    DELETE /api/v1/machines/[machine_id]/installations/[installation_id]/pick_lists/[id]
