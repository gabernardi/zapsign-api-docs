# Criar documento (OneClick)

Este endpoint permite criar um documento para assinatura com um clique a partir de um arquivo PDF ou DOCX. É recomendado quando você já possui o arquivo final e apenas precisa configurar o documento e os signatários. Para utilizá-lo, você deve enviar os dados no formato JSON e também receberá a resposta no mesmo formato.

### Criar documento via upload

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/docs/`

{% hint style="info" %}
**Dica:** para enviar vários documentos em um envelope para que o signatário os assine ao mesmo tempo, primeiro crie o documento com este endpoint e, em seguida, adicione os outros documentos utilizando o endpoint [**Adicionar anexo (documento extra)**.](../adicionar-anexo-documento-extra.md)
{% endhint %}

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Request Body

<table><thead><tr><th width="168">Name</th><th width="135">Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>Título do documento. String de até 255 caracteres</td></tr><tr><td>one_click_active</td><td>boolean</td><td>Para ativar a experiência simplificada de assinatura, este parâmetro deve ser true.</td></tr><tr><td>require_signature</td><td>boolean</td><td>Quando a experiência simplificada de assinatura (one_click_active) está ativada e este parâmetro é definido como true, o signatário precisará aceitar o checkbox e desenhar a assinatura.</td></tr><tr><td>url_pdf</td><td>string</td><td>Defina o PDF a ser assinado, a partir de uma URL pública com o arquivo. Aceitamos por enquanto apenas um arquivo no formato PDF, de até 10Mb. </td></tr><tr><td>base64_pdf</td><td>string</td><td><strong>Alternativa ao url_pdf:</strong> Defina o PDF a ser assinado, a partir de um base64. Você deve converter o arquivo para uma string em base64 e nos enviar neste parâmetro (mais detalhes abaixo).</td></tr><tr><td>url_docx</td><td>string</td><td><strong>Alternativa ao url_pdf:</strong> Defina o Word (.docx) a ser assinado, a partir de uma URL pública com o arquivo. Aceita um arquivo no formato .docx, de até 10Mb. </td></tr><tr><td>base64_docx</td><td>string</td><td><strong>Alternativa ao url_pdf:</strong> Defina o Word (.docx) a ser assinado, a partir de um base64. Você deve converter o arquivo para uma string em base64 e nos enviar neste parâmetro (mais detalhes abaixo).</td></tr><tr><td>signers[name]</td><td>Array&#x3C;Signer></td><td><p>O campo 'signers' representa os signatários do documento, ou seja, quem irá assinar. A configuração de cada signatário esta abaixo.</p><p>É um array de objetos.</p></td></tr><tr><td>lang </td><td>string</td><td>idioma do documento. Valores possíveis: "pt-br" (português), "es" (espanhol), "en" (inglês). Default: "pt-br"</td></tr><tr><td>disable_signer_emails </td><td>boolean</td><td>para desativar os e-mails enviados aos signatários, envie esse parâmetro como true. Default: false</td></tr><tr><td>brand_logo </td><td>string</td><td><p>(se deseja personalizar a logomarca da experiência de assinatura deste documento específico, envie a URL da imagem (precisa ser um link publicamente acessível). </p><p>Default: ""</p></td></tr><tr><td>brand_primary_color </td><td></td><td><p>se deseja personalizar a cor primária (do botão) da experiência de assinatura deste documento específico, envie em rgb ou hexadecimal. </p><p>Ex: "#0011ee". </p><p>Default: ""</p></td></tr><tr><td>brand_name</td><td>string</td><td><p>se deseja personalizar o nome do remetente dos e-mails enviados ao signatário, insira aqui o nome da marca. Por exemplo, se inserido "XPTO Advogados", o remetente do e-mail será "XPTO Advogados via ZapSign". </p><p>Max-length: 100 caracteres. </p><p>Default: ""</p></td></tr><tr><td>external_id</td><td>string</td><td><p>ID do documento na sua aplicação.</p><p>Default: ""</p></td></tr><tr><td>folder_path</td><td>string</td><td><p>caminho da pasta dentro da ZapSign em que o documento será colocado. Se as pastas não existirem, serão criadas automaticamente. Requisitos: (1) o folder_path pode ter até 255 caracteres, (2) cada pasta pode ter até 50 caracteres, (3) há um limite de 5 níveis de pasta. </p><p>Ex.: "/api/" ou "/pasta1/pasta2/pasta3/". </p><p>Default: "/" (sem pasta).</p></td></tr><tr><td>created_by</td><td>string</td><td><p>e-mail do usuário que será definido como criador do documento, para fins de organização interna. Caso o e-mail não exista ou não seja usuário da sua conta, este parâmetro será ignorado. </p><p>Default: "" </p><p>(documento terá como criador o proprietário da conta)</p></td></tr><tr><td>date_limit_to_sign </td><td>DateTime</td><td><p>Data limite para assinatura do documento. </p><p>Formatos aceitos: </p><p>YYYY-MM-DD</p><p>YYYY-MM-DDTH:m:s.ssssssZ</p></td></tr><tr><td>signature_order_active</td><td>boolean</td><td><p>Se verdadeiro, as assinaturas do signatário serão solicitadas sequencialmente. </p><p>Default: false</p></td></tr><tr><td>observers </td><td>array&#x3C;string></td><td>Representa os observadores do documento (limite de 20), ou seja, endereços de e-mails que serão notificados após a conclusão do fluxo de assinatura. É um array de strings.</td></tr><tr><td>reminder_every_n_days </td><td>integer</td><td>Representa o intervalo de dias entre os lembretes que serão enviados para os signatários.</td></tr><tr><td>allow_refuse_signature </td><td>boolean</td><td>Se verdadeiro, os signatários tem a opção de se recusar a assinar. Default: false.</td></tr><tr><td>disable_signers_get_original_file </td><td>boolean</td><td><p>Se verdadeiro, os signatários não tem a opção de baixar o documento original. </p><p>Default: false.</p></td></tr><tr><td>Metadata</td><td>Array</td><td>Metadados personalizados enviados na criação do documento, no formato de pares <code>key</code> e <code>value</code>. Essas informações aparecem apenas nos webhooks de criação, assinatura, recusa e exclusão.</td></tr></tbody></table>

### Configurando signatários

Esses campos permitem ajustar a experiência de assinatura para cada pessoa envolvida.&#x20;

{% hint style="warning" %}
**Aviso:** ao criar um documento com OneClick, é necessário preencher as informações de **name**, **email** ou **phone**, já que o signatário apenas aceitará a assinatura do documento por meio de uma checkbox (é opcional habilitar a assinatura). Além disso, não é possível definir métodos de autenticação (**auth\_mode**, **selfie\_validation\_type**, **require\_document\_photo**, **require\_selfie**).
{% endhint %}

**Documento** - raiz do JSON:

* **Signers**&#x20;
  * **name** (string): O nome do signatário. Obrigatório.
  * **email** (string): O e-mail do signatário. É **obrigatório** definir o e-mail ou o telefone, pois o signatário não poderá preencher esses dados.
  * **phone\_country** (string): O código do país do telefone do signatário. É **obrigatório** definir o e-mail ou o telefone, pois o signatário não poderá preencher esses dados.
  * **phone\_number** (string): O número de telefone do signatário. É **obrigatório** definir o e-mail ou o telefone, pois o signatário não poderá preencher esses dados.
  * **send\_automatic\_email** (boolean): Se **true**, a ZapSign irá enviar um e-mail ao signatário com o link para assinar o documento. Se **false** (default), [você é quem se encarregará de compartilhar o link de assinatura com o signatário](https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta), seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. Observação: para isso funcionar, é obrigatório que o email do signatário seja definido.
  * **send\_automatic\_whatsapp** (boolean): Se **true**, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para assinar o documento. Se **false** (default), [você é quem se encarregará de compartilhar o link de assinatura com o signatário](https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta), seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. \
    Observação: para isso funcionar, é obrigatório que o phone\_country e phone\_number do signatário sejam definidos e **cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em** [**Configurações > Plano**](https://app.zapsign.com.br/conta/configuracoes?tab=plans)**.**
  * **send\_automatic\_whatsapp\_signed\_file** (boolean): Se **true**, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para o arquivo assinado. Se **false** (default), [você é quem se encarregará de compartilhar o link de assinatura com o signatário](https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta), seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. \
    Observação: para isso funcionar, é obrigatório que o phone\_country e phone\_number do signatário sejam definidos e **cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em** [**Configurações > Plano**](https://app.zapsign.com.br/conta/configuracoes?tab=plans)**.**
  * **order\_group** (integer)**:** Caso "signature\_order\_active" esteja ativo no document, esse campo controla a ordem de assinatura. Exemplo: Se o order\_group é 1, esse será o primeiro a assinar, se o order\_group for 2 esse será o segundo a assinar e assim por diante.
  * **custom\_message** (string): (apenas relevante caso **send\_automatic\_email: true**). A custom\_message é a mensagem personalizada que você pode inserir no e-mail enviado pela ZapSign ao signatário. Exemplo: "Olá Fulano, \n Este é o seu contrato de trabalho. \n Abraços, Equipe XPTO". O símbolo \n serve para "pular uma linha" no texto do e-mail. Default: ""
  * **blank\_email** (boolean): Você pode não solicitar o email do signatário. Default: false
  * **hide\_email** (boolean): Você pode ocultar o email do signatário no relatório de assinaturas. Default: false
  * **blank\_phone** (boolean): Você pode não solicitar o telefone do signatário. Default: false
  * **hide\_phone** (boolean): Você pode ocultar o telefone do signatário no relatório de assinaturas. Default: false
  * **qualification** (string): Qualificação para aparecer no relatório de assinaturas. Ex: valor "testemunha" irá resultar em "Assinou como testemunha". Default: ""
  * **external\_id** (string): ID do signatário na sua aplicação. Default: ""
  * **redirect\_link** (string): link para redirecionamento após signatário assinar. Por exemplo: "https://www.seusite.com.br/agradecimento". Irá aparecer como um botão "CONTINUAR" abaixo dos botões "Baixar original" e "Baixar assinado". Lembre-se de inserir o http:// ou https:// no começo do link.  Default: ""

***

### Exemplos de requisição

```javascript
{
	"name":"Termos de uso de serviço",
	"url_pdf":"https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf",
        "one_click_active": true,
        "require_signature": true,
	"external_id": null,
	"signers":[
		{
			"name":"Maria Perez",
			"email":"maria@gmail.com",
			"send_automatic_email": false
		}
	],
    "lang": "pt-br",
    "signed_file_only_finished": false,
    "folder_path":"/",
    "created_by":"",
    "date_limit_to_sign": null,
    "signature_order_active": false,
    "reminder_every_n_days": 0,
    "allow_refuse_signature": false,
    "disable_signers_get_original_file": false
}
```

***

### O que faço com a resposta?

Após uma requisição bem sucedida, você deverá receber uma resposta como essa:

```javascript
{
    "open_id": 5,
    "token": "eb9c367a-e62f-4992-8360-b0219deaeecc",
    "status": "pending",
    "one_click_active": true,
    "require_signature": true,
    "name": "Contrato de Admissão João",
    "original_file": "https://zapsign.s3.amazonaws.com/pdf/62xxxxx-d8fc-4392-8575-f3c46c3cfc7a/df6bac91-2766-4182-8c8b-ded5287e4c0f.pdf",
    "signed_file": null,
    "created_at": "2020-04-16T03:33:46.241747Z",
    "last_update_at": "2020-04-16T03:33:46.241775Z",
    "signers": [
        {
            "token": "921c115d-4a6e-445d-bdca-03fadedbbc0b",
            "sign_url": "https://app.zapsign.com.br/verificar/oneclick/921c115d-4a6e-445d-bdca-03fadedbbc0b",
            "status": "new",
            "name": "João da Silva",
            "email": "",
            "phone_country": "",
            "phone_number": "",
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null,
            "resend_attempts": null
        },
        {
            "token": "07fb0a0a-4b7d-49a5-bd7b-4958265c4e46",
            "sign_url": "https://app.zapsign.com.br/verificar/oneclick/07fb0a0a-4b7d-49a5-bd7b-4958265c4e46",
            "status": "new",
            "name": "Fulano Siclano",
            "email": "",
            "phone_country": "",
            "phone_number": "",
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null,
            "resend_attempts": null
        }
    ]
}
```

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que o endpoint de [Detalhar documento](../detalhar-documento.md) seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

O próximo passo é compartilhar os links de assinatura com cada signatário através da sua aplicação. Cada link é composto pela rota base:

```arduino
https://app.zapsign.com.br/verificar/oneclick/{{signer_token}}
```

No exemplo acima, em que temos dois signatários, você deverá enviar dois links específicos, um para cada signatário, utilizando o respectivo token:

* **João da Silva**: [https://app.zapsign.com.br/verificar/onelick/921c115d-4a6e-445d-bdca-03fadedbbc0b](https://app.zapsign.com.br/verificar/921c115d-4a6e-445d-bdca-03fadedbbc0b)
* **Fulano Siclano**: [https://app.zapsign.com.br/verificar/oneclick/07fb0a0a-4b7d-49a5-bd7b-4958265c4e46](https://app.zapsign.com.br/verificar/07fb0a0a-4b7d-49a5-bd7b-4958265c4e46)

Agora, basta aguardar que os signatários acessem os links e concluam a assinatura!

***

### Editar documento OneClick em andamento&#x20;

É possível adicionar, remover ou editar um signatário de um documento em andamento. É importante destacar que, para adicionar ou editar um signatário, **não é possível utilizar os parâmetros auth\_mode, selfie\_validation\_type, require\_document\_photo ou require\_selfie**, pois o OneClick é uma experiência de assinatura simplificada e não é compatível com métodos avançados de autenticação.

Leia a documentação para:

* [Adicionar signatário ](../../signatarios/adicionar-signatario.md)
* [Remover signatário ](../excluir-documento.md)
* [Editar signatário](../../signatarios/atualizar-signatario.md)

### Sobre o base64

Base64 é uma maneira simples de converter um arquivo em texto. Veja aqui uma definição mais completa [https://pt.wikipedia.org/wiki/Base64](https://pt.wikipedia.org/wiki/Base64). Assim, converter o arquivo em base64 e enviar como texto no corpo da requisição é mais fácil do que lidar com **multipart/form-data**, por exemplo.

Para testar a API, você pode converter manualmente seu PDF em base64 através de vários sites, como esse: [https://base64.guru/converter/encode/pdf](https://base64.guru/converter/encode/pdf)

Quando a API já estiver integrada em seu sistema, procure a função adequada na sua linguagem de programação que pode converter o arquivo em base64.&#x20;

{% hint style="warning" %}
**Observação:** você deve enviar o parâmetro base64\_pdf apenas com a conversão do arquivo em base64. **Não** insira data:application/pdf;base64, na sua string.
{% endhint %}

Não quer trabalhar com base64? **Suba seu PDF em uma url pública e use o parâmetro url\_pdf.**

### Converse com o Gepeto!

Tem alguma duvida? Utilize nossa inteligência artificial treinada com toda a documentação da API =)

{% embed url="https://n8n.zapsign.com.br/webhook/fee2c476-7f23-4a4f-8928-5c7ab081ffcd/chat" %}

