---
description: >-
  Guia para adicionar um token de um signatário para utilizar as requisições de
  documentos e/ou signatários na Zapsign.
---

# Adicionando um token de um signatário

Navegue até **"SdkGo/utils/"** e abra o arquivo **"util.go".**

![](<../../../../.gitbook/assets/image (24).png>)

O arquivo "**util.go"** é um dos arquivos mais importantes do SDK. Nesse arquivo, há uma responsabilidade de definição de tokens de documentos, signatários, bem como também seu token de Signatário é adicionado aqui.

Encontre a função **"GetSignerToken()"** e adicione seu token no retorno dessa função.

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 12-16-59.png" alt=""><figcaption><p>Função responsável por guardar um token de um signatário</p></figcaption></figure>



Prontinho! Agora, o token de UM signatário estará adicionado em todas as requisições na Zapsign! Lembre-se sempre de mudar esse token caso você queira fazer alguma outra ação com outro signatário, tá? Agora apenas precisamos rodar os testes equivalentes a cada requisição! Fácil, né? 😁

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
