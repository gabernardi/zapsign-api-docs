# Atualizar formulario

Ao criar um documento a partir de um modelo sem preencher todos os campos dinâmicos, o signatário precisará completar as informações para gerar e assinar o documento. Este endpoint configura o formulário para melhorar a experiência do signatário e reduzir erros.

#### **Configurar Formulário**

<mark style="color:green;">**`POST`**</mark> `https://api.zapsign.com.br/api/v1/templates/update-form/`

## Headers

<table><thead><tr><th>Name</th><th width="101">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

### Request Body

<table><thead><tr><th width="125">Name</th><th width="158">Type</th><th>Description</th></tr></thead><tbody><tr><td>template_id*</td><td>string</td><td>Token do modelo criado.</td></tr><tr><td>custom_intro</td><td>string</td><td>Mensagem com instruções para o signatário (será exibida no início do formulário). Padrão: "".</td></tr><tr><td>youtube_video_code</td><td>string</td><td>Inclui um vídeo do YouTube no início do formulário. Se o vídeo for https://www.youtube.com/watch?v=Fi0qJgEjYAw, o código será Fi0qJgEjYAw. Padrão: "".</td></tr><tr><td>inputs [variable]</td><td>array &#x3C;input></td><td>Configurações dos campos dinâmicos.</td></tr></tbody></table>

### **inputs**

Configuração dos campos do formulário para ajudar o signatário no preenchimento e evitar erros.

* **variable** (string): Nome do campo dinâmico dentro do arquivo DOCX. Exemplo: \{{nome\}}.
* **input\_type** (string): Tipo de campo para validar o formato. Padrão: "input".

<table><thead><tr><th width="125">input_type</th><th>Description</th></tr></thead><tbody><tr><td>input</td><td>Texto curto.</td></tr><tr><td>email</td><td>Endereço de e-mail.</td></tr><tr><td>phone_br</td><td>Número de telefone no Brasil.</td></tr><tr><td>signer_fullname</td><td>Nome e sobrenome.</td></tr><tr><td>radio</td><td>Opção múltipla. Deve-se usar o parâmetro <strong>"options"</strong> para definir as opções.</td></tr><tr><td>dopdown-list</td><td>Lista suspensa para que o signatário selecione uma opção da lista. O parâmetro "options" deve ser usado para definir as opções.</td></tr><tr><td>checklist</td><td>Caixa de seleção (checkbox). Deve-se usar o parâmetro <strong>"options"</strong> para definir as opções.</td></tr><tr><td>date</td><td>Data no formato dd/mm/yyyy.</td></tr><tr><td>ext-date</td><td>Data da assinatura por escrito. Ao selecionar esta opção, o campo será preenchido automaticamente com a data de assinatura do documento.</td></tr><tr><td>date-signature</td><td>Data da assinatura no formato dd/mm/yyyy. Ao selecionar esta opção, o campo será preenchido automaticamente com a data de assinatura do documento.</td></tr><tr><td>cpf</td><td>CPF</td></tr><tr><td>cnpj</td><td>CNPJ</td></tr><tr><td>dinheiro</td><td>R$</td></tr></tbody></table>

* **label** (string): Título do campo no formulário. Exemplo: Nome completo. Padrão: mesmo nome da variável sem os colchetes \{{\}}.
* **help\_text** (string): Texto de ajuda que será exibido abaixo do título do campo. Exemplo: Maria Perez. Padrão: "".
* **options** (string): Opções quando o tipo de campo for múltipla escolha ou checkbox (input\_type "radio" ou "checklist"). Exemplo: "Opção A; Opção B; Opção C".
* **required** (boolean): Define se o campo é obrigatório para o signatário preencher. Padrão: true.
* **order** (integer): Ordem em que o campo será exibido no formulário.

### Request

````javascript
{
    "template_id":"8fb60983-eb54-450c-b7ce-fd27b0f277c5",
    "custom_intro": "Bem vindo",
    "youtube_video_code": "https://www.youtube.com/watch?v=WrV2uq2tGak",
    "inputs": [
        {
            "variable": "{{NOME COMPLETO}}",
            "input_type": "signer_fullname",
            "label": "Nome",
            "help_text": "Maria Souza",
            "options": "",
            "required": true,
            "order": 1
        },
        {
            "variable": "{{E-MAIL}}",
            "input_type": "email",
            "label": "E-mail",
            "help_text": "email@email.com",
            "options": "",
            "required": true,
            "order": 2
        },
        {
            "variable": "{{NÚMERO DO CPF}}",
            "input_type": "cpf",
            "label": Número de CPF",
            "help_text": "",
            "options": "",
            "required": true,
            "order": 3
        },
        {
            "variable": "{{ENDEREÇO COMPLETO}}",
            "input_type": "input",
            "label": "Endereço",
            "help_text": "",
            "options": "",
            "required": true,
            "order": 4
        }
    ]
}
```
````

### Response

````javascript
{
    "token": "8fb60983-eb54-450c-b7ce-fd27b0f277c5",
    "template_type": "docx",
    "name": "Nome do modelo",
    "active": true,
    "template_file": "https://zapsign.s3.amazonaws.com/2025/2/api/0a22531c-2a5b-4860-8566-d77e854e061e.docx?AWSAccessKeyId=AKIASUFZJ7JCTI2ZRGWX&Signature=5keF2sXFOVOHc5YNxZV833QytcY%3D&Expires=1738714013",
    "created_at": "2025-02-04T23:06:30.261376Z",
    "last_update_at": "2025-02-04T23:06:53.101554Z",
    "redirect_link": "",
    "folder_path": "/",
    "lang": "pt-br",
    "signers": [
        {
            "name": "Signatário 1",
            "auth_mode": "assinaturaTela",
            "email": "",
            "phone_country": "55",
            "phone_number": "",
            "lock_name": true,
            "lock_phone": false,
            "lock_email": false,
            "hide_phone": false,
            "blank_phone": false,
            "hide_email": false,
            "blank_email": true,
            "require_selfie_photo": true,
            "require_document_photo": false,
            "selfie_validation_type": "none",
            "qualification": "Representante Legal"
        }
    ],
    "inputs": [
        {
            "variable": "{{NOME COMPLETO}}",
            "input_type": "input",
            "label": "NOME COMPLETO 23",
            "help_text": "test nome",
            "options": "",
            "required": true,
            "order": 1
        },
        {
            "variable": "{{E-MAIL}}",
            "input_type": "input",
            "label": "E-MAIL 23",
            "help_text": "test email",
            "options": "",
            "required": true,
            "order": 2
        },
        {
            "variable": "{{NÚMERO DO CPF}}",
            "input_type": "input",
            "label": "NÚMERO DO CPF 32",
            "help_text": "test cpf",
            "options": "",
            "required": true,
            "order": 3
        },
        {
            "variable": "{{ENDEREÇO COMPLETO}}",
            "input_type": "email",
            "label": "ENDEREÇO COMPLETO 32",
            "help_text": "test endereço",
            "options": "",
            "required": true,
            "order": 4
        }
    ],
    "extra_templates": [],
    "notify_extra_emails": "silvana@zapsign.com.br",
    "custom_intro": "Bem vindo",
    "youtube_video_code": "https://www.youtube.com/watch?v=WrV2uq2tGak"
}
```
````

