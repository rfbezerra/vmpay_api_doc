###########
Instalações
###########

Listar
======

Lista as instalações de determinada máquina.

::

  GET /api/v1/machines/[machine_id]/installations

Parâmetros de URL:
------------------

==========  ===============  ===========
parâmetro   descrição        obrigatório
==========  ===============  ===========
machine_id  id da máquina    sim
==========  ===============  ===========

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
      "id": 77,
      "created_at": "2014-10-17T16:11:43.000-03:00",
      "updated_at": "2014-11-20T10:14:31.000-02:00",
      "location_id": 34,
      "machine_id": 42,
      "equipment_id": 314,
      "place": "Recepção",
      "cash_mode": "cash_and_cashless",
      "restock_mode": "restock_and_cash_collect",
      "restock_strategy": "allow_pick_list_or_full",
      "notifications_enabled": true,
      "audit_enabled": true,
      "visit_schedule": []
    },
    {
      "id": 88,
      "created_at": "2014-10-24T12:25:15.000-02:00",
      "updated_at": "2014-11-20T10:14:31.000-02:00",
      "location_id": 28,
      "machine_id": 42,
      "equipment_id": 314,
      "place": "Hall Biblioteca",
      "cash_mode": "cash_and_cashless",
      "restock_mode": "restock_and_cash_collect",
      "restock_strategy": "allow_pick_list_or_full",
      "notifications_enabled": true,
      "audit_enabled": true,
      "visit_schedule": ["tuesday", "thursday"]
    },
    {
      "id": 138,
      "created_at": "2014-11-21T16:54:19.000-02:00",
      "updated_at": "2014-11-21T19:40:14.000-02:00",
      "location_id": 34,
      "machine_id": 42,
      "equipment_id": 314,
      "place": "Recepção",
      "cash_mode": "cash_and_cashless",
      "restock_mode": "restock_and_cash_collect",
      "restock_strategy": "require_pending_pick_list",
      "notifications_enabled": true,
      "audit_enabled": true,
      "visit_schedule": ["monday", "wednesday", "friday"]
    }
  ]

Ver
===

Mostra determinada instalação de uma máquina.

::

  GET /api/v1/machines/[machine_id]/installations/[id]

Parâmetros de URL:
------------------

==========  ================  ===========
parâmetro   descrição         obrigatório
==========  ================  ===========
machine_id  id da máquina     sim
id          id da instalação  sim
==========  ================  ===========

Retorno
-------

======  =========
status  descrição
======  =========
200     OK
======  =========

* O campo *balance* diz respeito aos saldos da instalação:

  * *total_collectable_coins*: Saldo coletável no cofre.
  * *total_collectable_bills*: Saldo coletável no noteiro.
  * *total_collectable*: Saldo total coletável.
  * *total_in_coin_changer*: Saldo de troco no modeiro.
  * *total_in_bill_changer*: Saldo de troco no reciclador.
  * *total_in_changer*: Saldo total de troco.
  * *total_in_coins*: Saldo total de moedas.
  * *total_in_bills*: Saldo total de notas.
  * *total_in_cash*: Saldo total.

* O campo *current_session* diz respeito ao caixa total:

  * *cashbox*: Cofre.
  * *bill*: Noteiro.
  * *collection*: A coletar.
  * *changer*: Moedeiro.
  * *recycler*: Reciclador.
  * *supplied*: Carga/retirada.
  * *cashless*: Cashless.
  * *total_vends*: Vendas.
  * *difference*: Diferença de caixa.
  * *vends*: Totais de vendas discrimadas por produto.

Segue um exemplo de retorno:

