---
description: Entenda os eventos recebidos via webhooks
---

# Eventos

### Lista de eventos

A ZapSign envia os seguintes eventos por webhook:

* **`doc_created`**\
  Este evento é enviado quando um documento é criado.
* **`created_signer`**\
  Este evento é enviado quando um novo signatário é adicionado a um documento em andamento.
* **`doc_deleted`**\
  Notifica quando um documento foi excluído, seja pela plataforma ou via API.
* **`doc_signed`**\
  Acionado quando um signatário assina o documento. O webhook especifica qual signatário assinou o documento.
* **`doc_refused`**\
  Indica que um documento foi recusado pelo signatário.
* **`email_bounce`**\
  Notifica sobre falhas na entrega de e-mails.
* **`signature_notification_sent`**\
  Notifica quando o documento é enviado ao signatário por e-mail ou WhatsApp (parâmetro `send_automatic_email` ou `send_automatic_whatsapp`).
* **`doc_viewed`**\
  Notifica quando o signatário visualizou o documento (abriu o link de assinatura).
* **`doc_read_confirmation`**\
  Notifica quando o signatário confirma a leitura do documento (botão "Continuar" após visualizar o documento).
* **`signer_authentication_failed`**\
  Notifica quando o signatário excedeu o número máximo de tentativas para validar sua identidade através dos métodos Reconhecimento Facial e Validação de Identidade.
* **`doc_expired`**\
  Este evento é enviado quando um documento com data limite para assinatura é expirado.
* **`doc_expiration_alert`**\
  Este evento é enviado quando um documento com data limite para assinatura esta prestes á expirar. O evento será disparado 7 - 3 - 1 dia antes da expiração ser efetivada.&#x20;



Você poderá diferenciar um do outro pelo atributo "event\_type" que seguirá junto de todo webhook.&#x20;

```
"event_type": "doc_created"
```

Veja o body de cada evento nos próximos capítulos!
