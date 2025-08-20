---
description: email_bounce
---

# Email bounce

**Exemplo do conteúdo do webhook.** O campo "error" informa o motivo do erro no envio do documento.

{% hint style="info" %}
**Dica**: você pode usar o endpoint "[Atualizar signatário](../../../signatarios/atualizar-signatario.md)" para alterar o e-mail e reenviar o e-mail com o parâmetro `send_automatic_email`.
{% endhint %}

```json
{
  "email": "teste@truora.com",
  "token": "853fda7d-ca1c-45cf-829d-9006a4bdfb9e",
  "type": "link_email",
  "status": "dropped",
  "status_code": null,
  "error": "ZapSign did not send the message to this email address because there was a previous delivery failure to this same email. We recommend checking the email, and if you believe there was an error, please contact support@zapsign.com.br.",
  "delivered": false,
  "event_type": "email_bounce"
}
```
