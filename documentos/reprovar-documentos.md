---
description: >-
  Este endpoint permite reprovar um documento individual ou um envelope
  (conjunto de documentos).
---

# Reprovar documentos

<mark style="color:green;">`POST`</mark>`https://api.zapsign.com.br/api/v1/refuse/`

**Como Usar:**\
Envie um payload em formato JSON com os seguintes campos:

* **doc\_token:** (string) do documento principal no formato JSON.

**Condições**

* O documento deve estar com o status “Em andamento”.
* Ao criar o documento, o parâmetro `allow_refuse_signature` deve estar como true.

**Observações:**

* Quando um documento é recusado, ele recebe a marca d’água **"Documento recusado"** e fica impossibilitado de ser assinado futuramente.
* A resposta do endpoint será retornada no formato JSON.



#### Headers

<table><thead><tr><th width="156">Name</th><th width="93">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Request Body

<table><thead><tr><th>Name</th><th width="147">Type</th><th>Description</th></tr></thead><tbody><tr><td>doc_token<mark style="color:red;">*</mark></td><td>string</td><td>Token do documento</td></tr></tbody></table>

Response

```
200 sucesso
{
    "message": "Documento recusado com sucesso. Lembrete: este endpoint é assíncrono, então aguarde os PDF finais ficarem prontos via webhooks ou confira-os daqui alguns minutos."
}
```

