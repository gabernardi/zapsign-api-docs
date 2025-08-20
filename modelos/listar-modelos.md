# Listar modelos

Esse endpoint **facilita o controle sobre seus modelos**, permitindo que você **visualize informações importantes como o nome, o tipo de arquivo, a data de criação e a última atualização!**\
\
Imagine que você tenha uma empresa que utiliza diversos documentos padronizados, como contratos e acordos de confidencialidade. Ao longo do tempo, pode ser necessário revisar quais modelos já foram cadastrados, verificar se estão atualizados ou até mesmo encontrar um modelo específico para reutilizar. Usando esse endpoint, você consegue acessar rapidamente essas informações e organizar seus modelos conforme necessário.

## Listar modelos

<mark style="color:blue;">`GET`</mark> `https://api.zapsign.com.br/api/v1/templates/`

#### Query Parameters

| Name | Type   | Description                              |
| ---- | ------ | ---------------------------------------- |
| page | number | 1, 2, 3, n... (20 resultados por página) |

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

{% tabs %}
{% tab title="200: OK Listagem realizada com sucesso" %}
```javascript
{
	"count": 31,
	"next": "http://api.zapsign.com.br/api/v1/templates/?page=2",
	"previous": null,
	"results": [
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
		},
		{
			"token": "333333333-xxxx-xxxx-xxxx-1aaf785dd335",
			"template_type": "docx",
			"name": "Template name 2",
			"active": true,
			"template_file": "https://zapsign.s3.amazonaws.com/2022/1/docs/xxxxx-d66b-495f-9b51-xxxx.docx",
			"created_at": "2022-01-05T12:59:42.563218Z",
			"last_update_at": "2022-01-05T13:03:22.242003Z",
			"redirect_link": "",
			"folder_path": "",
			"lang": "pt-br"
		},
		...
	]
}
```
{% endtab %}
{% endtabs %}