::

    {
      "id": 123987,
      "created_at": "2016-01-26T17:36:44.000-02:00",
      "updated_at": "2016-01-26T19:21:27.000-02:00",
      "location_id": 12,
      "equipment_id": 123,
      "place": "Recepção",
      "cash_mode": "cash_and_cashless",
      "restock_mode": "restock_and_cash_collect",
      "restock_strategy": "allow_pick_list_or_full",
      "notifications_enabled": true,
      "audit_enabled": true,
      "visit_schedule": ["monday", "wednesday", "friday"],
      "pending_planogram": null,
      "current_planogram": {
        "id": 189976,
        "created_at": "2016-01-26T17:36:44.000-02:00",
        "updated_at": "2016-01-26T17:36:44.000-02:00",
        "due": "now",
        "started_at": "2016-01-26T17:36:44.000-02:00",
        "items": [
          {
            "id": 86717,
            "type": "Coil",
            "name": "1,2",
            "good_id": 10,
            "capacity": 20,
            "par_level": 20,
            "alert_level": 4,
            "desired_price": 2.5,
            "logical_locator": 1,
            "current_balance": 11.0
          },
          {
            "id": 86718,
            "type": "Coil",
            "name": "3",
            "good_id": 12,
            "capacity": 10,
            "par_level": 10,
            "alert_level": 2,
            "desired_price": 2.3,
            "logical_locator": 2,
            "current_balance": 8.0
          },
          {
            "id": 86719,
            "type": "VirtualCoil",
            "name": "4",
            "good_id": 23,
            "desired_price": 4.0,
            "logical_locator": 3,
            "children": { "1": 2, "2": 1 }
          },
          {
            "id": 86720,
            "type": "Canister",
            "good_id": 26,
            "capacity": 2000,
            "par_level": 2000,
            "alert_level": 200,
            "logical_locator": 4,
            "current_balance": 983.3
          },
          {
            "id": 86721,
            "type": "Canister",
            "good_id": 27,
            "capacity": 3000,
            "par_level": 3000,
            "alert_level": 300,
            "logical_locator": 5,
            "current_balance": 1975.4
          },
          {
            "id": 86722,
            "type": "VirtualCanister",
            "good_id": 30,
            "name": "5",
            "desired_price": 3.0,
            "logical_locator": 6,
            "children": { "4": 20, "5": 15 }
          }
        ]
      },
      "balance": {
        "total_collectable_coins": 8.7,
        "total_collectable_bills": 132.0,
        "total_collectable": 140.7,
        "total_in_coin_changer": 101.8,
        "total_in_bill_changer": 0.0,
        "total_in_changer": 101.8,
        "total_in_coins": 110.5,
        "total_in_bills": 132.0,
        "total_in_cash": 242.5
      },
      "current_session": {
        "cashbox": 8.7,
        "bill": 132.0,
        "collection": 140.7,
        "changer": -30.95,
        "recycler": 0.0,
        "supplied": 132.75,
        "cashless": 1218.3,
        "total_vends": 1328.05,
        "difference": 0.0,
        "vends": [
          {
            "vendible_id": 12,
            "quantity": 23.0,
            "value": 52.9,
            "vendible": {
              "type": "Product",
              "category_id": 5,
              "manufacturer_id": 3,
              "name": "Coca cola",
              "upc_code": "123"
            }
          },
          {
            "vendible_id": 30,
            "quantity": 19.0,
            "value": 57.0,
            "vendible": {
              "type": "Mixture",
              "category_id": 7,
              "manufacturer_id": null,
              "name": "Cappuccino",
              "upc_code": null
            }
          }
        ]
      }
    }

Erros
-----

==========  ====================================  ================
status      descrição                             response body
==========  ====================================  ================
404         máquina ou instalação não encontrada  (vazio)
==========  ====================================  ================

Criar
=====

Cria uma nova instalação em determinada máquina.

Se a máquina já possuir uma instalação ativa, a mesma é baixada automaticamente na data e hora atuais. A instalação criada torna-se a ativa.

::

  POST /api/v1/machines/[machine_id]/installations

Parâmetros de URL:
------------------

==========  ===============  ===========
parâmetro   descrição        obrigatório
==========  ===============  ===========
machine_id  id da máquina    sim
==========  ===============  ===========

