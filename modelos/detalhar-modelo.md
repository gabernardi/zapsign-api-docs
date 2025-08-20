# Detalhar modelo

Ao usar este endpoint com o token do modelo, você pode verificar dados como signatários, campos personalizados (inputs) e outras configurações essenciais, evitando erros ou retrabalhos no processo de assinatura. Esse recurso é útil quando você precisa verificar ou editar um modelo já existente, ou garantir que as configurações estão corretas antes de utilizá-lo.

## Detalhar modelo

<mark style="color:blue;">`GET`</mark> `https://api.zapsign.com.br/api/v1/templates/{{template_token}}/`\
\
No endpoint acima, substitua `{{template_token}}` pelo token exclusivo do modelo que deseja detalhar.&#x20;

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

{% tabs %}
{% tab title="200: OK Detalhamento realizado com sucesso" %}
```javascript
{
	"token": "152f8416-xxxx-xxxx-xxxx-1aaf785dd335",
	"template_type": "docx",
	"name": "Template name",
	"active": true,
	"template_file": "https://zapsign.s3.amazonaws.com/2022/1/docs/xxxxx-d66b-495f-9b51-xxxx.docx",
	"created_at": "2022-01-05T12:59:42.563218Z",
	"last_update_at": "2022-01-05T13:03:22.242003Z",
	"redirect_link": "",
	"folder_path": "",
	"lang": "pt-br"
	"signers": [
		{
			"name": "{{NOME COMPLETO}}",
			"auth_mode": "assinaturaTela",
			"email": "",
			"phone_country": "",
			"phone_number": "",
			"lock_name": true,
			"lock_phone": false,
			"lock_email": false,
			"hide_phone": false,
			"blank_phone": false,
			"hide_email": false,
			"blank_email": false,
			"require_selfie_photo": false,
			"require_document_photo": false,
			"selfie_validation_type": "none",
			"qualification": ""
		}
	],
	"inputs": [
		{
			"variable": "{{NOME COMPLETO}}",
			"input_type": "input",
			"label": "NOME COMPLETO",
			"help_text": "",
			"options": "",
			"required": false,
			"order": 1
		},
		{
			"variable": "{{CNPJ}}",
			"input_type": "input",
			"label": "CNPJ",
			"help_text": "",
			"options": "",
			"required": false,
			"order": 2
		},
		{
			"variable": "{{CPF}}",
			"input_type": "input",
			"label": "CRO",
			"help_text": "",
			"options": "",
			"required": false,
			"order": 3
		}
	]
}
```
{% endtab %}
{% endtabs %}
