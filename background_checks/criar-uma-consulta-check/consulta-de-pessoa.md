# Consulta de Pessoa

Este endpoint é utilizado para criar uma consulta de pessoa ou de histórico de crédito de pessoa.

Os parâmetros que você deve enviar variam conforme o país e o tipo de consulta.\
Além disso, existem parâmetros opcionais que podem melhorar os resultados consultando mais bases de dados e ajudando a filtrar homônimos em alguns casos.

<mark style="color:green;">**POST**</mark> `https://api.zapsign.com.br/api/v1/checks/`

#### Header

<table><thead><tr><th width="190">Campo</th><th width="103">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td>Token da API com prefixo "Bearer". Ex: <code>Bearer c7f35c84-7893-4087-b4fb-xxxxxx</code></td></tr></tbody></table>

#### Request Body

<table><thead><tr><th width="155.01953125">Campo</th><th width="135.46875">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>country<mark style="color:red;">*</mark></td><td>string</td><td>BR | CO | CL | MX | PE. Mais detalhes sobre consultas disponíveis [clique aqui].</td></tr><tr><td>type<mark style="color:red;">*</mark></td><td>string</td><td><code>person</code>, <code>credit_person_co</code>, <code>credit_person_br</code>, . Mais detalhes sobre consultas disponíveis <a href="../entendendo-o-resultado.md">clique aqui</a>.</td></tr><tr><td>user_authorized<mark style="color:red;">*</mark></td><td>boolean</td><td>Indica se a pessoa autorizou a validação. Deve ser <code>true</code> para prosseguir.</td></tr><tr><td>force_creation</td><td>boolean</td><td>Se <code>true</code>, força a criação de uma nova consulta mesmo se já houver uma anterior. Se <code>false</code>, retorna o resultado existente.</td></tr><tr><td>national_id</td><td>string</td><td>Documento de identidade oficial. Deve ser enviado <code>national_id</code>, <code>foreign_id</code>, <code>ptp</code> ou <code>ppt</code>.</td></tr><tr><td>foreign_id</td><td>string</td><td>Documento de identidade de estrangeiro. Deve ser enviado um dos seguintes: <code>national_id</code>, <code>foreign_id</code>, <code>ptp</code> ou <code>ppt</code>. Disponível para CO, CL, MX e PE.</td></tr><tr><td>first_name</td><td>string</td><td>Nome da pessoa. Ajuda a buscar em bases de dados internacionais para detalhes adicionais.</td></tr><tr><td>last_name</td><td>string</td><td>Sobrenome da pessoa. Também usado para buscas internacionais.</td></tr><tr><td>region</td><td>string</td><td>Obrigatório para BR. Região para consulta de antecedentes. Pode ser uma região específica ou <code>ALL</code> para consulta nacional (consultas nacionais podem levar até 24h). Ex: DF, SP, RJ, ALL, etc.</td></tr><tr><td>ptp</td><td>string</td><td>Permissão de Proteção Temporária no Peru (PE).</td></tr><tr><td>ppt</td><td>string</td><td>Permissão de Proteção Temporária na Colômbia (CO).</td></tr><tr><td>date_of_birth</td><td>string</td><td>Data de nascimento no formato <code>YYYY-MM-DD</code>. Obrigatório para estrangeiros (foreign_id) em CL e CO, e para documentos nacionais em PE e BR. Em outros casos, ajuda a melhorar os resultados.</td></tr><tr><td>issue_number</td><td>string</td><td>Número de emissão do documento no Chile (CL), usado para mais detalhes.</td></tr><tr><td>custom_input</td><td>string</td><td>Identificador externo opcional (até 128 caracteres).</td></tr><tr><td>state_id</td><td>string</td><td>RG (Registro Geral) no Brasil. Necessário para antecedentes completos. Omite caracteres especiais.</td></tr><tr><td>verification_code</td><td>string</td><td>Código de verificação para registros criminais no Peru e Chile.</td></tr><tr><td>issue_date</td><td>DateTime</td><td>Data de emissão do documento no formato <code>YYYY-MM-DD</code>. Aplica para CL e CO.</td></tr><tr><td>observers</td><td>array&#x3C;string></td><td>Representa os observadores da consulta de antecedentes (limite de 20), ou seja, endereços de e-mail que serão notificados quando a consulta de antecedentes for concluída. É um array de strings.</td></tr></tbody></table>

{% hint style="warning" %}
**Importante:** Cada consulta de antecedentes gera um custo adicional conforme o tipo de consulta. Você pode recarregar sua conta no painel acessando:\
[**Planos e Preços > Créditos**](https://app.zapsign.com.br/conta/configuracoes/plans?tab=credits)
{% endhint %}

#### Exemplo de Requisição

```json
{
    "user_authorized": true,
    "force_creation": true,
    "type": "person",
    "country": "BR",
    "national_id": "111.111.111-11"
}
```

Resposta

{% tabs %}
{% tab title="200 - Consulta criada com sucesso" %}
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
    "national_id": "111.111.111-1",
    "foreign_id": "",
    "tax_id": "",
    "country": "BR",
    "native_country": "",
    "check_type": "person",
    "lang": "es",
    "region": "",
    "created_at": "2025-03-28T17:49:43.363416Z",
    "last_update_at": "2025-03-28T17:49:43.363435Z"
}
```
{% endtab %}
{% endtabs %}
