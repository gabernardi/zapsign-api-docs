---
description: >-
  Este endpoint permite atualizar os dados de um documento desde que ele ainda
  esteja em andamento (ou seja, que não tenha sido finalizado nem cancelado).
---

# Update document

## Atualizar documento

<mark style="color:blue;">`PUT`</mark> `https://api.zapsign.com.br/api/v1/docs/{{doc_token}}/`

#### Condições

* O documento deve estar no estado **"em andamento"**.
* Somente os campos indicados abaixo podem ser modificados.

#### Path Parameters

<table><thead><tr><th width="116.28765869140625">Name</th><th width="106.6824951171875">Type</th><th>Description</th></tr></thead><tbody><tr><td>doc_token</td><td>string</td><td>Token do documento</td></tr></tbody></table>

#### Headers

<table><thead><tr><th width="166.25921630859375">Name</th><th width="105.82525634765625">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Body

<table><thead><tr><th width="168.664794921875">Campo</th><th width="108.22021484375">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td><code>name</code></td><td>string</td><td>Novo nome do documento principal.</td></tr><tr><td><code>date_limit_to_sign</code></td><td>string (YYYY-MM-DD)</td><td>Nova data limite para assinatura do documento.</td></tr><tr><td><code>folder_path</code></td><td>string</td><td>Caminho da pasta onde o documento será organizado na sua conta.</td></tr><tr><td><code>folder_token</code></td><td>string</td><td><p>Se preenchido, este campo terá prioridade sobre <code>folder_path</code>. Ele define o diretório com base no <strong>token da pasta</strong>, que pode ser obtido acessando o seguinte endereço:<br><code>https://app.zapsign.com.br/conta/documentos?pasta=&#x3C;token_da_pasta></code></p><p>Se você ainda não souber o token, navegue até a pasta desejada a partir de:<br><code>https://app.zapsign.com.br/conta/documentos</code><br>e copie o valor do parâmetro <code>pasta</code> na URL após acessar a pasta.</p></td></tr><tr><td><code>extra_docs</code></td><td>array de objetos</td><td>Lista de documentos extras vinculados que podem ser renomeados.</td></tr></tbody></table>

Estrutura extra\_docs

<table><thead><tr><th width="137.2222900390625">Campo</th><th width="127.2088623046875">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td><code>token</code></td><td>string</td><td>Token do documento extra já enviado anteriormente.</td></tr><tr><td><code>name</code></td><td>string</td><td>Novo nome para esse documento extra.</td></tr></tbody></table>

#### Exemplo body

```json
{
  "name": "Contrato de Serviços 2026",
  "date_limit_to_sign": "2025-06-26",
  "folder_path": "/Contratos/2026/Janeiro/",
  "extra_docs": [
    {
      "token": "token_do_documento_extra",
      "name": "Novo nome do documento extra"
    }
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
