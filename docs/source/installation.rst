###########
Instalações
###########

Listar
======

Lista instalações de determinada máquina.

::

    GET /api/v1/machines/[machine_id]/installations

Ver
===

Mostra determinada instalação de uma máquina.

::

    GET /api/v1/machines/[machine_id]/installations/[id]

Criar
=====

Cria uma nova instalação em determinada máquina.

Se a máquina já possuir uma instalação ativa, a mesma é baixada automaticamente na data e hora atuais. A instalação criada torna-se a ativa.

::

    POST /api/v1/machines/[machine_id]/installations

Request::

    {
      "installation": {
        "location_id": 12,
        "equipment_id": 123,
        "place": "Recepção",
        "cash_mode": "cash_and_cashless",
        "restock_mode": "restock_and_cash_collect",
        "notifications_enabled": true,
        "audit_enabled": true,
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

  * *notifications_enabled*: enviar notificações?
  * *audit_enabled*: habilitar auditorias?

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

Atualizar
=========

Atualiza uma instalação de determinada máquina.

::

    PATCH /api/v1/machines/[machine_id]/installations/[id]

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

Somente os parâmetros *location_id*, *place* e *notifications_enabled* são considerados; os demais são ignorados.

Não é permitido atualizar um planograma ativo, somente cadastrar um outro planograma pendente. Para tanto, ver Planogramas.

Baixar
======

Baixa uma instalação de determinada máquina.

::

    DELETE /api/v1/machines/[machine_id]/installations/[id]
