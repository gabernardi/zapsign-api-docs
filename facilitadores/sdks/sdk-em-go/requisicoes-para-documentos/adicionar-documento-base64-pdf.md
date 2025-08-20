---
description: >-
  Aqui nessa página você encontrará informações da requisição para criação de um
  documento via base64 de um docx aqui na Zapsign.
---

# Adicionar documento base64 PDF

## Struct utilizada:

* [Signer](../../sdk-em-java/classes-usadas/body/signer.md)
* [Base64Pdf](../structs/base64pdf.md)

## Sobre o base64:

Base64 é uma maneira simples de converter um arquivo em texto. Veja aqui uma definição mais completa [https://pt.wikipedia.org/wiki/Base64](https://pt.wikipedia.org/wiki/Base64). Assim, converter o arquivo em base64 e enviar como texto no corpo da requisição é mais fácil do que lidar com **multipart/form-data**, por exemplo.

Para testar a API, você pode converter manualmente seu PDF em base64 através de vários sites, como esse: [https://base64.guru/converter/encode/pdf](https://base64.guru/converter/encode/pdf)

Quando a API já estiver integrada em seu sistema, procure a função adequada na sua linguagem de programação que pode converter o arquivo em base64.

**Observação:** você deve enviar o parâmetro base64\_pdf apenas com a conversão do arquivo em base64. **Não** insira data:application/pdf;base64, na sua string.&#x20;

## Visão geral:



Na SDK em Go, temos o arquivo '**create\_doc\_frombase64pdf\_parameter\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de criação de um documento via base64 em '.pdf', basta navegar em **"tests/docs/create\_doc\_frombase64pdf\_parameter\_test.go".**

![](<../../../../.gitbook/assets/image (64).png>)



Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)
* O Body da requisição
  * Navegue até "**models/base64.go"**
    * Configure como você quer que seu documento seja criado. Veja mais detalhes nesse link de como criar um [documento utilizando a API](https://docs.zapsign.com.br/documentos/criar-documento).

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-10 16-02-05.png" alt=""><figcaption><p>Exemplo básico de um documento criado com o parâmetro base64_pdf </p></figcaption></figure>

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/), basta rodar o teste automatizado que o documento será criado com sucesso.&#x20;

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-10 16-11-40.png" alt=""><figcaption><p>Teste automatizado concluído e documento criado com sucesso.</p></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e um documento foi criado em sua conta!  Fácil, né? 😁

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
