---
description: >-
  Aqui nessa página você encontrará informações da requisição para listagens de
  documentos na Zapsign.
---

# Listar documentos

## Visão geral:

Na SDK em Go, temos o arquivo '**get\_docs\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de listagens de documentos, basta navegar em **"tests/docs/get\_docs\_test.go".**

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-10 16-57-24.png" alt=""><figcaption><p>Estrutura de arquivos de teste de documentos do SDK</p></figcaption></figure>

Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/) basta rodar o teste automatizado que a listagem de documentos será executada.



Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
