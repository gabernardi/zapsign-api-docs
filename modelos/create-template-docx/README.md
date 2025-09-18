# Criar modelo DOCX

Os modelos DOCX na ZapSign permitem a automação de documentos com campos dinâmicos, facilitando a geração de contratos, acordos e outros documentos recorrentes. Criar documentos a partir de um modelo é útil para diversos casos de uso, como:

* **Enviar um documento para que o signatário preencha um formulário** e, com essas informações, gerar o documento. Exemplos: solicitação de apólice de seguro, termo de consentimento, inscrições para eventos, entre outros.
* **Enviar um documento com informações parcialmente preenchidas**, permitindo que o signatário complete o formulário e os campos restantes. O documento será criado com os campos dinâmicos, e o signatário continuará com o processo de assinatura. Exemplos: abertura de contas bancárias, solicitação de empréstimo.
* **Preencher todos os campos dinâmicos para criar o documento final**, onde o signatário apenas precisará assinar. Exemplos: contrato de trabalho, nota promissória, contrato de aluguel.

#### **Criação do Documento no Word (DOCX)**

Antes de utilizar o endpoint para criar um modelo na ZapSign, é necessário preparar o arquivo DOCX com os campos dinâmicos que serão substituídos por informações específicas em cada geração de documento. Para isso, siga estes passos:

#### **Criação do Documento no Word (DOCX)**

Antes de utilizar o endpoint para criar um modelo na ZapSign, é necessário preparar o arquivo DOCX com os campos dinâmicos que serão substituídos por informações específicas em cada geração de documento. Para isso, siga estes passos:

**Criar o documento base**

* Utilize Microsoft Word, Google Docs (exportando para DOCX) ou qualquer editor compatível com o formato DOCX.
* Redija o conteúdo do documento, garantindo que esteja bem estruturado.

**Definir os campos dinâmicos**

* Os campos dinâmicos são representados por chaves duplas **\{{campo\}}** dentro do documento.
* Exemplo: **\{{nome\}}, \{{data\}}, \{{email\}}**.

**Evitar imagens e tabelas**

* Recomendamos evitar o uso de imagens e tabelas no documento DOCX, pois isso pode interferir no correto funcionamento da funcionalidade.

**Salvar e exportar**

* Salve o arquivo no formato `.docx`.
* Verifique se os campos dinâmicos estão corretamente escritos e posicionados.

Após a preparação do documento DOCX, será possível utilizar o endpoint correspondente para enviar o modelo para a ZapSign e começar a gerar documentos de forma automatizada.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Exemplo</p></figcaption></figure>

### Criar modelo DOCX

<mark style="color:green;">**`POST`**</mark> `https://api.zapsign.com.br/api/v1/templates/create/`

#### Headers

<table><thead><tr><th>Name</th><th width="101">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Request Body

<table><thead><tr><th width="125">Name</th><th width="158">Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>Título do documento. String de até 255 caracteres</td></tr><tr><td>docx_url</td><td>string</td><td>Deve ser uma URL pública, e o tamanho máximo do documento é de 10MB.</td></tr><tr><td>base64_docx</td><td>string</td><td>Documento convertido para uma string em base64 (mais detalhes abaixo).</td></tr><tr><td>lang </td><td>string</td><td>Idioma do documento. Valores possíveis: "pt-br" (português), "es" (espanhol), "en" (inglês). Default: "pt-br"</td></tr><tr><td>observers </td><td>array&#x3C;string></td><td>Representa os observadores do documento (limite de 20), ou seja, endereços de e-mails que serão notificados após a conclusão do fluxo de assinatura. É um array de strings.</td></tr><tr><td>first_signer</td><td>Object</td><td>Configuração do signatário do documento.</td></tr><tr><td>folder_token</td><td>string</td><td><p>Se preenchido, este campo terá prioridade sobre folder_path. Ele define o diretório com base no token da pasta, que pode ser obtido acessando o seguinte endereço:</p><p>https://zapsign.com.br/conta/modelos?pasta=&#x3C;token_da_pasta></p><p>Se você ainda não souber o token, navegue até a pasta desejada a partir de:</p><p>https://zapsign.com.br/conta/modelos</p><p>e copie o valor do parâmetro pasta na URL após acessar a pasta.</p></td></tr><tr><td>folder_path</td><td>string</td><td>Opcional, caminho da pasta dentro da ZapSign em que o modelo será colocado. Se as pastas não existirem, serão criadas automaticamente.<br>Requisitos:<br>folder_path pode ter até 255 caracteres<br>Cada pasta pode ter até 50 caracteres<br>Há um limite de 5 níveis de pasta<br>Exemplo: /api/ ou /pasta1/pasta2/pasta3/<br>Valor padrão: / (sem pasta)</td></tr><tr><td>redirect_link</td><td>string</td><td><p>Permite configurar um botão exibido ao final da assinatura para redirecionar o signatário a uma URL específica, como uma tela de agradecimento ou qualquer outra página do seu site.</p><p>Exemplo: https://zapsign.com.br/</p></td></tr></tbody></table>

