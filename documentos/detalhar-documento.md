# Detalhar documento

## Detalhar documento

<mark style="color:blue;">`GET`</mark> `https://api.zapsign.com.br/api/v1/docs/{{doc_token}}/`

Esse endpoint permite que você veja todos os atributos do seu documento, como status, signatários e URL do arquivo original e assinado.

#### Path Parameters

| Name       | Type   | Description        |
| ---------- | ------ | ------------------ |
| doc\_token | string | Token do documento |

#### Headers

<table><thead><tr><th>Name</th><th width="189">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

{% tabs %}
{% tab title="200 Documento encontrado." %}
```javascript
{
    "open_id": 5,
    "token": "eb9c367a-e62f-4992-8360-b0219deaeecc",
    "status": "pending",
    "name": "Contrato de Admissão João",
    "original_file": "https://zapsign.s3.amazonaws.com/pdf/62xxxx7-d8fc-4392-8575-f3c46c3cfc7a/df6bac91-2766-4182-8c8b-ded5287e4c0f.pdf",
    "signed_file": null,
    "created_at": "2020-04-16T03:33:46.241747Z",
    "last_update_at": "2020-04-16T03:33:46.241775Z",
    "signers": [
        {
            "token": "921c115d-4a6e-445d-bdca-03fadedbbc0b",
            "status": "new",
            "name": "João da Silva",
            "email": "",
            "phone_country": "",
            "phone_number": "",
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null
        },
        {
            "token": "07fb0a0a-4b7d-49a5-bd7b-4958265c4e46",
            "status": "new",
            "name": "Fulano Siclano",
            "email": "",
            "phone_country": "",
            "phone_number": "",
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null
        }
    ]
}
```
{% endtab %}
{% endtabs %}

Os possíveis status de um **documento** são:

* **pending** (em curso)&#x20;
* **signed** (todos signatários assinaram o documento)

Os possíveis status de um **signatário** são:

* **new** (signatário foi criado)
* **link-opened** (abriu o link do documento pelo menos uma vez)
* **signed** (assinou o documento)

{% hint style="info" %}
**Dica:** em vez de consultar os documentos várias vezes ao dia, utilize nossos [webhooks](https://docs.zapsign.com.br/webhooks/como-funciona). Além de ser uma economia da capacidade computacional dos nossos e seus servidores, você também conseguirá dar um feedback em tempo real ao seu usuário, e não a cada N minutos.
{% endhint %}

### Exemplo de resposta

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que este endpoint seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

```javascript
{
    "sandbox": false,
    "external_id": "",
    "open_id": 16,
    "token": "965ea3fa-938a-4b7d-84ed-7d7598b17231",
    "name": "sample.pdf",
    "folder_path": "/",
    "status": "pending",
    "lang": "pt-br",
    "original_file": "https://zapsign.s3.amazonaws.com/aaa/aaa5e7a6-56dd-4ad9-9a1c-6e7022fbfafa/658bee7b-1dd7-442c-b426-4f111aaedffb.pdf",
    "signed_file": null,
    "extra_docs": [
        {
            "open_id": 17,
            "token": "50c7d90e-ead6-46b5-99d6-33d2d3b9a31f", //utilize esse token caso queira posicionar assinaturas no documento extra
            "name": "doc extra1.pdf",
            "original_file": "https://zapsign.s3.amazonaws.com/aaa/48025712-b429-4216-8a33-d90c575d0b7f/0e2d0a87-a0f6-4a49-a05f-7a439fd7308e.pdf",
            "signed_file": null
        },
        {
            "open_id": 18,
            "token": "c8f2a1c4-58f2-4240-bcf5-f1dc34b07a7c", //utilize esse token caso queira posicionar assinaturas no documento extra
            "name": "doc extra2.pdf",
            "original_file": "https://zapsign.s3.amazonaws.com/aaa/52d81e46-64ea-4a2d-9171-c5c8907d895c/9b1353c8-73cd-4cca-a342-ba1e7f0354a9.pdf",
            "signed_file": null
        },
        {
            "open_id": 19,
            "token": "733b7538-cd38-41c1-abe7-07d06e4f6b8d", //utilize esse token caso queira posicionar assinaturas no documento extra
            "name": "doc extra3.pdf",
            "original_file": "https://zapsign.s3.amazonaws.com/dev/2021/8/api/57a8bb75-641f-4cf6-962c-587774188dce.pdf",
            "signed_file": null
        }
    ],
    "created_through": "api",
    "deleted": false,
    "deleted_at": null,
    "signed_file_only_finished": false,
    "disable_signer_emails": false,
    "brand_logo": "",
    "brand_primary_color": "",
    "created_at": "2021-08-23T22:04:06.650460Z",
    "last_update_at": "2021-08-23T22:44:06.901255Z",
    "created_by": {
        "email": "teste@gmail.com"
    },
    "signers": [
        {
            "external_id": "",
            "token": "ca63b929-c053-4f7b-8680-8f0380ca4a57",
            "status": "new",
            "name": "João da Silva",
            "lock_name": false,
            "email": "",
            "lock_email": false,
            "phone_country": "55",
            "phone_number": "",
            "lock_phone": false,
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null,
            "auth_mode": "assinaturaTela",
            "qualification": "",
            "require_selfie_photo": false,
            "require_document_photo": false,
            "geo_latitude": null,
            "geo_longitude": null,
            "redirect_link": "",
            "resend_attempts": {
                "whatsapp": 0,
                "email": 0,
                "sms": 0
            },
            "send_automatic_whatsapp_signed_file": null,
        }
    ],
    "answers": [ // lista de variaveis e respostas no modelo dinamico (caso o documento tenha sido criado através de um modelo dinamico)
        {
            "variable": "NOME COMPLETO",
            "value": "Nome Teste"
        },
        {
            "variable": "NÚMERO DO CPF",
            "value": "99999999999"
        },
        {
            "variable": "ENDEREÇO COMPLETO",
            "value": "Endereço teste"
        }
    ]
}
```

Obs: caso você faça um GET em um token de um extra\_doc (documento extra, não o documento principal), a resposta será muito mais curta e conterá o token do documento principal, por exemplo:

```javascript
{
    "open_id": 22,
    "token": "a35c3333-5c6e-4dbf-99cc-fc6345f91d8c",
    "name": "doc extra 1.pdf",
    "original_file": "https://zapsign.s3.amazonaws.com/aaa/f42c4315-ccf9-48c9-97df-ddd14ec5b865/e3a670c8-c811-45ef-a392-08b68db49a41.pdf",
    "signed_file": null,
    "parent_doc_token": "965ea3fa-938a-4b7d-84ed-7d7598b17231"
}
```