Request::

    {
      "installation": {
        "location_id": 12,
        "equipment_id": 123,
        "place": "Recepção",
        "cash_mode": "cash_and_cashless",
        "restock_mode": "restock_and_cash_collect",
        "restock_strategy": "allow_pick_list_or_full",
        "notifications_enabled": true,
        "audit_enabled": true,
        "visit_schedule": ["monday", "wednesday", "friday"],
        "planograms_attributes": [
          {
            "items_attributes": [
              {
                "type": "Coil",
                "name": "1,2",
                "good_id": 10,
                "capacity": 20,
                "par_level": 20,
                "alert_level": 4,
                "desired_price": 2.5,
                "logical_locator": 1
              },
              {
                "type": "Coil",
                "name": "3",
                "good_id": 12,
                "capacity": 10,
                "par_level": 10,
                "alert_level": 2,
                "desired_price": 2.3,
                "logical_locator": 2
              },
              {
                "type": "VirtualCoil",
                "name": "4",
                "good_id": 23,
                "desired_price": 4.0,
                "logical_locator": 3,
                "children": { "1": 2, "2": 1 }
              },
              {
                "type": "Canister",
                "good_id": 26,
                "capacity": 2000,
                "par_level": 2000,
                "alert_level": 200,
                "logical_locator": 4
              },
              {
                "type": "Canister",
                "good_id": 27,
                "capacity": 3000,
                "par_level": 3000,
                "alert_level": 300,
                "logical_locator": 5
              },
              {
                "type": "VirtualCanister",
                "good_id": 30,
                "name": "5",
                "desired_price": 3.0,
                "logical_locator": 6,
                "children": { "4": 20, "5": 15 }
              }
            ]
          }
        ]
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *installation*

  * *location_id*: id do local.
  * *equipment_id*: id do equipamento.
  * *cash_mode*: modo de pagamento.

    * Valores permitidos: *cash_and_cashless* (dinheiro e cartão), *cashless_only* (somente cartão) ou *cash_only* (somente dinheiro).

  * *restock_mode*: botão de reabastecimento.

    * Valores permitidos: *restock_and_cash_collect* (reabastecimento + coleta) ou *restock_only* (somente reabastecimento).
    * Se o botão de reabastecimento da máquina for pressionado somente uma única vez, o sistema irá gerar um reabastecimento juntamente com uma coleta ou somente um reabastecimento dependendo da opção selecionada.
    * Se o botão for pressionado duas vezes, o sistema sempre irá gerar uma coleta.

  * *restock_strategy*: estratégia de reabastecimento.

    * Valores permitidos: *allow_pick_list_or_full* (padrão) ou *require_pending_pick_list* (somente por pick list).

  * *notifications_enabled*: enviar notificações?
  * *audit_enabled*: habilitar auditorias?
  * *visit_schedule*: array contendo os dias da Agenda de Visitas. Valores permitidos são: *sunday, monday, tuesday, wednesday, thursday, friday, saturday*.

  * *planograms_attributes*: os planogramas da instalação. Nesse caso, somente um planograma é preenchido: o inicial.

    * *items_attributes*: um array contendo os items do planograma.

      * Os items podem ser de 4 tipos: canaletas, combos, canisters e seleções.
      * Canaletas:

        * *type*: deve ser igual a "Coil".
        * *name*: o número da canaleta. Caso se trate de um agrupamento de canaletas, os números devem ser separados por vírgulas.
        * *good_id*: id do produto. Nesse caso não pode ser composto. `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.
        * *capacity*: a capacidade total da canaleta. No caso de agrupameto de canaletas, deve-se colocar aqui a capacidade total, somando-se todas as canaletas.
        * *par_level*: o nível de par da canaleta. No caso de agrupameto de canaletas, deve-se colocar aqui o nível de par total, somando-se todas as canaletas.
        * *alert_level*: o nível de alerta da canaleta.
        * *desired_price*: o preço unitário desejado.
        * *logical_locator*: trata-se do identificador lógico da canaleta. Deve-se gerar um inteiro único dentro de todos os items do planograma.

      * Combos:

        * *type*: deve ser igual a "VirtualCoil".
        * *name*: o número de seleção do combo.
        * *good_id*: id do produto. Nesse caso deve ser composto e com o *type* *Combo*. `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.
        * *desired_price*: o preço unitário desejado.
        * *logical_locator*: trata-se do identificador lógico do combo. Deve-se gerar um inteiro único dentro de todos os items do planograma.
        * *children*: as canaletas e suas quantidades que compõe o combo. É um objeto cujas chaves são identificares lógicos (campo *logical_locator*) das canaletas e os valores as quantidades. No exemplo acima, o combo é composto de 2 produtos da canaleta cujo *name* é "1,2" - ou seja, canaletas 1 e 2 agrupadas - e 1 produto da canaleta 3.

      * Canisters:

        * *type*: deve ser igual a "Canister".
        * *good_id*: id do insumo. `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.
        * *capacity*: a capacidade total do canister. Deve ser preenchido na mesma unidade do insumo (g, ml ou un).
        * *par_level*: o nível de par do canister. Deve ser preenchido na mesma unidade do insumo (g, ml ou un).
        * *alert_level*: o nível de alerta do canister. Deve ser preenchido na mesma unidade do insumo (g, ml ou un).
        * *logical_locator*: trata-se do identificador lógico do canister. Deve-se gerar um inteiro único dentro de todos os items do planograma.

      * Seleções:

        * *type*: deve ser igual a "VirtualCanister".
        * *name*: o número da seleção.
        * *good_id*: id do produto. Nesse caso deve ser composto e com o *type* *Mixture*. `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.
        * *desired_price*: o preço unitário desejado.
        * *logical_locator*: trata-se do identificador lógico da seleção. Deve-se gerar um inteiro único dentro de todos os items do planograma.
        * *children*: os canisters e suas quantidades que compõe a seleção. É um objeto cujas chaves são identificares lógicos (campo *logical_locator*) dos canisters e os valores as quantidades. No exemplo acima, digamos que o insumo de id 26 seja *Café em pó* e o de id 27, *Leite em pó*. Logo, a seleção é composta de 20 gramas de Café em pó e 15 gramas de Leite em pó.

Opcionais
^^^^^^^^^

* *installation*

  * *place*: local interno.

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
    "id": 1109,
    "created_at": "2016-02-15T16:19:36.832-02:00",
    "updated_at": "2016-02-15T16:19:36.832-02:00",
    "location_id": 185,
    "machine_id": 612,
    "equipment_id": 314,
    "place": "Recepção",
    "cash_mode": "cash_and_cashless",
    "restock_mode": "restock_and_cash_collect",
    "restock_strategy": "allow_pick_list_or_full",
    "notifications_enabled": true,
    "audit_enabled": true,
    "visit_schedule": ["monday", "wednesday", "friday"],
    "current_planogram": {
      "id": 2950,
      "created_at": "2016-02-15T16:19:36.841-02:00",
      "updated_at": "2016-02-15T16:19:36.841-02:00",
      "due": "due_now",
      "started_at": "2016-02-15T16:20:36.603-02:00",
      "items": [
        {
          "id": 113835,
          "created_at": "2016-02-15T16:19:36.843-02:00",
          "updated_at": "2016-02-15T16:19:36.843-02:00",
          "planogram_id": 2950,
          "type": "Coil",
          "good_id": 10,
          "name": "1,2",
          "capacity": 20,
          "par_level": 20,
          "alert_level": 4,
          "desired_price": 2.5,
          "modified": false,
          "undefined": false,
          "logical_locator": "1",
          "physical_locators": [
            "1",
            "2"
          ],
          "children": null,
          "current_balance": 20,
          "good": {
            "id": 10,
            "name": "Amendoin",
            "upc_code": "77",
            "upc_code_name": "77 - Amendoin",
            "unit_description": "Unidade",
            "unit_symbol": "un"
          }
        }
      ]
    },
    "balance": {
      "total_collectable_coins": 0,
      "total_collectable_bills": 0,
      "total_collectable": 0,
      "total_in_coin_changer": 0,
      "total_in_bill_changer": 0,
      "total_in_changer": 0,
      "total_in_coins": 0,
      "total_in_bills": 0,
      "total_in_cash": 0
    },
    "current_session": {
      "cashbox": 0,
      "bill": 0,
      "collection": 0,
      "changer": 0,
      "recycler": 0,
      "supplied": 0,
      "cashless": 0,
      "total_vends": 0,
      "difference": 0,
      "vends": []
    }
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
    "location_id": [
      "não pode ficar em branco"
    ]
  }


Atualizar
=========

Atualiza uma instalação de determinada máquina.

::

  PATCH /api/v1/machines/[machine_id]/installations/[id]

Parâmetros de URL:
------------------

==========  ================  ===========
parâmetro   descrição         obrigatório
==========  ================  ===========
machine_id  id da máquina     sim
id          id da instalação  sim
==========  ================  ===========

Request::

  {
    "installation": {
      "location_id": 13,
      "place": "Recepção 2",
      "notifications_enabled": false
    }
  }

Campos
------

Ao menos um campo interno a *installation* deve ser passado.

Somente os parâmetros *location_id*, *place*, *restock_mode*, *restock_strategy*, *notifications_enabled*, *audit_enabled* e *visit_schedule* são considerados; os demais são ignorados.

Não é permitido atualizar um planograma ativo, somente cadastrar um outro planograma pendente. Para tanto, ver Planogramas.

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
    "id": 1119,
    "created_at": "2016-02-15T16:50:47.000-02:00",
    "updated_at": "2016-02-15T17:23:34.353-02:00",
    "location_id": 185,
    "machine_id": 612,
    "equipment_id": 314,
    "place": "Recepção 2",
    "restock_mode": "restock_and_cash_collect",
    "restock_strategy": "allow_pick_list_or_full",
    "notifications_enabled": false,
    "audit_enabled": true,
    "visit_schedule": ["monday", "wednesday", "friday"],
    "current_planogram": {
      "id": 2960,
      "created_at": "2016-02-15T16:50:47.000-02:00",
      "updated_at": "2016-02-15T16:50:47.000-02:00",
      "due": "due_now",
      "started_at": "2016-02-15T16:51:47.000-02:00",
      "items": [
        {
          "id": 113845,
          "created_at": "2016-02-15T16:50:47.000-02:00",
          "updated_at": "2016-02-15T16:50:47.000-02:00",
          "planogram_id": 2960,
          "type": "Coil",
          "good_id": 10,
          "name": "1,2",
          "capacity": 20,
          "par_level": 20,
          "alert_level": 4,
          "desired_price": 2.5,
          "modified": false,
          "undefined": false,
          "logical_locator": "1",
          "physical_locators": [
            "1",
            "2"
          ],
          "children": null,
          "current_balance": 20,
          "good": {
            "id": 10,
            "name": "Amendoin",
            "upc_code": "77",
            "upc_code_name": "77 - Amendoin",
            "unit_description": "Unidade",
            "unit_symbol": "un"
          }
        }
      ]
    },
    "balance": {
      "total_collectable_coins": 0,
      "total_collectable_bills": 0,
      "total_collectable": 0,
      "total_in_coin_changer": 0,
      "total_in_bill_changer": 0,
      "total_in_changer": 0,
      "total_in_coins": 0,
      "total_in_bills": 0,
      "total_in_cash": 0
    },
    "current_session": {
      "cashbox": 0,
      "bill": 0,
      "collection": 0,
      "changer": 0,
      "recycler": 0,
      "supplied": 0,
      "cashless": 0,
      "total_vends": 0,
      "difference": 0,
      "vends": []
    }
  }

Erros
-----

==========  ====================================  ====================================================
status      descrição                             response body
==========  ====================================  ====================================================
400         parâmetros faltando                   { "status": "400", "error": "Bad Request" }
401         não autorizado                        (vazio)
404         máquina ou instalação não encontrada  (vazio)
422         erro ao atualizar                     ver exemplo abaixo
==========  ====================================  ====================================================

422 - erro ao atualizar:

::

  {
    "location_id": [
      "não é válido"
    ]
  }

Baixar
======

Baixa uma instalação de determinada máquina.

::

  DELETE /api/v1/machines/[machine_id]/installations/[id]

Parâmetros de URL:
------------------

==========  ================  ===========
parâmetro   descrição         obrigatório
==========  ================  ===========
machine_id  id da máquina     sim
id          id da instalação  sim
==========  ================  ===========

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
401         não autorizado                        (vazio)
404         máquina ou instalação não encontrada  (vazio)
==========  ====================================  ====================================================

Resources aninhadas
===================

.. toctree::
   :maxdepth: 1

   installations/pick_list
   installations/planogram
