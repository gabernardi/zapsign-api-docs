---
description: >-
  Guia para adicionar um token de um documento que será deletado para utilizar a
  requisição de deletar um documento
---

# Adicionando um token de um documento que precisa ser deletado

Navegue até **"SdkGo/utils/"** e abra o arquivo **"util.go".**

![](<../../../../.gitbook/assets/image (24).png>)

O arquivo "**util.go"** é um dos arquivos mais importantes do SDK. Nesse arquivo, há uma responsabilidade de definição de tokens de documentos, signatários, bem como também seu token de documento que precisa ser deletado é adicionado aqui.

Encontre a função **"GetDocTokenThatWillBeDeleted()"** e adicione o token de um documento que **PRECISA SER DELETADO** no retorno dessa função.

<figure><img src="../../../../.gitbook/assets/Captura de tela de 2023-02-13 12-10-56.png" alt=""><figcaption><p>Função responsável por guardar um token de um documento que precisa ser deletado</p></figcaption></figure>

Prontinho! Agora, o token de UM documento que precisa ser deletado estará adicionado em todas as requisições na Zapsign! Lembre-se sempre de mudar esse token caso você queira fazer o delete de outro documento, tá? Agora apenas precisamos rodar os testes equivalentes requisição de deletar documento! Fácil, né? 😁



Ficou alguma dúvida ou tem alguma sugestão de melhoria? Nos contate [aqui](https://zapsign.com.br/contato/).
