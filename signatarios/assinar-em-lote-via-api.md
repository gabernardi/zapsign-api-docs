# Assinar em lote via API

Se a sua empresa frequentemente precisa assinar muitos documentos, este endpoint oferece uma maneira eficiente de realizar essas assinaturas sem a necessidade de acessar manualmente cada documento. Com a **assinatura em lote, você economiza tempo e automatiza o processo de assinatura de múltiplos documentos!**\
\
Nesta seção:

* [Como utilizar o Postman para assinar em lote;](assinar-em-lote-via-api.md#como-utilizar-o-postman-para-assinar-em-lote)
* [Como conseguir o user\_token;](assinar-em-lote-via-api.md#como-conseguir-o-user_token)
* [Como conseguir o signers\_token;](assinar-em-lote-via-api.md#como-conseguir-os-signer_tokens)

***

### Requisitos prévios:

* Você só pode assinar via API com usuários dentro da sua conta.\
  Isso significa que os signatários devem estar registrados como usuários na sua conta, configurados na seção **Configurações > Organização > Usuários**. Não é possível assinar para terceiros ou clientes externos que não sejam usuários da sua conta.
* Só é possível assinar documentos que tenham o **e-mail do signatário vazio ou igual ao do usuário** que está assinando os documentos. Caso o e-mail seja diferente, **não será possível assinar.**
* O usuário deve ter as seguintes informações salvas na seção [**Configurações > Meu perfil > Dados Pessoais**](https://app.zapsign.com.br/conta/perfil): **nome, sobrenome, telefone, assinatura e visto**.
* **A assinatura via API não consome créditos (é gratuita).**\
  No entanto, é necessário ter um **Plano API ativo** para usar esse endpoint, incluindo o **add-on de assinatura em lote**.
* A assinatura em lote só funciona com autenticação por **"assinatura na tela", "selfie" e "foto do documento de identidade" e "CPF Simples"** sem preencher o CPF na criação do documento.\
  Se o documento possuir outro método de autenticação, **não será possível assinar esses documentos.**

Com essa funcionalidade, você poderá economizar tempo e tornar o processo de assinatura mais eficiente para sua equipe! 🚀

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/sign`

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Request Body

<table><thead><tr><th>Name</th><th width="136">Type</th><th>Description</th></tr></thead><tbody><tr><td>user_token<mark style="color:red;">*</mark></td><td>string</td><td>Token do usuário que irá assinar.</td></tr><tr><td>signer_tokens[]</td><td>array</td><td>Tokens que serão assinados (token do signer em cada documento a ser assinado). </td></tr><tr><td>selfie_photo</td><td>string</td><td>Deve ser uma URL publicamente acessível contendo a imagem da selfie, aceita nos formatos JPG, JPEG ou PNG.</td></tr><tr><td>document_photo_url</td><td>string</td><td>Deve ser uma URL publicamente acessível contendo a imagem frontal do documento, aceita nos formatos JPG, JPEG ou PNG.</td></tr><tr><td>document_verse_photo_url</td><td>string</td><td>Deve ser uma URL publicamente acessível contendo a imagem traseira do documento, aceita nos formatos JPG, JPEG ou PNG.</td></tr><tr><td>cpf</td><td>string</td><td>String que representa o número de CPF do usuário, composta por 11 dígitos numéricos, com ou sem pontuação.</td></tr></tbody></table>

### Como utilizar o Postman para assinar em lote

\
O Postman é um grande aliado para assinar rapidamente seus documentos. **Comece configurando o endpoint e adicionando seu API Token na aba&#x20;**_**Authorization**_**.** Depois, **acesse seu perfil na plataforma para pegar o&#x20;**_**user token**_ e reúna os _**signer tokens**_ dos documentos que serão assinados.&#x20;

![Usuário assinando um documento via endpoint de assinatura em lote.](https://github.com/AmandaAmani/documenta-ocurso/blob/main/requisi%C3%A7%C3%A3o%20api.gif?raw=true)

### Exemplo de requisição

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-13470670-e542-4cc2-bf8d-0e0538dba086?ctx=documentation" %}

| Name                                          | Type   | Description                                                                                                             |
| --------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------- |
| user\_token<mark style="color:red;">\*</mark> | string | Token do usuário que irá assinar.                                                                                       |
| signer\_tokens\[]                             | array  | Tokens que serão assinados (token do signer em cada documento a ser assinado).                                          |
| selfie\_photo                                 | string | Deve ser uma URL acessível publicamente contendo a imagem da selfie, aceita nos formatos JPG, JPEG ou PNG.              |
| document\_photo\_url                          | string | Deve ser uma URL acessível publicamente contendo a imagem da frente do documento, aceita nos formatos JPG, JPEG ou PNG. |
| document\_verse\_photo\_url                   | string | Deve ser uma URL acessível publicamente contendo a imagem do verso do documento, aceita nos formatos JPG, JPEG ou PNG.  |
| cpf                                           | string | String representando o número do CPF do usuário. Deve conter 11 dígitos numéricos, com ou sem pontuação.                |

**Exemplos de respostas**

{% tabs %}
{% tab title="200- Sucesso" %}
```
{"message":"Documento(s) assinado(s) com sucesso. Lembrete: este endpoint é assíncrono, então aguarde os PDF finais ficarem prontos via webhooks ou confira-os daqui alguns minutos."}
```
{% endtab %}

{% tab title="404-  "detail": "Não encontrado."" %}
Caso você tente realizar uma requisição com **user\_token** ou **signer\_tokens** que não existam, você receberá uma response 404 (não encontrado).
{% endtab %}
{% endtabs %}

***

### Como conseguir o user\_token?

Para realizar a assinatura via API, é necessário o `user_token` do usuário que irá assinar os documentos. Siga os passos abaixo:

1. Faça login no usuário que irá assinar os documentos.
2. Entre em Configurações>meu perfil&#x20;
3. No final da página, habilite a assinatura via API.
4.  Copie o token gerado e cole no parametro user\_token, dentro da request.\
    \
    \


    ![Como conseguir seu user token](https://github.com/AmandaAmani/documenta-ocurso/blob/main/user%20token.gif?raw=true)



***

### Como Conseguir o signer\_token?

Cada signatário (signer) criado na ZapSign possui um token individual. Para obter o token do signatário, siga os passos:

1. Crie ou acesse um documento.
2. Adicione o signatário ao documento.
3. Copie o token gerado para cada signatário.

{% hint style="warning" %}
**Atenção**: Certifique-se de estar utilizando o `signer_token` (token do signatário) e não o `document_token` (token do documento). Em caso de dúvidas, consulte [Tipos de tokens e como localizá-los.](../tipos-de-tokens-e-como-localiza-los.md)
{% endhint %}

![Assinatura em API](https://github.com/AmandaAmani/documenta-ocurso/blob/main/ass%20em%20api.gif?raw=true)



{% hint style="info" %}
Este **endpoint é assíncrono,** isto é, **você irá pedir a assinatura dos documentos e receberá uma resposta quase imediata da ZapSign.** Conforme os documentos forem ficando prontos, você irá receber os webhooks em sua aplicação um por vez.  Recomendamos o envio de 100 documentos por vez.
{% endhint %}
