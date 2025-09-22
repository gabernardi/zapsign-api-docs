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
            "type": "Identity verification",
            "validation_number": "cd461e6a-a5d5-4bd7-8e50-20263c9f64a9",
            "status": "success",
            "reason": "",
            "created_at": "2025-06-05T18:51:26.286366Z",
            "document_photo_url": "https://zapsign.s3.amazonaws.com",
            "document_verse_photo_url": "https://zapsign.s3.amazonaws.com/",
            "selfie_photo_url": "",
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

### Sobre o resultado da validação

Este endpoint permite consultar o **resultado do processo de validação** definido no parâmetro `selfie_validation_type`.&#x20;

Cada tipo de validação possui **etapas específicas** que verificam diferentes aspectos do documento e/ou do rosto do signatário. Dentro de cada etapa existem **sub-validações**, e para cada uma delas a resposta do endpoint retorna:

* O **status** (sucesso ou falha).
* O campo **reason**, que explica o motivo da falha, quando aplicável.

A seguir estão detalhados os diferentes tipos de validação disponíveis e as etapas correspondentes.

#### liveness-document-match

Este método realiza duas validações principais

* **Document recognition:** verifica se a foto enviada da frente do documento realmente corresponde a um documento de identidade e se contém uma foto
  * Importante: não aplica modelos avançados de fraude nem identifica casos de “documento em foto”.
* **Face match:** compara o vídeo passivo do rosto do signatário com a foto do documento apresentado, garantindo que se trata da mesma pessoa. O resultado inclui a URL da foto de rosto capturada.

Se as duas validações forem bem-sucedidas, o signatário está autorizado a concluir a assinatura do documento.

#### face-match-and-datavalid&#x20;

_Disponível apenas para Brasil – CNH._ Este método realiza uma única validação:

* Compara o nome e CPF com as bases da Serpro, além de verificar se coincidem com a pessoa identificada no vídeo passivo feito durante a assinatura.

#### identity-verification-global

Este método realiza três validações complementares:

* **Identity verification**: valida se o documento é real utilizando modelos de detecção de fraude e retorna os dados extraídos automaticamente (ocr), incluindo:
  * `name`
  * `last_name`
  * `document_type`
  * `document_number`
  * `date_of_birth`
  * `document_country`
* **Name validation:** compara o nome extraído do documento com o nome informado pelo signatário. A validação é considerada aprovada se a similaridade for maior que 75%.
* **Validação de CPF** (Brasil): quando o documento for do Brasil e contiver CPF, é feita uma verificação automática junto à Receita Federal.

#### identity-verification&#x20;

_Disponível para Colômbia, México, Chile e Peru._ Este método realiza duas validações:

* **Identity verification**: valida que o documento é real com modelos de fraude, realiza consulta em bases de dados do governo e garante que o vídeo passivo corresponda à mesma pessoa do documento.
* **Name validation:** compara o nome extraído do documento com o nome informado pelo signatário, aplicando a mesma lógica de similaridade usada no método _identity-verification-global_.

