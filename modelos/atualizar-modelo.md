# Atualizar modelo

Ao usar este endpoint com o token do modelo, você pode atualizar os dados como nome e idioma do modelo. Também é possível alternar seu estado entre ativado e desativado. Redefinir os e-mails dos contatos que serão notificados sobre o modelo. E por fim, editar campos de configuração do primeiro signatário definido no modelo.

## Atualizar modelo

<mark style="color:green;">`PUT`</mark>`https://api.zapsign.com.br/api/v1/templates/{{template_token}}/`

{% hint style="success" %}
No endpoint acima, substitua `{{template_token}}` pelo token exclusivo do modelo que deseja atualizar.
{% endhint %}

### **Headers**

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

### **Request Body**

<table><thead><tr><th width="124">Name</th><th width="158">Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>Título do documento. String de até 255 caracteres</td></tr><tr><td>lang </td><td>string</td><td>Idioma do documento. Valores possíveis: "pt-br" (português), "es" (espanhol), "en" (inglês). Default: "pt-br"</td></tr><tr><td>observers </td><td>array&#x3C;string></td><td>Representa os observadores do documento (limite de 20), ou seja, endereços de e-mails que serão notificados após a conclusão do fluxo de assinatura. É um array de strings.</td></tr><tr><td>first_signer</td><td>Object</td><td>Configuração do signatário do documento.</td></tr><tr><td>folder_token</td><td>string</td><td><p>Opcional, se preenchido, este campo terá prioridade sobre folder_path. Ele define o diretório com base no token da pasta, que pode ser obtido acessando o seguinte endereço:</p><p>https://zapsign.com.br/conta/modelos?pasta=&#x3C;token_da_pasta></p><p>Se você ainda não souber o token, navegue até a pasta desejada a partir de:</p><p>https://zapsign.com.br/conta/modelos</p><p>e copie o valor do parâmetro pasta na URL após acessar a pasta.</p></td></tr><tr><td>folder_path</td><td>string</td><td>Opcional, caminho da pasta dentro da ZapSign em que o modelo será colocado. Se as pastas não existirem, serão criadas automaticamente.<br>Requisitos:<br>folder_path pode ter até 255 caracteres<br>Cada pasta pode ter até 50 caracteres<br>Há um limite de 5 níveis de pasta<br>Exemplo: /api/ ou /pasta1/pasta2/pasta3/<br>Valor padrão: / (sem pasta)</td></tr></tbody></table>

{% hint style="danger" %}
O parâmetro **url\_docx** ou **base64\_docx** não pode ser mudado. Caso precise alterar o documento do modelo, será necessário criar um modelo novo.
{% endhint %}

### **Configurando o Signatário**

Esses campos permitem ajustar a experiência de assinatura, como o método de autenticação.

{% hint style="warning" %}
Para entender mais sobre os campos de configuração de signatário, acesse a página de [criação de modelo](create-template-docx/).
{% endhint %}

### Request

```javascript
{
    "name": "Nome do modelo",
    "lang": "pt-br",
    "observers": [
        "email@email.com"
    ],
    "first_signer": {
        "blank_email": false,
        "blank_phone": false,
        "auth_mode": "assinaturaTela",
        "require_selfie_photo": false,
        "require_document_photo": false,
        "selfie_validation_type": "",
        "qualification": "Aprovador"
    }
}
```

### Response

{% tabs %}
{% tab title="200: OK  -  Modelo atualizado com sucesso" %}
```javascript
{
	"token": "152f8416-xxxx-xxxx-xxxx-1aaf785dd335",
	"template_type": "docx",
	"name": "Nome do modelo",
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
			"qualification": "Aprovador"
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
	],
    "extra_templates": [],
    "notify_extra_emails": "email@email.com",
    "custom_intro": "",
    "youtube_video_code": ""
}
```
{% endtab %}
{% endtabs %}
