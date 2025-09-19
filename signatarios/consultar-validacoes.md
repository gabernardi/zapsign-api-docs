---
description: >-
  Este endpoint retorna todas as tentativas de validação de identidade
  realizadas por um signatário, incluindo o status, motivo de falha (se houver)
  e as informações extraídas do documento.
hidden: true
---

# Consultar validações

<mark style="color:green;">**GET**</mark> `https://api.zapsign.com.br/api/v1/signer-verification-details/{{signer_token}}/`

#### Headers

<table><thead><tr><th width="162">Name</th><th width="128">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

### Exemplo response

{% hint style="warning" %}
O endpoint retorna todas as tentativas feitas pelo signatário, permitindo acompanhar o histórico de validações e entender possíveis motivos de falha.
{% endhint %}

```
{
    "token": "0abe0677-72d7-4816-9ba8-317145d387ea",
    "selfie_validation_type": "identity-verification-global",
    "validations": [
        {
            "validation_number": "cd461e6a-a5d5-4bd7-8e50-20263c9f64a9",
            "status": "success",
            "reason": "",
            "created_at": "2025-06-05T18:51:26.286366Z",
            "document_photo_url": "https://zapsign.s3.amazonaws.com",
            "document_verse_photo_url": "https://zapsign.s3.amazonaws.com/",
            "selfie_photo_url": "",
            "selfie_photo_url2": "",
            "document_ocr": {
                "process_id": "cd461e6a-a5d5-4bd7-8e50-20263c9f64a9",
                "name": "MARIA",
                "last_name": "SOUZA",
                "document_type": "ID_CARD",
                "document_number": "11111111",
                "date_of_birth": "1980-01-01",
                "document_country": "BR"
            }
        },
        {
            "type": "Name validation",
            "status": "success",
            "reason": "",
            "created_at": "2025-06-05T18:51:26.286366Z",
        },
    ]
}

```

#### Sobre o campo `selfie_validation_type`

O campo `selfie_validation_type` indica qual método de validação foi utilizado. O endpoint retorna as validações referentes aos seguintes métodos:

<table><thead><tr><th width="256">Selfie_validation_type</th><th>Descrição</th></tr></thead><tbody><tr><td><code>liveness-document-match</code></td><td>Reconhecimento facial com upload do documento de identidade e gravação do rosto. Valida se a pessoa é a mesma do documento.</td></tr><tr><td><code>liveness-NXCD</code></td><td>Valida se a pessoa está presente na assinatura através de vídeo passivo (liveness).</td></tr><tr><td><code>face-match-and-datavalid</code></td><td>Autenticação facial com verificação nos dados do governo (Serpro), confirmando CPF e CNH. Somente Brasil.</td></tr><tr><td><code>identity-verification-global</code></td><td>Validação global da identidade, incluindo autenticação do documento e reconhecimento facial.</td></tr><tr><td><code>identity-verification</code></td><td>Validação da identidade, incluindo autenticação do documento e reconhecimento facial.</td></tr></tbody></table>
