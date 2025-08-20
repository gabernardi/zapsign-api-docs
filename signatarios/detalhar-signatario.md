# Detalhar signatário

Este endpoint é fundamental para acompanhar o progresso de assinaturas e obter informações precisas sobre o status de cada signatário, como se o documento foi visualizado ou já assinado. Ele permite que você acesse detalhes como nome, e-mail, número de visualizações e o momento exato da assinatura, fornecendo total visibilidade do processo.

<mark style="color:green;">**GET**</mark> `https://api.zapsign.com.br/api/v1/signers/{{signer_token}}/`

{% hint style="info" %}
Em dúvida sobre como encontrar seu signer token? Consulte a seção [Tipos de token e como  Localizá-los](../tipos-de-tokens-e-como-localiza-los.md)
{% endhint %}

#### Headers

<table><thead><tr><th width="162">Name</th><th width="111">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

{% tabs %}
{% tab title="200 Detalhes do signatário" %}
```json
    {
    "external_id": "",
    "token": "9534eabd-1111-4ba0-aaaa-37bfa6324257",
    "status": "signed",
    "name": "João da Silva",
    "lock_name": false,
    "email": "joao@gmail.com",
    "lock_email": false,
    "hide_email": false,
    "blank_email": true,
    "phone_country": "55",
    "phone_number": "11999881286",
    "lock_phone": false,
    "hide_phone": false,
    "blank_phone": true,
    "times_viewed": 5,
    "last_view_at": "2021-08-23T21:50:02.193406Z",
    "signed_at": "2021-08-23T21:48:41.783595Z",
    "auth_mode": "assinaturaTela",
    "qualification": "contratante",
    "require_selfie_photo": true,
    "require_document_photo": false,
    "geo_latitude": "-20.559258",
    "geo_longitude": "-48.683447",
    "redirect_link": "",
    "resend_attempts": {
        "whatsapp": 0,
        "email": 0,
        "sms": 0
    },
    "send_automatic_whatsapp_signed_file": false
}
```
{% endtab %}
{% endtabs %}

### Exemplo de requisição

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-b51eb4aa-9efe-4d91-afb4-5baba556d906?ctx=documentation" %}

