# Consulta de Empresa

Este endpoint é utilizado para criar uma consulta de empresa ou de histórico de crédito de empresa.

<mark style="color:green;">**POST**</mark> `https://api.zapsign.com.br/api/v1/checks/`

#### Header

<table><thead><tr><th width="150">Campo</th><th width="94">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td>Token da API com prefixo "Bearer". Exemplo: <code>Bearer c7f35c84-7893-4087-b4fb-d1f06c23</code></td></tr></tbody></table>

#### Request Body

<table><thead><tr><th width="155">Nome</th><th width="131.609375">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>country<mark style="color:red;">*</mark></td><td>string</td><td>BR | CO | MX. Mais detalhes sobre consultas disponíveis <a href="../introducao.md">clique aqui.</a></td></tr><tr><td>type<mark style="color:red;">*</mark></td><td>string</td><td> <code>company</code>, <code>credit_company_co</code>,  <code>credit_company_br</code>. Mais detalhes sobre consultas disponíveis <a href="../entendendo-o-resultado.md">clique aqui</a>.</td></tr><tr><td>user_authorized<mark style="color:red;">*</mark></td><td>boolean</td><td>Indica se a empresa autorizou a validação. Deve ser <code>true</code> para prosseguir.</td></tr><tr><td>force_creation</td><td>boolean</td><td>Se <code>true</code>, força a criação de uma nova consulta de antecedentes, mesmo que já exista um resultado anterior. Se <code>false</code>, retorna o resultado da consulta anterior.</td></tr><tr><td>tax_id<mark style="color:red;">*</mark></td><td>string</td><td>Documento de identificação oficial da empresa (RUT, CNPJ, RFC).</td></tr><tr><td>company_name</td><td>string</td><td>Nome da empresa. Se especificado, realiza uma consulta adicional em bases internacionais para detalhar os resultados.</td></tr><tr><td>observers</td><td>array&#x3C;string></td><td>Representa os observadores da consulta de antecedentes (limite de 20), ou seja, endereços de e-mail que serão notificados quando a consulta de antecedentes for concluída. É um array de strings.</td></tr></tbody></table>



{% hint style="warning" %}
**Importante:** Cada consulta de antecedentes gera um custo adicional conforme o tipo de consulta. Você pode recarregar sua conta no painel acessando:\
[**Planos e Preços > Créditos**](https://app.zapsign.com.br/conta/configuracoes/plans?tab=credits)
{% endhint %}

#### Exemplo de Requisição

```json
{
    "user_authorized": true,
    "force_creation": true,
    "type": "company",
    "country": "CO",
    "tax_id": "11111111"
}
```

**Resposta**

{% tabs %}
{% tab title="200 - Criado com sucesso" %}
```json
{
    "check_id": "CHK682a755bb7135140248cc8dd1d290a01",
    "status": "not_started",
    "company_name": "",
    "full_name": "",
    "first_name": "",
    "last_name": "",
    "date_of_birth": null,
    "issue_date": null,
    "national_id": "",
    "foreign_id": "",
    "tax_id": "11111111",
    "country": "CO",
    "native_country": "",
    "check_type": "company",
    "lang": "es",
    "region": "",
    "created_at": "2025-03-28T17:49:43.363416Z",
    "last_update_at": "2025-03-28T17:49:43.363435Z"
}

```
{% endtab %}
{% endtabs %}
