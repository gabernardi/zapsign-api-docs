---
description: >-
  Aqui nessa página você encontrará informações da requisição para criação de um
  documento extra a um documento já existente aqui na Zapsign.
---

# Inserir documento extra

## Visão geral:



Na SDK em Go, temos o arquivo '**add\_extra\_doc\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de criação de um documento extra, basta navegar em **"tests/docs/add\_extra\_doc\_test.go".**

![](<../../../../.gitbook/assets/image (32).png>)



Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  *   [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)


* Um documento principal já criado na Zapsign. Veja como podemos criar um [documento na Zapsign utilizando a API.](https://docs.zapsign.com.br/documentos/criar-documento)
*   O Body da requisição

    * Navegue até "**models/extradoc.go"**
      * Configure como você quer que seu extra documento seja criado. Veja mais detalhes nesse link de como criar um [documento extra utilizando a API](https://docs.zapsign.com.br/documentos/adicionar-anexo-documento-extra).

    <figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-09 15-14-50 (1).png" alt=""><figcaption></figcaption></figure>

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/) e um token de um documento principal, basta rodar o teste automatizado que o documento extra seja anexado ao documento principal.&#x20;

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-09 15-18-39.png" alt=""><figcaption><p>Sucesso ao criar um documento extra</p></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e o documento extra foi anexado ao documento principal!  Fácil, né? 😁

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
