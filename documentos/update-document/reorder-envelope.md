---
description: >-
  Este endpoint permite definir a ordem em que os documentos serão exibidos
  dentro de um envelope específico. É útil quando a ordem de leitura ou
  assinatura dos documentos é relevante.
---

# Reordenar documentos de um envelope

## Atualizar documento

<mark style="color:blue;">`PUT`</mark> `https://api.zapsign.com.br/api/v1/docs/{doc_token}/document-display-order/`

#### Condições

* O documento identificado por `doc_token` deve ser um **envelope** (ou seja, um documento que agrupa vários arquivos).
* A reordenação só é permitida se o envelope estiver **em andamento**.
* É necessário incluir **todos** os tokens dos documentos que compõem o envelope, na ordem desejada.\
  Esses tokens estão disponíveis na resposta da criação do documento ou nos detalhes do envelope.

#### Path Parameters

<table><thead><tr><th width="116.28765869140625">Name</th><th width="106.6824951171875">Type</th><th>Description</th></tr></thead><tbody><tr><td>doc_token</td><td>string</td><td>Token do documento</td></tr></tbody></table>

#### Headers

<table><thead><tr><th width="166.25921630859375">Name</th><th width="105.82525634765625">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Body

<table><thead><tr><th width="168.664794921875">Campo</th><th width="108.22021484375">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>document_display_order</td><td>array de string</td><td>Lista ordenada de tokens dos documentos, indicando a nova ordem de exibição.</td></tr></tbody></table>

#### Exemplo body

```json
{
  "document_display_order": [
    "6a4c7b7d-433e-4faf-a4b1-1f96bbf72c68",    
    "09d983a1-7c26-472a-a2ef-8ee10470b5ed",
    "9f8c63bb-eb1b-461d-8ede-0ae90d75c18a"
  ]
}


```

{% tabs %}
{% tab title="200 Sucesso" %}
```javascript
{
    "message": "Documento atualizado corretamente"

}
```
{% endtab %}
{% endtabs %}
