---
description: >-
  Aqui nessa página você encontrará informações da requisição para detalhamento
  de um documento na Zapsign.
---

# Detalhar documento

## Visão geral:

No SDK em Go, temos o arquivo '**detail\_doc\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de detalhamento de documento, basta navegar em **"tests/docs/detail\_doc\_test.go".**

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-10 16-57-24.png" alt=""><figcaption><p>Estrutura de arquivos de teste de documentos do SDK</p></figcaption></figure>

Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)
* Um Token de um documento a ser detalhado. [Confira aqui como fazer isso](../definindo-configuracoes/adicionando-um-token-de-um-documento.md).

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/) e seu token de documento basta rodar o teste automatizado que a listagem de UM documento será executada.

Exemplo:

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 16-44-38.png" alt=""><figcaption><p>Detalhamento de um documento</p></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e o documento será detalhado no console da sua IDE ou terminal! Fácil, né? 😁

Mais informações sobre a requisição, pode ser encontrada [aqui](https://docs.zapsign.com.br/documentos/detalhar-documento)!

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
