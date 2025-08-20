---
description: >-
  Aqui nessa página você encontrará informações da requisição para atualização
  de um signatário na Zapsign.
---

# Atualizar signatário

## Structs utilizadas:

* [Signer](../structs/signer.md)

## Visão geral:

No SDK em Go, temos o arquivo '**update\_signer\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de atualização de signatário, basta navegar em **"tests/signers/update\_signer\_test.go".**

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 16-27-52.png" alt=""><figcaption><p>Estrutura de arquivos de teste de signatários do SDK</p></figcaption></figure>

Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)
* Um token de signatário: Veja como adicionar um token de um signatário [aqui](../definindo-configuracoes/adicionando-um-token-de-um-signatario.md).
*   A configuração do seu signatário. Navegue até "**tests/signers/update\_signer\_test.go**" e localize a função abaixo:



<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 15-52-01.png" alt=""><figcaption><p>Função de teste de atualização de um signatário</p></figcaption></figure>

Edite essas linhas para a configuração correta do seu signatário. Os campos a se colocar podem ser vistos [aqui](../structs/signer.md).

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 15-55-24.png" alt=""><figcaption><p>Configuração de signatário a ser editado</p></figcaption></figure>

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/) e do seu signatário basta rodar o teste automatizado que UM signatário será atualizado.

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 16-01-57.png" alt=""><figcaption><p>Sucesso ao editar um signatário</p></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e UM signatário foi atualizado no seu documento! Fácil, né? 😁

Mais informações sobre a requisição, pode ser encontrada [aqui](https://docs.zapsign.com.br/signatarios/atualizar-signatario)!

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
