# Excluir documento

## Excluir documento

<mark style="color:red;">`DELETE`</mark> `https://api.zapsign.com.br/api/v1/docs/{{doc_token}}/`

Exclua um documento. **Atenção: esse endpoint é apenas um soft delete do documento, isto é, ele continuará sendo acessível via API e salvo no banco de dados da ZapSign. O documento apenas ficará escondido da interface web para usuários finais.**\
\
A ação de exclusão é **sem volta**, e irá alterar os campos "deleted" e "deleted\_at" do documento.\
\
Obs: o método da requisição é DELETE. Caso utilize GET ou POST não surtirá o efeito desejado.

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

{% tabs %}
{% tab title="200 Documento excluído com sucesso" %}
````json
```json
{
    "sandbox": false,
    "external_id": "",
    "open_id": 178,
    "token": "1504d2e9-a4ad-42a1-a1a7-aaf752431b01",
    "name": "any-with-rubricas.pdf",
    "folder_path": "/",
    "status": "pending",
    "rejected_reason": null,
    "lang": "pt-br",
    "original_file": "https://zapsign.s3.amazonaws.com/2023/3/docs/15499007-18a8-4aac-a340-1abc13a80878/da85a4e3-7bd3-46b3-8c2e-261187f5ff71.pdf",
    "signed_file": null,
    "extra_docs": [],
    "created_through": "web",
    "deleted": true,
    "deleted_at": "2023-07-06T05:21:59.786161Z",
    "signed_file_only_finished": false,
    "disable_signer_emails": false,
    "brand_logo": "",
    "brand_primary_color": "",
    "created_at": "2023-03-15T14:01:17.805249Z",
    "last_update_at": "2023-07-06T05:21:59.786346Z",
    "created_by": {
        "email": "test@gmail.com"
    },
    "template": null,
    "signers": [
        {
            "external_id": "",
            "sign_url": "https://app.zapsign.com.br/verificar/3e497dcc-acb1-40c7-bf06-295e234c35a8",
            "token": "3e497dcc-acb1-40c7-bf06-295e234c35a8",
            "status": "new",
            "name": "John Doe",
            "lock_name": false,
            "email": "",
            "lock_email": false,
            "hide_email": false,
            "blank_email": false,
            "phone_country": "55",
            "phone_number": "9823668218",
            "lock_phone": false,
            "hide_phone": false,
            "blank_phone": false,
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null,
            "auth_mode": "assinaturaTela-tokenWhatsapp",
            "qualification": "",
            "require_selfie_photo": false,
            "require_document_photo": false,
            "geo_latitude": null,
            "geo_longitude": null,
            "redirect_link": "",
            "signature_image": null,
            "visto_image": null,
            "document_photo_url": "",
            "document_verse_photo_url": "",
            "selfie_photo_url": "",
            "selfie_photo_url2": "",
            "send_via": "whatsapp"
        }
    ],
    "answers": [],
    "auto_reminder": 3
}
```
````
{% endtab %}
{% endtabs %}
