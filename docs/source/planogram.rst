###########
Planogramas
###########

Listar
======

Lista os planogramas de determinada máquina e instalação.

::

    GET /api/v1/machines/[machine_id]/installations/[installation_id]/planograms

Ver
===

Mostra determinado planograma de uma máquina e instalação.

::

    GET /api/v1/machines/[machine_id]/installations/[installation_id]/planograms/[id]

Criar
=====

Cria uma novo planograma em determinada máquina e instalação.

O planograma criado fica pendente e pode ser atualizado. O mesmo só entra em atividade no próximo reabastecimento da máquina.

Uma instalação pode ter somente um planograma pendente. Se houver uma tentativa de cadastro de um outro planograma, será retornado um erro de validação, código HTTP 422.

::

    POST /api/v1/machines/[machine_id]/installations/[installation_id]/planograms

Request::

    {
      "planogram": {
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
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *planogram*

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

Nenhum.

Atualizar
=========

Atualiza um planograma de determinada máquina e instalação.

Somente planogramas pendentes podem ser atualizados. Se houver uma tentativa de atualização de planograma ativo ou anterior, será retornado um erro de validação, código HTTP 422.

::

    PATCH /api/v1/machines/[machine_id]/installations/[installation_id]/planograms/[id]

Request::

    {
      "planogram": {
        "items_attributes": [
          {
            "id": 64893,
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
            "id": 64894,
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
            "id": 64895,
            "type": "VirtualCoil",
            "name": "4",
            "good_id": 23,
            "desired_price": 4.0,
            "logical_locator": 3,
            "children": { "1": 2, "2": 1 }
          },
          {
            "id": 64896,
            "type": "Canister",
            "good_id": 26,
            "capacity": 2000,
            "par_level": 2000,
            "alert_level": 200,
            "logical_locator": 4
          },
          {
            "id": 64897,
            "type": "Canister",
            "good_id": 27,
            "capacity": 3000,
            "par_level": 3000,
            "alert_level": 300,
            "logical_locator": 5
          },
          {
            "id": 64898,
            "type": "VirtualCanister",
            "good_id": 30,
            "name": "5",
            "desired_price": 3.0,
            "logical_locator": 6,
            "children": { "4": 20, "5": 15 }
          }
        ]
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *planogram*

  * *items_attributes*: um array contendo os items do planograma.

    * Os items podem ser de 4 tipos: canaletas, combos, canisters e seleções.
    * Canaletas:

      * *id*: o id do item, gerado automaticamente pelo sistema no momento da criação do planograma.
      * *type*: deve ser igual a "Coil".
      * *name*: o número da canaleta. Caso se trate de um agrupamento de canaletas, os números devem ser separados por vírgulas.
      * *good_id*: id do produto. Nesse caso não pode ser composto. `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.
      * *capacity*: a capacidade total da canaleta. No caso de agrupameto de canaletas, deve-se colocar aqui a capacidade total, somando-se todas as canaletas.
      * *par_level*: o nível de par da canaleta. No caso de agrupameto de canaletas, deve-se colocar aqui o nível de par total, somando-se todas as canaletas.
      * *alert_level*: o nível de alerta da canaleta.
      * *desired_price*: o preço unitário desejado.
      * *logical_locator*: trata-se do identificador lógico da canaleta. Deve-se gerar um inteiro único dentro de todos os items do planograma.

    * Combos:

      * *id*: o id do item, gerado automaticamente pelo sistema no momento da criação do planograma.
      * *type*: deve ser igual a "VirtualCoil".
      * *name*: o número de seleção do combo.
      * *good_id*: id do produto. Nesse caso deve ser composto e com o *type* *Combo*. `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.
      * *desired_price*: o preço unitário desejado.
      * *logical_locator*: trata-se do identificador lógico do combo. Deve-se gerar um inteiro único dentro de todos os items do planograma.
      * *children*: as canaletas e suas quantidades que compõe o combo. É um objeto cujas chaves são identificares lógicos (campo *logical_locator*) das canaletas e os valores as quantidades. No exemplo acima, o combo é composto de 2 produtos da canaleta cujo *name* é "1,2" - ou seja, canaletas 1 e 2 agrupadas - e 1 produto da canaleta 3.

    * Canisters:

      * *id*: o id do item, gerado automaticamente pelo sistema no momento da criação do planograma.
      * *type*: deve ser igual a "Canister".
      * *good_id*: id do insumo. `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.
      * *capacity*: a capacidade total do canister. Deve ser preenchido na mesma unidade do insumo (g, ml ou un).
      * *par_level*: o nível de par do canister. Deve ser preenchido na mesma unidade do insumo (g, ml ou un).
      * *alert_level*: o nível de alerta do canister. Deve ser preenchido na mesma unidade do insumo (g, ml ou un).
      * *logical_locator*: trata-se do identificador lógico do canister. Deve-se gerar um inteiro único dentro de todos os items do planograma.

    * Seleções:

      * *id*: o id do item, gerado automaticamente pelo sistema no momento da criação do planograma.
      * *type*: deve ser igual a "VirtualCanister".
      * *name*: o número da seleção.
      * *good_id*: id do produto. Nesse caso deve ser composto e com o *type* *Mixture*. `Good <https://en.wikipedia.org/wiki/Good_%28economics%29>`_ neste caso se traduz como `bem <https://pt.wikipedia.org/wiki/Bem_%28economia%29>`_.
      * *desired_price*: o preço unitário desejado.
      * *logical_locator*: trata-se do identificador lógico da seleção. Deve-se gerar um inteiro único dentro de todos os items do planograma.
      * *children*: os canisters e suas quantidades que compõe a seleção. É um objeto cujas chaves são identificares lógicos (campo *logical_locator*) dos canisters e os valores as quantidades. No exemplo acima, digamos que o insumo de id 26 seja *Café em pó* e o de id 27, *Leite em pó*. Logo, a seleção é composta de 20 gramas de Café em pó e 15 gramas de Leite em pó.

Opcionais
^^^^^^^^^

Nenhum.

Excluir
=======

Exclui um planograma de determinada máquina e instalação.

Somente planogramas pendentes podem ser excluídos. Se houver uma tentativa de exclusão de planograma ativo ou anterior, será retornado um erro de validação, código HTTP 422.

::

    DELETE /api/v1/machines/[machine_id]/installations/[installation_id]/planograms/[id]
