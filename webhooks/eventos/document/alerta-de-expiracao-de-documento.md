# Alerta de expiração de documento

Exemplo de corpo da requisição enviada pelo webhook de Alerta de expiração de documento.

```
{
  "sandbox": false,
  "external_id": "None",
  "open_id": 1491,
  "token": "xxxxxxxx.xxxxxx.xxxxx.xxxxx.",
  "name": "Documento Teste",
  "folder_path": "/",
  "folder_token": null,
  "status": "pending",
  "rejected_reason": null,
  "lang": "pt-br",
  "original_file": "https://zapsign.test.com/pdf/1",
  "signed_file": null,
  "extra_docs": [],
  "created_through": "api",
  "deleted": false,
  "deleted_at": null,
  "signed_file_only_finished": false,
  "disable_signer_emails": false,
  "brand_logo": "",
  "brand_primary_color": "",
  "created_at": "2025-07-10T19:07:47.849390Z",
  "last_update_at": "2025-07-10T19:07:47.849404Z",
  "created_by": {
    "email": "test@zapsign.com.br"
  },
  "template": null,
  "signers": [
    {
      "external_id": "",
      "sign_url": "https://app.zapsign.com.br/verificar/test",
      "token": "xxxxxxxx-xxxxx-xxxxx-xxxxx",
      "status": "new",
      "name": "John Doe",
      "lock_name": false,
      "email": "johndoe@zapsign.com.br",
      "lock_email": false,
      "hide_email": false,
      "blank_email": false,
      "phone_country": "55",
      "phone_number": "11999999999",
      "lock_phone": false,
      "hide_phone": false,
      "blank_phone": false,
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
      "signature_image": "testbase64",
      "visto_image":"testbase64",
      "document_photo_url": "",
      "document_verse_photo_url": "",
      "selfie_photo_url": "",
      "selfie_photo_url2": "",
      "send_via": "email",
      "resend_attempts": null,
      "cpf": "12345678900",
      "cnpj": "",
      "send_automatic_whatsapp_signed_file": null,
      "liveness_photo_url": "",
      "selfie_validation_type": "none",
      "ip": null
    }
  ],
  "answers": [],
  "auto_reminder": 0,
  "signature_report": null,
  "tsa_country": null,
  "use_timestamp": true,
  "metadata": [
    {
      "key": "chave",
      "value": "valor"
    }
  ],
  "event_type": "doc_expiration_alert",
  "expiration_date": "2025-07-10T23:59:59.000999+00:00"
}
```
