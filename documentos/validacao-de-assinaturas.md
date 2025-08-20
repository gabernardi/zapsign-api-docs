---
description: >-
  Ideal para automatizar a checagem de documentos e garantir que estejam
  completos e inalterados.
---

# Validação de assinaturas

A ZapSign disponibiliza um endpoint que valida se um PDF foi corretamente assinado e mantido íntegro, assegurando conformidade com padrões de segurança e validade jurídica.&#x20;

\
Este endpoint permite validar a integridade de assinaturas digitais em um arquivo PDF. A validação confirma se:\


* O PDF contém uma ou mais assinaturas digitais;
* Todas as assinaturas foram emitidas pela ZapSign;
* As assinaturas são criptograficamente válidas;
* O documento não foi alterado após a assinatura;
* Não há assinaturas pendentes ou recusadas.

{% hint style="warning" %}
Em caso de documento inválido, o endpoint retorna uma mensagem com a razão pela qual foi invalidado.
{% endhint %}

***

### Como utilizar:

\
Envie uma requisição com o método `POST`  em formato `multipart/form-data`  contendo o arquivo PDF no campo `file` .\
\
<mark style="color:yellow;">`POST`</mark>`https://api.zapsign.com.br/api/v1/validate-pdf-signature`

#### Headers

| Name         | Type                | Description |
| ------------ | ------------------- | ----------- |
| Content-Type | multipart/form-data |             |

#### Request Body (form-data)

| Name | Type          | Description                |
| ---- | ------------- | -------------------------- |
| file | arquivo (PDF) | Arquivo PDF a ser validado |

<figure><img src="../.gitbook/assets/validar doc1 (1).gif" alt=""><figcaption><p>Chamando o endpoint via Postman</p></figcaption></figure>

***

### Exemplo de Resposta

{% tabs %}
{% tab title="200- Documento Válido" %}
```
{
    "isValid": true,
    "message": "Document signed correctly (CN=ZAPSIGN) and without subsequent notes.",
    "authority": "AC Certisign Multipla G7",
    "signingDate": "05/20/2025 20:56:55",
    "commonName": "ZAPSIGN PROCESSAMENTO DE DADOS LTDA"
}
```
{% endtab %}

{% tab title="200-Documento inválido" %}
```json
{
    "isValid": false,
    "message": "Untracked exception: Incorrect file header",
    "authority": "N/A",
    "signingDate": "N/A",
    "commonName": "N/A"
}
```
{% endtab %}

{% tab title="Erro 400" %}
```
{
    "error": "Nenhum arquivo foi enviado."
}
```
{% endtab %}
{% endtabs %}

***

### Possíveis mensagens em caso de documento inválido

| Mensagem                                                                                       | Descrição                                                                              |
| ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Signature `signature1` does not cover the whole document                                       | A assinatura não cobre o documento inteiro                                             |
| Certificate validation failed: CN is not ZAPSIGN PROCESSAMENTO DE DADOS LTDA                   | O documento contém uma ou mais assinaturas que não foram realizadas pela ZapSign       |
| Signature `signature1` not valid because the document contains pending signature indicators    | O documento é inválido porque contém indicadores de que existem assinaturas pendentes  |
| Signature `signature1` is not valid because the document contains refused signature indicators | O documento é inválido porque contem indicadores de que existem assinaturas recusadas  |
| Document does not contain digital signatures                                                   | O documento não está assinado                                                          |
| Signature `signature1` is not cryptographically valid                                          | O documento contém uma assinatura inválida ou foi alterado depois de ter sido assinado |

***

#### Converse com o Gepeto! <a href="#converse-com-o-gepeto" id="converse-com-o-gepeto"></a>

Tem alguma duvida? Utilize nossa inteligência artificial treinada com toda a documentação da API

{% embed url="https://n8n.zapsign.com.br/webhook/fee2c476-7f23-4a4f-8928-5c7ab081ffcd/chat" %}
