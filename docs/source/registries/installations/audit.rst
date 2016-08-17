##########
Auditorias
##########

Listar
======

Lista as auditorias de determinada máquina e instalação.

::

  GET /api/v1/machines/[machine_id]/installations/[installation_id]/audits

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
      "id": 725818,
      "began_at": "2016-04-25T15:00:30.000-03:00",
      "ended_at": "2016-04-25T15:00:33.000-03:00",
      "total_quantity": 1,
      "total_value": 2.5
    },
    {
      "id": 725186,
      "began_at": "2016-04-25T11:50:27.000-03:00",
      "ended_at": "2016-04-25T11:50:31.000-03:00",
      "total_quantity": 7,
      "total_value": 19.85
    },
    {
      "id": 724622,
      "began_at": "2016-04-25T09:00:30.000-03:00",
      "ended_at": "2016-04-25T09:00:33.000-03:00",
      "total_quantity": 1,
      "total_value": 3
    }
  ]

Ver
===

Mostra determinada auditoria de uma máquina e instalação.

::

  GET /api/v1/machines/[machine_id]/installations/[installation_id]/audits/[id]

Parâmetros de URL:
------------------

===============  ================  ===========
parâmetro        descrição         obrigatório
===============  ================  ===========
machine_id       id da máquina     sim
installation_id  id da instalação  sim
id               id da auditoria   sim
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
    "id": 725186,
    "occurred_at": "2016-04-25T11:50:27.000-03:00",
    "total_vends_value": 55,
    "total_vends_quantity": 500,
    "planogram_items": [
      {
        "locator": "10",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "11",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "12",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "13",
        "total_vends_value": 0.1,
        "total_vends_quantity": 0
      },
      {
        "locator": "14",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "15",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "16",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "17",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "18",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "19",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "20",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "21",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "22",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "23",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "24",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "25",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "26",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "27",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "28",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "29",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "30",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "31",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "32",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "33",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "34",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "35",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "36",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "37",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "38",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "39",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "40",
        "total_vends_value": 7.8,
        "total_vends_quantity": 59
      },
      {
        "locator": "41",
        "total_vends_value": 6.8,
        "total_vends_quantity": 68
      },
      {
        "locator": "42",
        "total_vends_value": 6.5,
        "total_vends_quantity": 65
      },
      {
        "locator": "43",
        "total_vends_value": 5.9,
        "total_vends_quantity": 58
      },
      {
        "locator": "44",
        "total_vends_value": 7,
        "total_vends_quantity": 70
      },
      {
        "locator": "45",
        "total_vends_value": 7.6,
        "total_vends_quantity": 76
      },
      {
        "locator": "46",
        "total_vends_value": 5.3,
        "total_vends_quantity": 51
      },
      {
        "locator": "47",
        "total_vends_value": 6.5,
        "total_vends_quantity": 38
      },
      {
        "locator": "48",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "49",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "50",
        "total_vends_value": 0.1,
        "total_vends_quantity": 1
      },
      {
        "locator": "51",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "52",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "53",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "54",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "55",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "56",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "57",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "58",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "59",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "60",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "61",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "62",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "63",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "64",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "65",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "66",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "67",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "68",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "69",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "70",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "71",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "72",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "73",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "74",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "75",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "76",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "77",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "78",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "79",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "80",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "81",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "82",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "83",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "84",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "85",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "86",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "87",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "88",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "89",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "90",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "91",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "92",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "93",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "94",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      }
    ]
  }

Erros
-----

======  ===========================================  =========================================
status  descrição                                    response body
======  ===========================================  =========================================
404     máquina/instalação/auditoria não encontrada  { "status": "404", "error": "Not Found" }
======  ===========================================  =========================================



Ver última auditoria
====================

Mostra última auditoria de uma máquina e instalação.

::

  GET /api/v1/machines/[machine_id]/installations/[installation_id]/last_audit

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

  {
    "id": 725186,
    "occurred_at": "2016-04-25T11:50:27.000-03:00",
    "total_vends_value": 55,
    "total_vends_quantity": 500,
    "planogram_items": [
      {
        "locator": "10",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "11",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "12",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "13",
        "total_vends_value": 0.1,
        "total_vends_quantity": 0
      },
      {
        "locator": "14",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "15",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "16",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "17",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "18",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "19",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "20",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "21",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "22",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "23",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "24",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "25",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "26",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "27",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "28",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "29",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "30",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "31",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "32",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "33",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "34",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "35",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "36",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "37",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "38",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "39",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "40",
        "total_vends_value": 7.8,
        "total_vends_quantity": 59
      },
      {
        "locator": "41",
        "total_vends_value": 6.8,
        "total_vends_quantity": 68
      },
      {
        "locator": "42",
        "total_vends_value": 6.5,
        "total_vends_quantity": 65
      },
      {
        "locator": "43",
        "total_vends_value": 5.9,
        "total_vends_quantity": 58
      },
      {
        "locator": "44",
        "total_vends_value": 7,
        "total_vends_quantity": 70
      },
      {
        "locator": "45",
        "total_vends_value": 7.6,
        "total_vends_quantity": 76
      },
      {
        "locator": "46",
        "total_vends_value": 5.3,
        "total_vends_quantity": 51
      },
      {
        "locator": "47",
        "total_vends_value": 6.5,
        "total_vends_quantity": 38
      },
      {
        "locator": "48",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "49",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "50",
        "total_vends_value": 0.1,
        "total_vends_quantity": 1
      },
      {
        "locator": "51",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "52",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "53",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "54",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "55",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "56",
        "total_vends_value": 0.2,
        "total_vends_quantity": 2
      },
      {
        "locator": "57",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "58",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "59",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "60",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "61",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "62",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "63",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "64",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "65",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "66",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "67",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "68",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "69",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "70",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "71",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "72",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "73",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "74",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "75",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "76",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "77",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "78",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "79",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "80",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "81",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "82",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "83",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "84",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "85",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "86",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "87",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "88",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "89",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "90",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "91",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "92",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "93",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      },
      {
        "locator": "94",
        "total_vends_value": 0,
        "total_vends_quantity": 0
      }
    ]
  }

Erros
-----

======  ===========================================  =========================================
status  descrição                                    response body
======  ===========================================  =========================================
404     máquina/instalação/auditoria não encontrada  { "status": "404", "error": "Not Found" }
======  ===========================================  =========================================
