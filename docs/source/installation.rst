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
        "cash_mode": "",
        "restock_mode": "",
        "notifications_enabled": true,
        "audit_enabled": true
      }
    }

Campos
------

Obrigatórios
^^^^^^^^^^^^

* *installation*

  * *location_id*: id do local.
  * *equipment_id*: ido do equipamento.
  * *cash_mode*: modo de pagamento.

    * Valores permitidos: *cash_and_cashless* (dinheiro e cartão), *cashless_only* (somente cartão) ou *cash_only* (somente dinheiro).

  * *restock_mode*: botão de reabastecimento.

    * Valores permitidos: *restock_and_cash_collect* (reabastecimento + coleta) ou *restock_only* (somente reabastecimento).
    * Se o botão de reabastecimento da máquina for pressionado somente uma única vez, o sistema irá gerar um reabastecimento juntamente com uma coleta ou somente um reabastecimento dependendo da opção selecionada.
    * Se o botão for pressionado duas vezes, o sistema sempre irá gerar uma coleta.

  * *notifications_enabled*: enviar notificações?
  * *audit_enabled*: habilitar auditorias?

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
