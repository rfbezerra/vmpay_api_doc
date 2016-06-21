############
Equipamentos
############

Listar
======

::

  GET /api/v1/equipments

Filtros
-------

Os parâmetros abaixo podem ser passados como uma `query string <https://en.wikipedia.org/wiki/Query_string>`_.

**assigned**:
  Retorna máquinas associadas, não associadas ou todas, dependendo do valor:

  * *true*: retorna somente os equipamentos associados a alguma instalação ativa
  * *false*: retorna somente os equipamento não associados a nenhuma das instalações ativas
  * não informado: retorna todos os equipamentos

Exemplos::

  GET /api/v1/equipments?assigned=true
  GET /api/v1/equipments?assigned=false
  GET /api/v1/equipments

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
      "id": 258,
      "serial_number": "081875000007",
      "label_number": "0249",
      "point_of_sale": 50062
    },
    {
      "id": 257,
      "serial_number": "081875000012",
      "label_number": "0250",
      "point_of_sale": 50070
    },
    {
      "id": 259,
      "serial_number": "08187500000F",
      "label_number": "0251",
      "point_of_sale": null
    }
  ]

Ver
===

::

  GET /api/v1/equipments/[id]


Parâmetros de URL:
------------------

=========  =================  ===========
parâmetro  descrição          obrigatório
=========  =================  ===========
id         id do equipamento  sim
=========  =================  ===========

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
    "id": 1294,
    "serial_number": "357176047267502",
    "label_number": "1253",
    "point_of_sale": null
  }

Erros
-----

==========  ==========================  =========================================
status      descrição                   response body
==========  ==========================  =========================================
404         equipamento não encontrado  { "status": "404", "error": "Not Found" }
==========  ==========================  =========================================