### **Configurando o Signatário**

Esses campos permitem ajustar a experiência de assinatura, como o método de autenticação.

{% hint style="info" %}
Os dados do signatário (nome, e-mail e telefone) são definidos ao criar o documento a partir de um modelo.
{% endhint %}

#### **first\_signer**

* **blank\_email** (boolean): Se definido como true, o e-mail do signatário não será solicitado e não será incluído no relatório de assinatura. É obrigatório ter **o e-mail OU o número de telefone** do signatário. Valor padrão: false.
* **blank\_phone** (boolean): Se definido como true, o número de celular do signatário não será solicitado e não será incluído no relatório de assinatura. É obrigatório ter **o e-mail OU o número de telefone** do signatário. Valor padrão: false.
* **qualification** (string): Papel do signatário que será exibido no relatório de assinatura. Por exemplo, "Testemunha" será mostrado como "Assinou como Testemunha". Valor padrão: "".
* **auth\_mode** (string): Escolha o método de autenticação para o signatário. Isso adiciona mais segurança ao documento assinado. Para mais informações sobre os métodos de autenticação, clique **aqui**. Valor padrão: "assinaturaTela".

<table><thead><tr><th width="262">auth_mode</th><th>Descrição</th><th>Custo</th></tr></thead><tbody><tr><td>"assinaturaTela"</td><td>Assinatura diretamente na tela.</td><td>Sem custo </td></tr><tr><td>"tokenEmail"</td><td>Envio de token via e-mail para autenticação.</td><td>Sem custo </td></tr><tr><td>"assinaturaTela-tokenEmail"</td><td>Combinação de assinatura na tela e token enviado por e-mail.</td><td>Sem custo </td></tr><tr><td>"tokenSms"</td><td>Envio de token via SMS para autenticação.</td><td>R$0,10 por envio</td></tr><tr><td>"assinaturaTela-tokenSms"</td><td>Combinação de assinatura na tela e token enviado por SMS.</td><td>R$0,10 por envio</td></tr><tr><td>"tokenWhatsapp"</td><td>Envio de token via WhatsApp para autenticação.</td><td>5 créditos</td></tr><tr><td>"assinaturaTela-tokenWhatsapp"</td><td>Combinação de assinatura na tela e token enviado por WhatsApp.</td><td>5 créditos</td></tr><tr><td>"certificadoDigital"</td><td>Autenticação com certificado digital.</td><td>5 créditos</td></tr><tr><td>"CPF"</td><td>Autenticação com verificação de CPF.</td><td>Sem custo</td></tr><tr><td>"assinaturaTela-cpf"</td><td>Combinação de assinatura na tela e verificação de CPF avançado.</td><td>Sem custo </td></tr></tbody></table>

