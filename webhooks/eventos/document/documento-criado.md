---
description: doc_created
---

# Documento criado

Exemplo de corpo da requisição enviada pelo webhook de documento criado.

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que o endpoint de [Detalhar documento](../../../documentos/detalhar-documento.md) seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

```json
{
  "event_type": "doc_created",
  "sandbox": false,
  "external_id": "id-suaaplicacao-e32213ds-243",
  "open_id": 23,
  "token": "cce11abf-abcd-abcd-a657-25b55f185f16",
  "name": "sample.pdf",
  "folder_path": "/",
  "status": "pending",
  "lang": "pt-br",
  "original_file": "https://zapsign.s3.amazonaws.com/c11c4f2c11c4f2/c11c4f2/c11c4f25-79c7-4eea-8dcf-5434996a4251.pdf",
  "signed_file": null,
  "created_through": "web",
  "deleted": false,
  "deleted_at": null,
  "signed_file_only_finished": false,
  "disable_signer_emails": false,
  "brand_logo": "",
  "brand_primary_color": "",
  "created_at": "2021-06-07T19:21:59.609067Z",
  "last_update_at": "2021-06-07T19:21:59.609094Z",
  "signers": [
    {
      "external_id": "",
      "token": "b14f141f-aaaa-425e-8dfa-0bdac0ec806a",
      "status": "new",
      "name": "ola@zapsign.com.br",
      "lock_name": false,
      "email": "ola@zapsign.com.br",
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
      "resend_attempts": null,
      "cpf": null,
      "cnpj": null
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
