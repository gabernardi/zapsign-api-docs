---
description: >-
  Guia para adicionar um token de um documento para utilizar as requisições de
  documentos e/ou signatários na Zapsign.
---

# Adicionando um token de um documento

Navegue até **"SdkGo/utils/"** e abra o arquivo **"util.go".**

![](<../../../../.gitbook/assets/image (24).png>)

O arquivo "**util.go"** é um dos arquivos mais importantes do SDK. Nesse arquivo, há uma responsabilidade de definição de tokens de documentos, signatários, bem como também seu token de documento é adicionado aqui.

Encontre a função **"GetDocToken()"** e adicione seu token no retorno dessa função.

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 12-12-56.png" alt=""><figcaption><p>Função responsável por guardar um token de um documento</p></figcaption></figure>

Prontinho! Agora, o token de UM documento estará adicionado em todas as requisições na Zapsign! Lembre-se sempre de mudar esse token caso você queira fazer alguma outra ação com outro documento, tá? Agora apenas precisamos rodar os testes equivalentes a cada requisição! Fácil, né? 😁



Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
