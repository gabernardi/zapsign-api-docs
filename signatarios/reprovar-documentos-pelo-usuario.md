# Reprovar documentos pelo usuário

<mark style="color:green;">`POST`</mark>`https://api.zapsign.com.br/api/v1/refuse/by-user/`

Este endpoint permite reprovar um documento individual ou um envelope (conjunto de documentos em lote) enviando as informações necessárias no corpo da requisição.

#### Como Usar:

Envie um payload no formato JSON contendo os seguintes campos:

* **doc\_token**: (string) Token do documento a ser reprovado.
* **user\_token**: (string) Token do usuário que está reprovando o documento.
* **signer\_token**: (string) Token do signatário relacionado ao documento.
* **rejected\_reason**: (string, opcional) Motivo da recusa do documento.

Confira mais sobre os[ tipos de tokens aqui](../tipos-de-tokens-e-como-localiza-los.md)

**Condições**

* O documento deve estar com o status “Em andamento”.
* Ao criar o documento, o parâmetro allow\_refuse\_signature deve estar como true.
* O e-mail do signatário e do usuário deve ser o mesmo.

**Observações:**

* O sistema aplicará automaticamente a marca d'água padrão: **"Documento recusado"**.
* A resposta do endpoint também será retornada no formato JSON.
* O documento deve estar com o status “**Em curso**”.



**Headers**

<table><thead><tr><th width="156">Name</th><th width="111">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Request Body

| Name                                            | Type   | Description         |
| ----------------------------------------------- | ------ | ------------------- |
| doc\_token<mark style="color:red;">\*</mark>    | string | Token do documento  |
| user\_token<mark style="color:red;">\*</mark>   | string | Token do usuário    |
| signer\_token<mark style="color:red;">\*</mark> | string | Token do signatário |
| rejected\_reason                                | string | Motivo da recusa    |

Exemplo Request

```json
{
    "doc_token":"e082d806-6b31-4e27-ae9a-e16b603a70b3",
    "user_token":"97ab0000-36d4-xxxx-9ded-00005d690xxxx",
    "signer_token": "8be272d8-20a9-xx-899c-db4edbb846cd",
    "rejected_reason": ""
}
```

**Response**

{% tabs %}
{% tab title="200 sucesso" %}
```
{
    "message": "Documento recusado com sucesso. Lembrete: este endpoint é assíncrono, então aguarde os PDF finais ficarem prontos via webhooks ou confira-os daqui alguns minutos."
}
```
{% endtab %}

{% tab title="403" %}
```json
{
    "error": "A reprovação deste documento não é permitida."
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "error": "O e-mail do signatário e do usuário são diferentes"
}
```
{% endtab %}
{% endtabs %}