* **require\_selfie\_photo** (boolean): Se definido como true, o signatário será solicitado a tirar uma selfie durante o processo de assinatura (**não há validação da foto**). Valor padrão: false.
* **require\_document\_photo** (boolean): Se definido como true, o signatário será solicitado a tirar uma foto da frente e do verso do seu documento de identidade durante o processo de assinatura (**não há validação da foto**). Valor padrão: false.
* **selfie\_validation\_type** (string): Métodos biométricos avançados para validar a identidade do signatário. Para saber mais sobre cada método, [clique **aqui**.](https://zapsign.com.br/produto/identidade-signatario)

<table><thead><tr><th width="136">Selfie_validation_type</th><th width="222">Descrição</th><th width="137">Paises</th><th>Valor por validação</th></tr></thead><tbody><tr><td>"liveness-document-match"</td><td>Reconhecimento facial que solicita que o signatário faça o upload de uma foto do documento de identidade e grave o rosto. Valida que a pessoa é a mesma do documento e que está presente no momento da assinatura</td><td>Todos os países</td><td>15 creditos</td></tr><tr><td>"liveness-NXCD"</td><td>Valida que a pessoa está presente no momento da assinatura com um vídeo passivo (liveness)</td><td>Todos os países</td><td>15 creditos </td></tr><tr><td><p>“face-match-and-datavalid”</p><p><br></p></td><td>Autenticação via verificação facial com correspondência no banco de dados do governo (Serpro), confirmando o CPF e a CNH. </td><td>Disponível somente para o Brasil.</td><td>35 créditos</td></tr><tr><td><p>“identity-verification-global”</p><p><br></p></td><td>Verificação global da identidade do signatário no momento da assinatura, incluindo autenticação do documento e correspondência facial.</td><td>Todos os países</td><td>50 créditos</td></tr></tbody></table>

### Request

```javascript
{
    "name": "Nome do modelo",
    "docx_url": "https://zapsign.s3.amazonaws.com/dev/2025/1/docs/1b1e8e16-b9ce-45f4-8dc8-c0320af371a5/29812f55-eb17-4182-b65e-09e895a861ad.docx",
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

```javascript
{
    "token": "272xxxd4-ecda-47xx2-be7e-59e2beb752xx",
    "template_type": "docx",
    "name": "Nome do modelo",
    "active": true,
    "template_file": "https://zapsign.s3.amazonaws.com/dev/2025/1/api/45f39edb-c78d-42e4-a450-22cd7c62d656.docx?AWSAccessKeyId=AKIASUFZJ7JCTI2ZRGWX&Signature=v8haa5obmuOzV88e3naQDXnPVr8%3D&Expires=1738258954",
    "created_at": "2025-01-30T16:42:34.703412Z",
    "last_update_at": "2025-01-30T16:42:34.741300Z",
    "redirect_link": "https://zapsign.com.br/",
    "folder_path": "/",
    "lang": "pt-br",
    "signers": [
        {
            "name": "Signatario 1",
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
            "require_selfie_photo": false,
            "require_document_photo": false,
            "selfie_validation_type": "none",
            "qualification": "Aprovador"
        }
    ],
    "inputs": [
        {
            "variable": "{{nome}}",
            "input_type": "input",
            "label": "nome",
            "help_text": "",
            "options": "",
            "required": true,
            "order": 1
        },
        {
            "variable": "{{email}}",
            "input_type": "input",
            "label": "email",
            "help_text": "",
            "options": "",
            "required": true,
            "order": 2
        },
        {
            "variable": "{{numero documento}}",
            "input_type": "input",
            "label": "numero documento",
            "help_text": "",
            "options": "",
            "required": true,
            "order": 3
        },
        {
            "variable": "{{endereco}}",
            "input_type": "input",
            "label": "endereco",
            "help_text": "",
            "options": "",
            "required": true,
            "order": 4
        }
    ],
    "extra_templates": [],
    "notify_extra_emails": "email@email.com",
    "custom_intro": "",
    "youtube_video_code": ""
}
```

### **Próximos Passos**

* **Se o signatário precisar preencher os campos dinâmicos no formulário durante a assinatura**, você deve configurar o formulário usando o endpoint **"Configuração de Formulário de Modelo"**.

{% hint style="success" %}
**Para criar documentos a partir deste modelo**, acesse a seção [**"Criar Documento via Modelo"**.](../../documentos/criar-documento-via-modelo.md)
{% endhint %}

***

#### **Sobre Base64**

Base64 é uma forma simples de converter arquivos em texto. Se quiser saber mais detalhes sobre o que é Base64, você pode consultar sua [definição completa **aqui**.](https://en.wikipedia.org/wiki/Base64)

Ao converter um arquivo para Base64 e enviá-lo como texto no corpo da requisição, ele se torna mais fácil de manipular do que, por exemplo, o formato `multipart/form-data`.

Para **testar a API**, você pode converter manualmente seu arquivo DOCX para Base64 através de diversos sites online, [como **este**.](https://products.aspose.app/pdf/pt/conversion/word-to-base64)

Quando a API já estiver integrada ao seu sistema, procure a função correspondente na sua linguagem de programação para converter arquivos para Base64.

{% hint style="warning" %}
**Atenção:** Você deve enviar o parâmetro base64\_docx **somente** com a conversão Base64 do arquivo. **Não** inclua data:application/pdf;base64, no seu parâmetro.
{% endhint %}

