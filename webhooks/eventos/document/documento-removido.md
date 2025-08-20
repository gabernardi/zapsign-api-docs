---
description: doc_deleted
---

# Documento removido

Exemplo do corpo da requisição enviada pelo webhook de documento removiado.

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que o endpoint de [Detalhar documento](../../../documentos/detalhar-documento.md) seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

```json
{
  "event_type": "doc_deleted",
  "sandbox": false,
  "external_id": "id-suaaplicacao-e32213ds-243",
  "open_id": 23,
  "token": "cce11abf-abcd-abcd-a657-25b55f185f16",
  "name": "sample.pdf",
  "folder_path": "/",
  "status": "signed",
  "lang": "pt-br",
  "original_file": "https://zapsign.s3.amazonaws.com/asddasdasdasads08e1-48f5-8972-7b4e476dec9d/c11c4f25-79c7-4eea-8dcf-5434996a4251.pdf",
  "signed_file": "https://zapsign.s3.amazonaws.com/saddas1d5as16d5asads-2b89-460e-8c30-1644fbe8f249/a5bf7fe0-05d0-4d09-bbeb-0beaa91abc56.pdf",
  "created_through": "web",
  "deleted": true, // deleted: true significa que o documento foi excluído
  "deleted_at": "2021-06-07T19:22:33.932981Z", // data e horário do delete
  "signed_file_only_finished": false,
  "disable_signer_emails": false,
  "brand_logo": "",
  "brand_primary_color": "",
  "created_at": "2021-06-07T19:21:59.609067Z",
  "last_update_at": "2021-06-07T19:22:21.838310Z",
  "signers": [
    {
      "external_id": "",
      "token": "b14f141f-abcd-abcd-8dfa-0bdac0ec806a",
      "status": "signed",
      "name": "Fulano Silva",
      "lock_name": false,
      "email": "ola@zapsign.com.br",
      "lock_email": false,
      "phone_country": "55",
      "phone_number": "1155551111",
      "lock_phone": false,
      "times_viewed": 1,
      "last_view_at": "2021-06-07T19:22:12.875967Z",
      "signed_at": "2021-06-07T19:22:19.956056Z",
      "auth_mode": "assinaturaTela",
      "qualification": "",
      "require_selfie_photo": false,
      "require_document_photo": false,
      "geo_latitude": "-23.559298",
      "geo_longitude": "-46.683343",
      "resend_attempts": {
          "whatsapp": 0,
          "email": 0,
          "sms": 0
      },
      "cpf": "99999999999",
      "cnpj": "99999999999"
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
