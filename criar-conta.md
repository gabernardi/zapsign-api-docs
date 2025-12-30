---
description: >-
  Este endpoint permite que você crie contas separadas para diferentes clientes
  ou departamentos da sua empresa, mantendo todos eles sob o controle da sua
  conta principal (parceira ou reseller).
---

# Criar conta

Essa estrutura é ideal para parceiros que desejam gerenciar múltiplas operações dentro de uma estrutura única, mantendo:

* Separação de documentos e usuários por conta;
* Permissões ajustadas por equipe ou cliente;
* Relatórios e consumo organizados por unidade;
* Integrações independentes para cada conta (com tokens exclusivos por conta)

{% hint style="danger" %}
**Importante:** Apenas contas com essa funcionalidade ativa poderão utilizar este endpoint. Caso você ainda não tenha acesso, [entre em contato com o time comercial.](https://zapsign.com.br/fale-com-vendas)
{% endhint %}

### Como funciona

Ao fazer a requisição para este endpoint:

1. Será criada uma **nova conta** (organização) dentro da ZapSign.
2. O **proprietário da conta principal** (quem fez a requisição) também será o **proprietário da nova conta** criada. Isso garante controle total sobre as contas associadas.
3. O e-mail informado na requisição será adicionado à nova conta com o papel de **Membro**. Se você não informar um e-mail na requisição, será criado apenas um usuário, que será o proprietário da conta.
   * Um membro pode visualizar todos os documentos da conta, mas **não tem acesso às configurações** da plataforma.
4. Caso um e-mail seja informado, o usuário convidado receberá um e-mail da ZapSign para criar uma senha e acessar sua conta.

### Faturamento e gestão das contas associadas

> <mark style="color:red;">**⚠️ Atenção: Todos os consumos das contas associadas serão de responsabilidade da conta principal (parceiro).**</mark>

Isso inclui:

* Criação de documentos;
* Consultas de antecedentes;
* Envio de documentos por **WhatsApp**;
* Métodos de **autenticação avançada** como reconhecimento facial, certificado digital, etc.

A conta principal terá acesso a um painel consolidado com todos os consumos e documentos gerados pelas contas associadas.

Se for necessário **suspender temporariamente** o acesso de uma conta associada, você pode utilizar o endpoint [Atualizar status de pagamento](parcerias/atualizar-status-de-pagamento.md)

## Criar uma conta parceira

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/partner/company/`

**Headers**

<table><thead><tr><th width="143">Name</th><th width="105">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Request Body

<table><thead><tr><th width="156">Name</th><th width="116">Type</th><th>Description</th></tr></thead><tbody><tr><td>email</td><td>string</td><td>E-mail do novo usuário que será adicionado como membro.</td></tr><tr><td>country<mark style="color:red;">*</mark></td><td>string</td><td>País da nova conta. Valores possíveis:br, mx, co, pe, cl</td></tr><tr><td>lang<mark style="color:red;">*</mark></td><td>string</td><td>Idioma da nova empresa. "pt-br" (português), "es" (espanhol), "en" (inglês). Default: "pt-br"</td></tr><tr><td>company_name<mark style="color:red;">*</mark></td><td>string</td><td>Nome da nova empresa</td></tr><tr><td>phone_country</td><td>string</td><td>Código do país do telefone do novo usuário.</td></tr><tr><td>phone_number</td><td>string</td><td>Número de telefone do novo usuário.</td></tr><tr><td>primary_color</td><td>string</td><td>Opcional - Cor primária da empresa (ex: código HEX ou identificador interno).</td></tr><tr><td>logo_url</td><td>string</td><td>Opcional - Logo da empresa em formato base64.</td></tr></tbody></table>

{% tabs %}
{% tab title="Exemplo de payload:" %}
```json
{
    "email": "email@email",
    "phone_number": "11111111111",
    "phone_country": "55",
    "country": "br",
    "lang": "pt-br",
    "company_name": "Nome do cliente"
}
```
{% endtab %}
{% endtabs %}

### Response

{% tabs %}
{% tab title="200 Conta Criada" %}
```json
{
    "id": 543,
    "name": "Nome do cliente",
    "api_token": "010234xx-23ed-44ab-8b57-9XXXXe03cc5e-cc71-4911-bf29-3bxxxx140540",
    "created_at": "2025-04-04T22:35:16.821400Z",
    "credits_balance": 0,
    "lang": "pt-br",
    "timezone": "America/Brasilia"
}
```
{% endtab %}

{% tab title="400 Bad Request" %}
```json
{
    "message": "Invalid Input",
    "data": {
        "email": [
            "Este campo é obrigatório."
        ],
        "country": [
            "Este campo é obrigatório."
        ],
        "lang": [
            "Este campo é obrigatório."
        ],
        "company_name": [
            "Este campo é obrigatório."
        ]
    }
}
```
{% endtab %}

{% tab title="403 Forbidden - Token Inválido" %}
```json
{
    "detail": "Você não tem permissão para executar essa ação."
}
```
{% endtab %}

{% tab title="403 Forbidden - Plano Inválido" %}
```json
{
    "detail": "Plan necesario para crear empresa parceira."
}
```
{% endtab %}

{% tab title="403 Forbidden - Company Parceira" %}
```json
{
    "detail": "Ação não permitida para empresa parceira."
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Na resposta da requisição, você receberá o **API token exclusivo** da nova conta criada. Isso permite que cada conta tenha sua própria integração com a API da ZapSign, de forma totalmente independente das demais.
{% endhint %}
