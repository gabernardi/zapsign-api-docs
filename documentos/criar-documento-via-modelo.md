# Criar documento via Modelo

## Criar documento via Modelo

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/models/create-doc/`

Este endpoint permite criar um documento por meio de um Modelo DOCX. Você só precisa enviar os dados que substituirão os campos dinâmicos do modelo no formato JSON e receberá a resposta também em JSON.

{% hint style="info" %}
Antes de começar, você deve criar o Modelo na plataforma web da ZapSign na seção de Modelos e selecionar a opção DOCX (**não está disponível para modelos PDF**). [Veja o tutoria](https://clients.zapsign.com.br/help/modelos-o-que-s%C3%A3o-e-como-usar)l para criar um modelo dinâmico.
{% endhint %}

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Request Body

| Name                                           | Type    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ---------------------------------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| template\_id<mark style="color:red;">\*</mark> | string  | <p>Identificador/token do template (modelo dinâmico)</p><p>Ex: https://app.zapsign.com.br/conta/modelos/{TEMPLATE_ID}</p><p></p><p>Para acessar a sua lista de templates clique aqui:<br><a href="https://app.zapsign.com.br/conta/modelos/">https://app.zapsign.com.br/conta/modelos/</a></p><p></p><p></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| signer\_name                                   | string  | Nome do signatário do documento. Se houver mais de um signatário no documento, você poderá adicioná-lo posteriormente via endpoint Adicionar signatário.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| data\[]\['de']                                 | string  | <p>Nome da variável a ser substituída. </p><p>Ex: "{{NOME COMPLETO}}"</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| data\[]\['para']                               | string  | Valor a ser preenchido no lugar da variável. Ex: "João dos Santos"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| signer\_email                                  | string  | Email do signatário do documento. Se houver mais de um signatário no documento, você poderá adicioná-lo posteriormente via endpoint Adicionar signatário.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| signer\_phone\_country                         | String  | Código do pais do signatário do documento (Ex: 55). Se houver mais de um signatário no documento, você poderá adicioná-lo posteriormente via endpoint Adicionar signatário.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| signer\_phone\_number                          | String  | Numero do telefone do signatário do signatário do documento (Ex: 11999999999). Se houver mais de um signatário no documento, você poderá adicioná-lo posteriormente via endpoint Adicionar signatário.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| lang                                           | string  | <p>idioma do documento. Valores possíveis: </p><p>"pt-br" (português)</p><p>"es" (espanhol)</p><p>"en" (inglês). </p><p>Default: "pt-br"</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| disable\_signer\_emails                        | boolean | para desativar os e-mails enviados aos signatários, envie esse parâmetro como true. Default: false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| brand\_logo                                    | string  | <p>se deseja personalizar a logomarca da experiência de assinatura deste documento específico, envie a URL da imagem (precisa ser um link publicamente acessível). </p><p>Default: ""</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| brand\_primary\_color                          | string  | <p>se deseja personalizar a cor primária (do botão) da experiência de assinatura deste documento específico, envie em rgb ou hexadecimal. </p><p>Ex: "#0011ee". </p><p>Default: ""</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| brand\_name                                    | string  | <p>se deseja personalizar o nome do remetente dos e-mails enviados ao signatário, insira aqui o nome da marca. Por exemplo, se inserido "XPTO Advogados", o remetente do e-mail será "XPTO Advogados via ZapSign". Max-length: 100 caracteres. </p><p>Default: ""</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| external\_id                                   | string  | <p>ID do documento na sua aplicação. </p><p>Default: ""</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| folder\_path                                   | string  | <p>caminho da pasta dentro da ZapSign em que o documento será colocado. Se as pastas não existirem, serão criadas automaticamente. Requisitos: (1) o folder_path pode ter até 255 caracteres, (2) cada pasta pode ter até 50 caracteres, (3) há um limite de 5 níveis de pasta. </p><p>Ex.: "/api/" ou "/pasta1/pasta2/pasta3/". </p><p>Default: "/" (sem pasta).</p>                                                                                                                                                                                                                                                                                                                                                                                                |
| created\_by                                    | string  | <p>e-mail do usuário que será definido como criador do documento, para fins de organização interna. Caso o e-mail não exista ou não seja usuário da sua conta, este parâmetro será ignorado. </p><p>Default: "" </p><p>(documento terá como criador aquele usuário que criou o modelo)</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| send\_automatic\_email                         | boolean | <p>Se <strong>true</strong>, a ZapSign irá enviar um e-mail ao signatário com o link para assinar o documento. Se <strong>false</strong> (default), você é quem se encarregará de compartilhar o link de assinatura com o signatário, seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. Observação: para isso funcionar, é obrigatório que o email do signatário seja definido com um campo dinâmico, por exemplo {{EMAIL DO CLIENTE}}, e esse valor seja enviado junto da requisição.</p><p><img src="../.gitbook/assets/image (75).png" alt=""></p>                                                                                                                                                                                                     |
| custom\_message                                | string  | <p>(apenas relevante caso <strong>send_automatic_email: true</strong>). </p><p>A custom_message é a mensagem personalizada que você pode inserir no e-mail enviado pela ZapSign ao signatário.</p><p>Exemplo: "Olá Fulano, \n Este é o seu contrato de trabalho. \n Abraços, Equipe XPTO". O símbolo \n serve para "pular uma linha" no texto do e-mail. </p><p>Default: ""</p>                                                                                                                                                                                                                                                                                                                                                                                      |
| signer\_has\_incomplete\_fields                | bolean  | Caso definido como _true_, o signatário será direcionado para preencher o formulário do modelo antes de assinar o documento. Observação: valores enviados em _data_ já estarão preenchidos, sem que o signatário precise preencher novamente. Default: false.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| reminder\_every\_n\_days                       | integer | <p>Representa o intervalo de dias entre os lembretes que serão enviados para os signatários, enquanto o signatario não assinar. Serão executadas no máximo 3 tentativas. Observação: este campo só deve ser preenchido se send_automatic_whatsapp ou send_automatic_email forem true<br>Exemplo: se definido como 7 será enviada uma tentativa a cada 7 dias, até que o usuario assine, por no máximo 21 dias.</p>                                                                                                                                                                                                                                                                                                                                                   |
| allow\_refuse\_signature                       | boolean | Se verdadeiro, os signatários tem a opção de se recusar a assinar. Default: false.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| disable\_signers\_get\_original\_file          | boolean | Se verdadeiro, os signatários não tem a opção de baixar o documento original. Default: false.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| send\_automatic\_whatsapp                      | boolean | <p>Se <strong>true</strong>, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para assinar o documento. Se <strong>false</strong> (default), <a href="https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta">você é quem se encarregará de compartilhar o link de assinatura com o signatário</a>, seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. <br>Observação: para isso funcionar, é obrigatório que o phone_country e phone_number do signatário sejam definidos e <strong>cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em</strong> <a href="https://app.zapsign.com.br/conta/configuracoes?tab=plans"><strong>Configurações > Plano</strong></a><strong>.</strong></p> |
| send\_automatic\_whatsapp\_signed\_file        | boolean | <p>Se <strong>true</strong>, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para o arquivo assinado. Se <strong>false</strong> (default), <a href="https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta">você é quem se encarregará de compartilhar o link de assinatura com o signatário</a>, seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. <br>Observação: para isso funcionar, é obrigatório que o phone_country e phone_number do signatário sejam definidos e <strong>cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em</strong> <a href="https://app.zapsign.com.br/conta/configuracoes?tab=plans"><strong>Configurações > Plano</strong></a><strong>.</strong></p>  |
| signature\_order\_active                       | boolean | Se verdadeiro, as assinaturas do signatário serão solicitadas sequencialmente. Default: false. Sempre verdadeiro quando signer\_has\_incomplete\_fields = true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Metadata                                       | Array   | Metadados personalizados enviados na criação do documento, no formato de pares `key` e `value`. Essas informações aparecem apenas nos webhooks de criação, assinatura, recusa e exclusão.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| folder\_token                                  | string  | <p>Se preenchido, este campo terá prioridade sobre <code>folder_path</code>. Ele define o diretório com base no <strong>token da pasta</strong>, que pode ser obtido acessando o seguinte endereço:<br><code>https://app.zapsign.com.br/conta/documentos?pasta=&#x3C;token_da_pasta></code></p><p>Se você ainda não souber o token, navegue até a pasta desejada a partir de:<br><code>https://app.zapsign.com.br/conta/documentos</code><br>e copie o valor do parâmetro <code>pasta</code> na URL após acessar a pasta.</p>                                                                                                                                                                                                                                        |
| signature\_placement                           | string  | Permite posicionar a assinatura no documento usando um texto âncora (sem necessidade de coordenadas x, y). Configure signature\_placement: "<<{identificador\_da\_assinatura}>>" e a assinatura será posicionada onde encontrar esse texto. Se o texto aparecer mais de uma vez, a assinatura será posicionada em todos os locais. Observação: o uso de << >> é altamente recomendado para evitar conflitos com o texto, mas não é obrigatório. Ex: "<>". Default: ""                                                                                                                                                                                                                                                                                                |
| rubrica\_placement                             | string  | Permite posicionar a rubrica no documento usando um texto âncora (sem necessidade de coordenadas x, y). Configure rubrica\_placement: "<<{identificador\_da\_rubrica}>>" e a rubrica será posicionada onde encontrar esse texto. Se o texto aparecer mais de uma vez, a rubrica será posicionada em todos os locais. Observação: o uso de << >> é altamente recomendado para evitar conflitos com o texto, mas não é obrigatório. Ex: "<>". Default: ""                                                                                                                                                                                                                                                                                                              |

{% tabs %}
{% tab title="200 Modelo criado com sucesso" %}
```
{
    "open_id": 5,
    "token": "eb9c367a-e62f-4992-8360-b0219deaeecc",
    "status": "pending",
    "name": "Contrato de Admissão",
    "original_file": "https://zapsign.s3.amazonaws.com/pdf/62xxxxx-d8fc-4392-8575-f3c46c3cfc7a/df6bac91-2766-4182-8c8b-ded5287e4c0f.pdf",
    "signed_file": null,
    "created_at": "2020-04-16T03:33:46.241747Z",
    "last_update_at": "2020-04-16T03:33:46.241775Z",
    "signers": [
        {
            "token": "921c115d-4a6e-445d-bdca-03fadedbbc0b",
            "sign_url": "https://app.zapsign.com.br/verificar/921c115d-4a6e-445d-bdca-03fadedbbc0b",
            "status": "new",
            "name": "João da Silva",
            "email": "",
            "phone_country": "",
            "phone_number": "",
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null
        }
    ],
    "answers": [ // lista de variaveis e respostas no modelo dinamico (caso o documento tenha sido criado através de um modelo dinamico)
        {
            "variable": "NOME COMPLETO",
            "value": "Nome Teste"
        },
        {
            "variable": "NÚMERO DO CPF",
            "value": "99999999999"
        },
        {
            "variable": "ENDEREÇO COMPLETO",
            "value": "Endereço teste"
        }
    ]
}
```
{% endtab %}
{% endtabs %}

### Exemplo de requisição

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-11b56f17-c3cd-4898-bd58-98bcb011b925?ctx=documentation" %}
URL para o endpoint Create doc from template
{% endembed %}

### O que fazer com a resposta

Após uma requisição bem sucedida, você deverá receber uma resposta como essa:

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que o endpoint de [Detalhar documento](detalhar-documento.md) seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

```javascript
{
    "open_id": 5,
    "token": "eb9c367a-e62f-4992-8360-b0219deaeecc",
    "status": "pending",
    "name": "Contrato de Admissão",
    "original_file": "https://zapsign.s3.amazonaws.com/pdf/62xxxxx-d8fc-4392-8575-f3c46c3cfc7a/df6bac91-2766-4182-8c8b-ded5287e4c0f.pdf",
    "signed_file": null,
    "created_at": "2020-04-16T03:33:46.241747Z",
    "last_update_at": "2020-04-16T03:33:46.241775Z",
    "signers": [
        {
            "token": "921c115d-4a6e-445d-bdca-03fadedbbc0b",
            "sign_url": "https://app.zapsign.com.br/verificar/921c115d-4a6e-445d-bdca-03fadedbbc0b",
            "status": "new",
            "name": "João da Silva",
            "email": "",
            "phone_country": "",
            "phone_number": "",
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null,
            "resend_attempts": null
        }
    ],
    "answers": [ // lista de variaveis e respostas no modelo dinamico (caso o documento tenha sido criado através de um modelo dinamico)
        {
            "variable": "NOME COMPLETO",
            "value": "Nome Teste"
        },
        {
            "variable": "NÚMERO DO CPF",
            "value": "99999999999"
        },
        {
            "variable": "ENDEREÇO COMPLETO",
            "value": "Endereço teste"
        }
    ]
}
```

O que você deverá fazer com essa resposta é **enviar o link de assinatura para o signatário através da sua aplicação.**

O link de assinatura consiste na rota:\
**https://app.zapsign.com.br/verificar/{signer\_token}**

Ou seja, no exemplo acima, você deve enviar o seguinte link de assinatura ao signatário:\
&#xNAN;**- https://app.zapsign.com.br/verificar/921c115d-4a6e-445d-bdca-03fadedbbc0b**\
\
E agora é só aguardar que o signatário assine!

### Mais de um signatário

{% hint style="info" %}
**Mais de um signatário?** Se você quiser adicionar mais signatários, utilize os endpoints "[Atualizar signatário](https://docs.zapsign.com.br/signatarios/atualizar-signatario)" e "[Adicionar signatário](https://docs.zapsign.com.br/signatarios/adicionar-signatario)", receba o token do novo signatário e envie o link de assinatura como explicado acima.
{% endhint %}

### Como criar um Modelo dinâmico na ZapSign

Acesse nossa central de ajuda e veja o passo a passo completo:

{% embed url="https://clients.zapsign.com.br/help/modelos-o-que-s%C3%A3o-e-como-usar?utm_term=&utm_campaign=%5BON%5D+%5BPerformance+Max+%23001%5D&utm_source=adwords&utm_medium=ppc&hsa_acc=6928999691&hsa_cam=14865783484&hsa_grp=&hsa_ad=&hsa_src=x&hsa_tgt=&hsa_kw=&hsa_mt=&hsa_net=adwords&hsa_ver=3&gad=1&gclid=CjwKCAjwvJyjBhApEiwAWz2nLWdB7ch3VJ0TK4AVNd9LH6ajS_Mz873X5BfMUYLCMTyrQ9muXbeukBoCkNAQAvD_BwE" %}
URL para a central de ajuda da ZapSign
{% endembed %}

### Converse com o Gepeto!

Tem alguma duvida? Utilize nossa inteligência artificial treinada com toda a documentação da API =)

{% embed url="https://n8n.zapsign.com.br/webhook/fee2c476-7f23-4a4f-8928-5c7ab081ffcd/chat" %}
