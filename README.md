# Documentação da API do VMPay

### Descrição

Código fonte da documentação da API do VMPay.

Escrita em formato [reStructuredText](http://docutils.sourceforge.net/rst.html),
usando o [Sphinx](http://sphinx-doc.org/),
hospedada no [readthedocs](https://readthedocs.org/).

### Setup

[Guia para instalar e utilizar o Sphinx com o readthedocs](https://docs.readthedocs.org/en/latest/getting_started.html)

### Quick start

A documentação é gerada em html a partir dos arquvivos .rst (reStructuredText):

1. Editar o arquivo .rst desejado ([Referência do formato reStructuredText](http://sphinx-doc.org/rest.html))

2. Ir para o diretório docs

   ```cd docs```

3. Gerar a documentação em html:

   ```make html```

4. A documentação html será gerada dentro do diretório `build`

5. Se o html estiver ok, é só commitar e dar push para este repo. A documentação
será automaticamente gerada e disponibilizada no readthedocs.

### Onde ler a documentação do VMPay

A documentação em formato legível está [aqui](http://vmpay-api.readthedocs.org/en/latest/).

### Referências

[Referência do formato reStructuredText](http://sphinx-doc.org/rest.html)
