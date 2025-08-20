---
description: >-
  Aqui nessa página você encontrará informações da requisição para criação de um
  documento via modelo na Zapsign.
---

# Criar documento via Modelo

## Structs utilizadas:

* [DeParaTemplate](../structs/deparatemplate.md)
* [DocFromTemplate](../structs/docfromtemplate.md)

## Visão geral:

No SDK em Go, temos o arquivo '**create\_doc\_from\_template\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de criação de documento via modelo, basta navegar em **"tests/docs/create\_doc\_from\_template\_test.go".**

<figure><img src="../../../../.gitbook/assets/files (1).png" alt=""><figcaption><p>Estrutura de arquivos de teste de documentos do SDK</p></figcaption></figure>



Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

*   Um API Token.&#x20;

    * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
    * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)


* Criação de variáveis pro seu template
  * Navegue até "**models/deparatemplate.go**" e localize a função abaixo:

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 11-44-41.png" alt=""><figcaption><p>Função responsável pela criação de variáveis</p></figcaption></figure>

Não sabe o que são variáveis de um? Saiba mais sobre variáveis [aqui](https://docs.zapsign.com.br/documentos/criar-documento-via-modelo). Para mais informações, confira também a classe [DeParaTemplate](../structs/deparatemplate.md).

* Os campos de um documento
  * Navegue até "**models/docfromtemplate.go**" e localize a função abaixo:

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 11-50-48.png" alt=""><figcaption><p>Função responsável por retornar uma resposta com os campos do seu documento que será criado a partir de um template</p></figcaption></figure>

Para mais informações de como configurar seu documento a partir de um modelo, confira também a classe [DocFromTemplate](../../sdk-em-java/classes-usadas/body/docfromtemplate.md).

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/), suas variáveis e seu documento basta rodar o teste automatizado que UM documento a partir de um template id será criado.

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 12-04-15.png" alt=""><figcaption></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e UM documento a partir de um template id foi criado em sua conta!  Fácil, né? 😁

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).

