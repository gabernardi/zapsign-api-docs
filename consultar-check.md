# Consultar Check

Este endpoint permite verificar o status da consulta e, caso esteja concluída, é possível obter o PDF com os resultados da verificação.

**GET** `https://api.zapsign.com.br/api/v1/checks/{{check_id}}/`&#x20;

### **Parâmetros de Path**

<table><thead><tr><th width="167">Nome</th><th width="130">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>check_id</td><td>string</td><td>Identificador da consulta</td></tr></tbody></table>

### **Header**

<table><thead><tr><th width="155">Nome</th><th width="118">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>Authorization*</td><td>string</td><td>Token da API com o prefixo "Bearer". Ex: <code>Bearer c7f35c84-7893-4087-b4fb-d1f06c23</code></td></tr></tbody></table>

### **Status do check**

* `not_started`: A consulta está na fila e a coleta de dados ainda não começou.
* `in_progress`: As informações começaram a ser coletadas, mas algumas fontes de dados ainda não foram finalizadas.
* `delayed`: Uma ou mais fontes de dados estão levando mais tempo que o esperado para concluir. A maioria já foi finalizada.
* `error`: A consulta foi finalizada, mas mais de 30% das fontes de dados retornaram erro.
* `completed`: 70% ou mais das fontes de dados foram finalizadas ou a maioria não terminou com erro.

Response

{% tabs %}
{% tab title="200 - sucesso" %}
```json
{
    "check_id": "CHK41dd253a3e9c018f3d4ee062ac98b091",
    "status": "completed",
    "company_name": "",
    "full_name": "MARIA",
    "last_name": "PEREZ",
    "date_of_birth": null,
    "issue_date": null,
    "national_id": "11111111",
    "passport": "",
    "native_national_id": "",
    "pep": "",
    "ptp": "",
    "foreign_id": "",
    "tax_id": "",
    "country": "CO",
    "native_country": "",
    "check_type": "person",
    "lang": "en",
    "region": "",
    "pdf_report": {
        "status": "completed",
        "url": "https://zapsign.s3.amazonaws.com/2025/4/truora/92001eac-2d94-4115-95d9-ef205693a7d0.pdf?AWSAccessKeyId=AKIASSSZJ7JCTI2ZRGWX&Signature=VddqJfz0B64a9VcWeeewDp8Gca4%3D&Expires=1743787456"
    },
    "created_at": "2025-04-02T20:09:47.017891Z",
    "last_update_at": "2025-04-02T20:24:15.872207Z"
}
```
{% endtab %}

{% tab title="404 - Não encontrado" %}
```html
Background check not found.
```
{% endtab %}
{% endtabs %}
