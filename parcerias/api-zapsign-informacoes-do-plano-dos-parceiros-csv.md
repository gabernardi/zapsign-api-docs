# API ZapSign: Informações do Plano dos Parceiros (CSV)

Este endpoint permite exportar um arquivo CSV com informações do plano e métricas de uso da conta autenticada e de suas contas parceiras. Ele é útil para acompanhar, em um único arquivo, dados como nome da conta, marca, plano atual, saldo de créditos, status da assinatura, período do plano e métricas de uso no intervalo consultado.

### Endpoint

GET `https://api.zapsign.com.br/api/v1/info-plan/partners-csv/`

### Parâmetros de Consulta (Query Parameters)

| **Nome**     | **Tipo** | **Descrição**                                              |
| ------------ | -------- | ---------------------------------------------------------- |
| `start_date` | string   | Data inicial do período consultado (YYYY-MM-DD). Opcional. |
| `end_date`   | string   | Data final do período consultado (YYYY-MM-DD). Opcional.   |

Regras do período:

* O intervalo máximo permitido é de 30 dias.
* Se nenhum parâmetro for enviado, o endpoint considera os últimos 30 dias.
* Se apenas `start_date` for enviado, `end_date` será assumido como a data atual.
* Se apenas `end_date` for enviado, `start_date` será assumido como 30 dias antes da data atual.
* `start_date` deve ser menor ou igual a `end_date`.

### Cabeçalhos (Headers)

* Authorization: `Bearer SEU_API_TOKEN`

### Colunas do CSV

O arquivo CSV contém uma linha para a conta autenticada e uma linha para cada conta parceira vinculada a ela. As colunas são:

* id, name, brand\_name: Identificação da conta e nome da marca.
* plan\_name, credits, status: Nome do plano, saldo de créditos e status da assinatura.
* period, current\_period\_end: Periodicidade (monthly ou annual) e data de término do ciclo atual.
* Métricas de uso: `documents_created`, `envelopes_created`, `qty_sms`, `qty_whatsapp`, `qty_digital_certificate`, `qty_biometry_sov`, `qty_facial_recognition`, `qty_identity_verification`, `qty_liveness`.

### Exemplo de Requisição (curl)

Bash

```
curl --request GET \
  --url 'https://api.zapsign.com.br/api/v1/info-plan/partners-csv/?start_date=2026-03-01&end_date=2026-03-04' \
  --header 'Authorization: Bearer SEU_API_TOKEN'
```

### Observações Importantes

* O retorno deste endpoint é um arquivo CSV (`text/csv`), e não um JSON.
* Caso uma conta não tenha assinatura válida no período, o campo status será `no_subscription`.
* Assinaturas com status `unpaid` não entram como plano válido no CSV.

### Respostas de Erro

400 - Parâmetros inválidos

Ocorre quando o formato da data está incorreto ou o intervalo excede 30 dias.

Exemplo:

JSON

```
{
  "non_field_errors": [
    "Date range cannot exceed 30 days"
  ]
}
```

401 - Não autenticado

Ocorre quando o token de API é inválido ou não foi fornecido.

JSON

```
{
  "detail": "Invalid API token."
}
```

***

Desej
