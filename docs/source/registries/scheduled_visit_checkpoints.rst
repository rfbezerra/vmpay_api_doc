###########
Checkpoints
###########

Ver
===

::

  GET /api/v1/scheduled_visit_checkpoints/[id]

Parâmetros de URL:
------------------

==========  ================  ===========
parâmetro   descrição         obrigatório
==========  ================  ===========
id          id do checkpoint  sim
==========  ================  ===========

Retorno
-------

É retornado um `JSON <https://en.wikipedia.org/wiki/JSON>`_ com os seguintes
campos:

* **id**: o id do checkpoint

* **scheduled_visit_id**: a data em que o checkpoint foi criado

* **created_at**: a data de criação do checkpoint

* **updated_at**: a data de atualização do checkpoint

* **restock**: se é um reabastecimento

* **finished**: se está finalizado

* **finished_at**: a data em que o checkpoint foi finalizado

* **reopened_at**: a data em que o checkpoint foi reaberto

* **installation_id**: o id da instalação

* **planogram_id**: o id do planograma

* **pick_list_id**: o id da pick list

* **synched_at**: a data em que o checkpoint foi sincronizado com o VMpay
  Visitor

* **scheduled_at**: a data em que o agendamento foi efetuado

* **inventories**: lista de inventários em que cada elemento contém os seguintes
  campos:

  - **planogram_item_id**: o id do item do planograma

  - **capacity**: capacidade do item do planograma

  - **expected_vacant_amount**: saldo esperado para o item

  - **entered_vacant_amount**: saldo informado para o item no VMpay Visitor

  - **returned_amounts**: um array com até 4 elementos contendo os valores
    retornados na seguinte ordem: "Retirado: danificado", "Retirado: vencido",
    "Sobra: troca de grade" e "Sobra: pick list".

* **custom_values**: lista de campos customizados em que cada elemento contém os
  seguintes campos:

  - **field**: dados do campo customizado:

    + **name**: nome do campo

    + **label**: rótulo do campo

    + **field_type**: tipo do campo

    + **required**: se o campo é obrigatório

  - **field_value**: valor preenchido no VMpay Visitor

Exemplo:

::

  {
    "id": 21013,
    "scheduled_visit_id": 4744,
    "created_at": "2016-12-21T07:56:05.000-02:00",
    "updated_at": "2016-12-21T10:16:01.000-02:00",
    "restock": true,
    "cash_collect": false,
    "finished": true,
    "finished_at": "2016-12-21T16:39:20.000-02:00",
    "reopened_at": null,
    "installation_id": 1896,
    "planogram_id": 11204,
    "pick_list_id": 63089,
    "synched_at": "2016-12-22T08:05:33.000-02:00",
    "scheduled_at": "2016-12-21T10:16:01.000-02:00",
    "inventories": [
      {
        "planogram_item_id": 385102,
        "capacity": 10.0,
        "expected_vacant_amount": 6.0,
        "entered_vacant_amount": 7.0,
        "returned_amounts": [0.0, 0.0, 0.0, 4.0]
      },
      {
        "planogram_item_id": 385103,
        "capacity": 10.0,
        "expected_vacant_amount": 0.0,
        "entered_vacant_amount": 0.0,
        "returned_amounts": []
      },
      {
        "planogram_item_id": 385104,
        "capacity": 13.0,
        "expected_vacant_amount": 5.0,
        "entered_vacant_amount": 2.0,
        "returned_amounts": [1.0]
      },
      {
        "planogram_item_id": 385105,
        "capacity": 10.0,
        "expected_vacant_amount": 0.0,
        "entered_vacant_amount": 8.0,
        "returned_amounts": [1.0, 1.0, 0.0, 1.0]
      }
    ],
    "custom_values": [
      {
        "field": {
          "name": "limpeza",
          "label": "Limpeza?",
          "field_type": "boolean",
          "required": true
        },
        "field_value": {
          "value": true
        }
      },
      {
        "field": {
          "name": "malote",
          "label": "Malote",
          "field_type": "string",
          "required": true
        },
        "field_value": {
          "value": "123"
        }
      }
    ]
  }
