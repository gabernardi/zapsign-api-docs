# Histórico de atividades do documento

O intuito principal desse endpoint é possibilitar a recuperação do histórico de atividades para um documento especifico. A rota ainda provê a possibilidade de retorno no formato padrão JSON, ou em formato de arquivo PDF para download.

## Coletar Histórico de atividades

<mark style="color:blue;">`GET`</mark> `https://api.zapsign.com.br/api/v1/docs/signer-log/{{doc_token}}?download_pdf=boolean`

#### Headers

<table><thead><tr><th width="158">Name</th><th width="77">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Path Parameters

<table><thead><tr><th width="156">Name</th><th width="79">Type</th><th>Description</th></tr></thead><tbody><tr><td>doc_token</td><td>string</td><td>O token do documento que se deseja analisar o histórico de atividades</td></tr></tbody></table>

#### Query Parameters

<table><thead><tr><th width="156">Name</th><th width="106">Type</th><th>Description</th></tr></thead><tbody><tr><td>download_pdf</td><td>boolean</td><td><p>Valor que permite decidir o tipo de retorno que o endpoint irá devolver. </p><p></p><p>Ex.:</p><p><code>download_pdf=true</code></p><p>ou</p><p><code>download_pdf=false</code></p><p></p><p>Caso seja o valor atribuído seja <code>true</code>  O retorno será um arquivo PDF com o histórico de atividades nele.<br>Caso seja  <code>false</code> ou caso não esteja preenchido, será retornado, em formato JSON, um lista com os valores de cada atividade feita no documento pelo signatário.<br></p></td></tr></tbody></table>

#### Exemplos de retorno de sucesso:

{% tabs %}
{% tab title="Status 200 - Formato JSON" %}
```json
[
    {
        "time": "2024-11-27 17:44:32.117577+00:00",
        "user": "jose.da.silva@teste.com.br",
        "event": "Documento visualizado",
        "description": "Documento visualizado por jose.da.silva@teste.com.br"
    },
    {
        "time": "2024-11-27 17:44:34.395952+00:00",
        "user": "jose.da.silva@teste.com.br",
        "event": "Confirmação de leitura",
        "description": "Confirmação de leitura de jose.da.silva@teste.com.br"
    },
    {
        "time": "2024-11-27 17:45:29.398835+00:00",
        "user": "jose.da.silva@teste.com.br",
        "event": "Validação reconhecimento facial",
        "description": "Validação do rosto de jose.da.silva@teste.com.br com a foto do documento de identidade (anexo no relatório de assinaturas)"
    },
    {
        "time": "2024-11-27 17:45:40.904009+00:00",
        "user": "jose.da.silva@teste.com.br",
        "event": "Aceitação do processamento de dados pessoais",
        "description": "jose.da.silva@teste.com.br concordou com o processamento de dados pessoais de acordo com a Política de Privacidade"
    },
    {
        "time": "2024-11-21 05:18:45.733798+00:00",
        "user": "jose.da.silva@teste.com.br",
        "event": "Documento criado",
        "description": "O documento foi criado por jose.da.silva@teste.com.br via web"
    }
]
```
{% endtab %}

{% tab title="Status 200 - Arquivo em pdf" %}
Neste modelo o endpoint retorna um arquivo de download direto, no seguinte modelo:

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

#### Exemplos de retorno de erro:

{% tabs %}
{% tab title="Status 401 - Não Autorizado" %}
Para este erro o endpoint retorna no atributo StatusCode o valor 401, indicando que o token enviado não tem permissão de visualizar os dados desse documento.

Para esse erro sugerimos que verifique se o token enviado nos Headers está correto de acordo como exemplo já descrito acima.
{% endtab %}

{% tab title="Status 404 - Não encontrado" %}
Neste erro o endpoint retorna o StatusCode com valor 404, indicando que o doc token enviado não foi encontrado.

Quando esse erro acontece, sugerimos conferir se o token enviado na url do endpoint foi o token correto.
{% endtab %}
{% endtabs %}
