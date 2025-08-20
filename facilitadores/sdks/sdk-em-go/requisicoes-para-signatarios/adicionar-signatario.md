---
description: >-
  Aqui nessa página você encontrará informações da requisição para criação de um
  signatário na Zapsign.
---

# Adicionar signatário

## Structs utilizadas:

* [Signer](../structs/signer.md)

## Visão geral:

No SDK em Go, temos o arquivo '**add\_signer\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de adicionar um signatário, basta navegar em **"tests/signers/add\_signer\_test.go".**

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 16-27-52.png" alt=""><figcaption><p>Estrutura de arquivos de teste de signatários do SDK</p></figcaption></figure>

Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)
*   A configuração do seu signatário. Navegue até "**models/signer.go**" e localize a função abaixo:



<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 14-31-21.png" alt=""><figcaption><p>Função para adicionar um token de um documento</p></figcaption></figure>

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/) e do seu signatário basta rodar o teste automatizado que UM será criado.

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 14-43-40.png" alt=""><figcaption><p>Sucesso ao criar um signatário</p></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e UM signatário foi criado no seu documento! Fácil, né? 😁

Mais informações sobre a requisição, pode ser encontrada [aqui](https://docs.zapsign.com.br/signatarios/adicionar-signatario)!

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
