---
description: >-
  Aqui nessa página você encontrará informações da requisição para exclusão de
  um signatário na Zapsign.
---

# Excluir signatário

## Visão geral:

No SDK em Go, temos o arquivo '**delete\_signer\_test.go**' no diretório do projeto **SdkGo** na Zapsign! Confira o diretório clicando [aqui](https://github.com/ZapSign/SdkGo).&#x20;

Ao entrar no projeto, podemos ver claramente que existe uma estrutura de testes automatizados para cada requisição da Zapsign na pasta "**tests**". Para acessar o teste de exclusão de signatário, basta navegar em **"tests/signers/delete\_signer\_test.go".**

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 16-27-52.png" alt=""><figcaption><p>Estrutura de arquivos de teste de signatários do SDK</p></figcaption></figure>

Para que esse teste consiga ter um [retorno 200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) e com sucesso, precisamos de algumas configurações essenciais. Lembre-se de usar um token a ser deletado de um documento que tenha mais de um signatário, caso contrário, não será possível deletar um signatário que esteja unicamente sozinho no documento.

* Um API Token.&#x20;
  * Descubra como achar seu [API Token](https://docs.zapsign.com.br/).
  * [Adicione seu API Token no projeto](../definindo-configuracoes/adicionando-api-token.md)
* O token do signatário a ser deletado. Veja como adicionar um token de um signatário que precisa ser excluído [aqui](../definindo-configuracoes/adicionando-um-token-de-um-signatario-que-precisa-ser-deletado.md).

Após toda a configuração do seu [API Token](https://docs.zapsign.com.br/) e do token do signatário a ser excluído basta rodar o teste automatizado que UM signatário será deletado.

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 15-04-24.png" alt=""><figcaption><p>Sucesso ao deletar um documento</p></figcaption></figure>

Pronto! A requisição foi realizada com sucesso e UM signatário foi deletado do seu documento! Fácil, né? 😁

Mais informações sobre a requisição, pode ser encontrada [aqui](https://docs.zapsign.com.br/signatarios/excluir-signatario)!

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
