###########
Visão geral
###########

Endpoints
=========

Os endpoints são mapeados como segue::

    http://vmpay.vertitecnologia.com.br/api/v1/caminho/para/resource

Autenticação
============

Cada operador receberá a sua api key, que deverá ser passada na URL em TODAS as
requisições feitas à API.

Exemplo::

    http://vmpay.vertitecnologia.com.br/api/v1/caminho/para/api?access_token=837e068fbb4c1e1f

Paginação
=========

Serviços que retornam muitos registros podem usar paginação para evitar
sobrecarga do servidor e demora no cliente. Quando habilitada os seguintes
parâmetros estarão disponíveis:

* **page**: a página a ser buscada pela consulta.

  * Caso não seja passado, é considerado 1.

* **per_page**: o número de registros por página.

  * Caso não seja passado, é considerado 100.
  * Pode ser até 1000 no máximo.
  * Caso seja passado mais que 1000, é retornado erro com o código HTTP 400 (*bad request*).

Exemplo de requisição válida
============================

Essa requisição lista toda as categorias de um determinado operador::

    GET http://vmpay.vertitecnologia.com.br/api/v1/categories?access_token=213qweasdzxc

Códigos de retorno e seus significados
======================================

* 200: Requisição processada com sucesso / entidade salva com sucesso
* 201: Entidade criada com sucesso
* 204: Entidade excluída com sucesso
* 400: Algum parâmetro obrigatório faltando ou com formato errado
* 401: Tentativa de acesso a entidade não permitida
* 422: Entidade não salva por conta de erros de validação

Código de exemplo
=================

Um exemplo de código em linguagem Python para acessar a API do VMPay está
disponível no `repositório da Verti no github`_.

.. _repositório da Verti no github: https://github.com/vertitecnologia/vmpay_api_client
