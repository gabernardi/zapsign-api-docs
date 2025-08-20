---
description: >-
  Aqui nessa página você encontrará informações da requisição para exclusão de
  um documento na Zapsign.
---

# Excluir documento

## Visão geral:

No SDK em Go, temos o arquivo '**delete\_doc\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de exclusão de documento, basta navegar em **"tests/docs/delete\_doc\_test.go".**

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-10 16-57-24.png" alt=""><figcaption><p>Estrutura de arquivos de teste de documentos do SDK</p></figcaption></figure>

Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)
* Um Token de um documento a ser excluído. Navegue até "**utils/util.go**" e localize a função abaixo:

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 10-51-02 (1).png" alt=""><figcaption></figcaption></figure>

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/) e seu token de documento para ser excluído basta rodar o teste automatizado que a exclusão de UM documento será executada. Lembre-se sempre de trocar o token de um documento excluído para que não se repita a mesma requisição.

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 11-13-49 (1).png" alt=""><figcaption></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e um documento foi removido de sua conta!  Fácil, né? 😁

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
