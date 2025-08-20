---
description: >-
  Guia para adicionar seu API Token para utilizar as requisições de documentos
  e/ou signatários na Zapsign.
---

# Adicionando API Token

Navegue até **"SdkGo/utils/"** e abra o arquivo **"util.go".**

![](<../../../../.gitbook/assets/image (24).png>)

O arquivo "**util.go"** é um dos arquivos mais importantes do SDK. Nesse arquivo, há uma responsabilidade de definição de tokens de documentos, signatários, bem como também seu [API Token](https://docs.zapsign.com.br/) é adicionado aqui.

Encontre a função **"GetApiToken()"** e adicione seu token no retorno dessa função.\~

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 12-14-43 (1).png" alt=""><figcaption><p>Função responsável por guardar seu API Token</p></figcaption></figure>

Prontinho! Agora, seu API Token estará adicionado em todas as requisições na Zapsign! Agora apenas precisamos rodar os testes equivalentes a cada requisição! Fácil, né? 😁

Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).

