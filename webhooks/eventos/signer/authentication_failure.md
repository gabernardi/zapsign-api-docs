---
description: signer_authentication_failed
---

# Falha na Validação

Este evento do webhook é acionado quando o signatário atinge o número máximo permitido de tentativas (3 tentativas) para validar sua identidade usando os métodos de autenticação disponíveis na ZapSign: **Reconhecimento Facial, Biometría Gov+ e** **Validação de Identidade**.

Quando esta notificação é recebida, significa que o signatário não pode continuar com o processo de assinatura eletrônica até que o cliente tome uma ação.

#### **Ações possíveis que o cliente pode realizar:**

* **Alterar o método de autenticação:** Utilizar o endpoint [Atualizar signatário](../../../signatarios/atualizar-signatario.md) para mudar o método de autenticação para uma alternativa (por exemplo, OTP via SMS ou e-mail).
* [**Reiniciar tentativas de validação:** ](../../../signatarios/reset-signer-attempts.md)Com este endpoint, o signatário terá três novas tentativas para realizar a validação.

Este evento permite que o cliente tome decisões rápidas e eficientes para garantir a continuidade e a segurança do processo de assinatura eletrônica.

{% hint style="info" %}
Na resposta, o parâmetro **authentication\_failure\_reason** explica o motivo da falha na validação.
{% endhint %}

```json
{
    "sandbox": false,
    "external_id": "",
    "open_id": 256,
    "token": "514ca933-f995-443f-b940-7e82ee5f7c5",
    "name": "Documento exemplo",
    "folder_path": "/",
    "status": "pending",
    "rejected_reason": null,
    "lang": "en",
    "original_file": "https://zapsign.s3.amazonaws.com/dev/2025/3/docs/92b22e27-b091-4398-940d-6d9976ecdbed/b3871a48-2636-4562-9919-e9dae326db55.pdf?AWSAccessKeyId=AKIASUFZJ7JCTI2ZRGWX&Signature=h7Fab%2F%2F1TggGxgbztlXaDcrxHCg%3D&Expires=1742339713",
    "signed_file": null,
    "extra_docs": [],
    "created_through": "web",
    "deleted": false,
    "deleted_at": null,
    "signed_file_only_finished": false,
    "disable_signer_emails": false,
    "brand_logo": "",
    "brand_primary_color": "",
    "created_at": "2025-03-18T22:12:37.843154Z",
    "last_update_at": "2025-03-18T22:12:37.843171Z",
    "created_by": {
        "email": "silvana@zapsign.com.br"
    },
    "template": null,
    "signers": [{
        "external_id": "",
        "sign_url": "https://app.zapsign.com.br/verificar/8XX394fa-cXXX48c2-8d50-2935f5XXX363",
        "token": "821394fa-c7af-48c2-8d50-2935f5f39363",
        "status": "link-opened",
        "name": "Silvana Alvarez",
        "lock_name": false,
        "email": "email@email.com",
        "lock_email": false,
        "hide_email": false,
        "blank_email": false,
        "phone_country": "55",
        "phone_number": "",
        "lock_phone": false,
        "hide_phone": false,
        "blank_phone": true,
        "times_viewed": 1,
        "last_view_at": "2025-03-18T22:12:45.255310Z",
        "signed_at": null,
        "auth_mode": "assinaturaTela",
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
        "send_via": "",
        "resend_attempts": null,
        "cpf": "",
        "cnpj": "",
        "send_automatic_whatsapp_signed_file": null,
        "liveness_photo_url": "",
        "selfie_validation_type": "identity-verification-global",
        "ip": null
    }],
    "answers": [],
    "auto_reminder": 0,
    "signature_report": null,
    "tsa_country": null,
    "use_timestamp": true,
    "metadata": [],
    "event_type": "signer_authentication_failed",
    "unauthenticated_signer": {
        "external_id": "",
        "sign_url": "https://app.zapsign.com.br/verificar/8XX394fa-cXXX48c2-8d50-2935f5XXX363",
        "token": "821394fa-c7af-48c2-8d50-2935f5f39363",
        "status": "link-opened",
        "name": "Silvana Alvarez",
        "lock_name": false,
        "email": "email@email.com",
        "lock_email": false,
        "hide_email": false,
        "blank_email": false,
        "phone_country": "55",
        "phone_number": "",
        "lock_phone": false,
        "hide_phone": false,
        "blank_phone": true,
        "times_viewed": 1,
        "last_view_at": "2025-03-18T22:12:45.255310Z",
        "signed_at": null,
        "auth_mode": "assinaturaTela",
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
        "send_via": "",
        "resend_attempts": null,
        "cpf": "",
        "cnpj": "",
        "send_automatic_whatsapp_signed_file": null,
        "liveness_photo_url": "",
        "selfie_validation_type": "identity-verification-global",
        "ip": null,
        "max_attempts": 2,
        "attempts_used": 2,
        "authentication_failure_reason": "Unsuccessful validation of Silvana Alvarez due to Attempted deceit, device screen used"
    }
}
```
