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

Exemplo de requisição válida
============================

Essa requisição lista toda as categorias de um determinado operador::

    GET http://vmpay.vertitecnologia.com.br/api/v1/categories?access_token=213qweasdzxc

Códigos de retorno e seus significados
======================================

* 200: OK
* 201: Criado com sucesso
* 204: Excluído com sucesso
* 400: bad request, algum parâmetro obrigatório faltando
* 401: unauthorized, tentativa de alterar/excluir uma categoria de outro operador
* 422: Erro ao criar, nome já está em uso

Exemplo de uso
==============

Um exemplo de código em linguagem Python para acessar a API do VMPay está
disponível no `repositório da Verti no github`_.

.. _repositório da Verti no github: https://github.com/vertitecnologia/vmpay_api_client
