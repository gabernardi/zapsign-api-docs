---
description: >-
  Aqui nessa página você encontrará informações da requisição para detalhar um
  signatário na Zapsign.
---

# Detalhar signatário

## Visão geral:

No SDK em Go, temos o arquivo '**detail\_signer\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de detalhamento de signatário, basta navegar em **"tests/signers/detail\_signer\_test.go".**

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 16-27-52.png" alt=""><figcaption><p>Estrutura de arquivos de teste de signatários do SDK</p></figcaption></figure>

Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)
* Um token de signatário: Veja como adicionar um token de um signatário [aqui](../definindo-configuracoes/adicionando-um-token-de-um-signatario.md).

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/) e do seu signatário basta rodar o teste automatizado que os detalhes de UM signatário serão exibidos no seu console.

Exemplo:

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 16-25-47.png" alt=""><figcaption><p>Detalhamento de um signário</p></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e o signatário será detalhado no console da sua IDE ou terminal! Fácil, né? 😁

Mais informações sobre a requisição, pode ser encontrada [aqui](https://docs.zapsign.com.br/signatarios/detalhar-signatario)!

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
