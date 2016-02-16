##################
Modelos de máquina
##################

Listar
======

::

  GET /api/v1/machine_models

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
      "id": 69,
      "name": "Tower Nespresso",
      "status": "approved",
      "manufacturer_id": 1,
      "machine_type_id": 8
    },
    {
      "id": 70,
      "name": "AMS 35",
      "status": "approved",
      "manufacturer_id": 2,
      "machine_type_id": 1
    },
    {
      "id": 71,
      "name": "AMS 39",
      "status": "approved",
      "manufacturer_id": 2,
      "machine_type_id": 1
    }
  ]
