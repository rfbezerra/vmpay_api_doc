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

* **checkpoints**: lista dos checkpoints da visita; cada elemento contém:

  - **id**: o id do `checkpoint <scheduled_visit_checkpoints.html>`_

  - **installation_id**: o id da instalação

Exemplo:

::

  [
    {
      "id": 4744,
      "created_at": "2016-12-21T07:54:55.000-02:00",
      "updated_at": "2016-12-21T10:16:01.000-02:00",
      "date": "2016-12-21",
      "completed_at": "2016-12-21T10:16:01.000-02:00",
      "checkpoints": [
        { "id": 21013, "installation_id": 1896 },
        { "id": 21014, "installation_id": 1903 },
        { "id": 21015, "installation_id": 1901 },
        { "id": 21016, "installation_id": 2020 },
        { "id": 21017, "installation_id": 1894 },
        { "id": 21018, "installation_id": 1899 }
      ]
    },
    {
      "id": 4745,
      "created_at": "2016-12-21T08:05:40.000-02:00",
      "updated_at": "2016-12-21T12:40:37.000-02:00",
      "date": "2016-12-21",
      "completed_at": "2016-12-21T12:40:37.000-02:00",
      "checkpoints": [
        { "id": 21019, "installation_id": 1983 },
        { "id": 21020, "installation_id": 3794 },
        { "id": 21021, "installation_id": 1370 },
        { "id": 21022, "installation_id": 843 },
        { "id": 21023, "installation_id": 1834 }
      ]
    }
  ]
