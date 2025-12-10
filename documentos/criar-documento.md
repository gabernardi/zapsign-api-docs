# Criar documento via Upload

A plataforma da ZapSign permite configurar cada signatário individualmente, **definindo não apenas os dados de contato, mas também preferências de autenticação, mensagens e ordem de assinatura.**

Neste artigo, vamos detalhar cada campo configurável para signatários ao criar um documento por upload de PDF ou um DOCX.\
\
Nesta seção:\
[**Configurando o Documento;**](criar-documento.md#configurando-documento)\
[**Configurando Signatários;**](criar-documento.md#configurando-signatarios)\
[**Exemplos de requesições prontas;**](criar-documento.md#exemplos-de-requisicao)\
[**O que faço com a resposta?**](criar-documento.md#o-que-faco-com-a-resposta)\
[**Sobre o Base64**](criar-documento.md#sobre-o-base64)[**;**](criar-documento.md#sobre-o-base64)

***

### Configurando documento

\
Na configuração do documento, você define as propriedades básicas para criar e gerenciar um documento na plataforma. Esses campos incluem o nome, status inicial, e URLs do arquivo original e assinado, formando a estrutura essencial do documento. Essa etapa garante que o documento esteja corretamente identificado e acessível ao longo de todo o processo de assinatur&#x61;**.Você deverá enviar os dados em JSON, bem como receberá eles nesse mesmo formato.**<br>

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/docs/`

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Request Body

| Name                                   | Type           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------------------------------------- | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name                                   | string         | Título do documento. String de até 255 caracteres                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| url\_pdf                               | string         | Defina o PDF a ser assinado, a partir de uma URL pública com o arquivo. Aceitamos por enquanto apenas um arquivo no formato PDF, de até 10Mb.                                                                                                                                                                                                                                                                                                                                                                                 |
| base64\_pdf                            | string         | **Alternativa ao url\_pdf:** Defina o PDF a ser assinado, a partir de um base64. Você deve converter o arquivo para uma string em base64 e nos enviar neste parâmetro (mais detalhes abaixo).                                                                                                                                                                                                                                                                                                                                 |
| signers\[name]                         | Array\<Signer> | <p>O campo 'signers' representa os signatários do documento, ou seja, quem irá assinar. A configuração de cada signatário esta abaixo.</p><p>É um array de objetos.</p>                                                                                                                                                                                                                                                                                                                                                       |
| markdown\_text                         | string         | **Aternativa ao url\_pdf:** Permite enviar um texto em Markdown para a criação do documento, facilitando a integração com IA e automações.  Como exemplo, confira o [ZapSign Agent OpenAI](https://github.com/renatohr/zapsign-agent-openai), que demonstra como agentes de IA podem utilizar essa funcionalidade.                                                                                                                                                                                                            |
| url\_docx                              | string         | **Alternativa ao url\_pdf:** Defina o Word (.docx) a ser assinado, a partir de uma URL pública com o arquivo. Aceita um arquivo no formato .docx, de até 10Mb.                                                                                                                                                                                                                                                                                                                                                                |
| base64\_docx                           | string         | **Alternativa ao url\_pdf:** Defina o Word (.docx) a ser assinado, a partir de um base64. Você deve converter o arquivo para uma string em base64 e nos enviar neste parâmetro (mais detalhes abaixo).                                                                                                                                                                                                                                                                                                                        |
| lang                                   | string         | idioma do documento. Valores possíveis: "pt-br" (português), "es" (espanhol), "en" (inglês). Default: "pt-br"                                                                                                                                                                                                                                                                                                                                                                                                                 |
| disable\_signer\_emails                | boolean        | para desativar os e-mails enviados aos signatários, envie esse parâmetro como true. Default: false                                                                                                                                                                                                                                                                                                                                                                                                                            |
| brand\_logo                            | string         | <p>(se deseja personalizar a logomarca da experiência de assinatura deste documento específico, envie a URL da imagem (precisa ser um link publicamente acessível). </p><p>Default: ""</p>                                                                                                                                                                                                                                                                                                                                    |
| brand\_primary\_color                  |                | <p>se deseja personalizar a cor primária (do botão) da experiência de assinatura deste documento específico, envie em rgb ou hexadecimal. </p><p>Ex: "#0011ee". </p><p>Default: ""</p>                                                                                                                                                                                                                                                                                                                                        |
| brand\_name                            | string         | <p>se deseja personalizar o nome do remetente dos e-mails enviados ao signatário, insira aqui o nome da marca. Por exemplo, se inserido "XPTO Advogados", o remetente do e-mail será "XPTO Advogados via ZapSign". </p><p>Max-length: 100 caracteres. </p><p>Default: ""</p>                                                                                                                                                                                                                                                  |
| external\_id                           | string         | <p>ID do documento na sua aplicação.</p><p>Default: ""</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| folder\_path                           | string         | <p>caminho da pasta dentro da ZapSign em que o documento será colocado. Se as pastas não existirem, serão criadas automaticamente. Requisitos: (1) o folder_path pode ter até 255 caracteres, (2) cada pasta pode ter até 50 caracteres, (3) há um limite de 5 níveis de pasta. </p><p>Ex.: "/api/" ou "/pasta1/pasta2/pasta3/". </p><p>Default: "/" (sem pasta).</p>                                                                                                                                                         |
| created\_by                            | string         | <p>e-mail do usuário que será definido como criador do documento, para fins de organização interna. Caso o e-mail não exista ou não seja usuário da sua conta, este parâmetro será ignorado. </p><p>Default: "" </p><p>(documento terá como criador o proprietário da conta)</p>                                                                                                                                                                                                                                              |
| date\_limit\_to\_sign                  | DateTime       | <p>Data limite para assinatura do documento. </p><p>Formatos aceitos: </p><p>YYYY-MM-DD</p><p>YYYY-MM-DDTH:m:s.ssssssZ</p>                                                                                                                                                                                                                                                                                                                                                                                                    |
| signature\_order\_active               | boolean        | <p>Se verdadeiro, as assinaturas do signatário serão solicitadas sequencialmente. </p><p>Default: false</p>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| observers                              | array\<string> | Representa os observadores do documento (limite de 20), ou seja, endereços de e-mails que serão notificados após a conclusão do fluxo de assinatura. É um array de strings.                                                                                                                                                                                                                                                                                                                                                   |
| reminder\_every\_n\_days               | integer        | Representa o intervalo de dias entre os lembretes que serão enviados para os signatários.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| allow\_refuse\_signature               | boolean        | Se verdadeiro, os signatários tem a opção de se recusar a assinar. Default: false.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| disable\_signers\_get\_original\_file  | boolean        | <p>Se verdadeiro, os signatários não tem a opção de baixar o documento original. </p><p>Default: false.</p>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Metadata                               | Array          | Metadados personalizados enviados na criação do documento, no formato de pares `key` e `value`. Essas informações aparecem apenas nos webhooks de criação, assinatura, recusa e exclusão.                                                                                                                                                                                                                                                                                                                                     |
| folder\_token                          | string         | <p>Se preenchido, este campo terá prioridade sobre <code>folder_path</code>. Ele define o diretório com base no <strong>token da pasta</strong>, que pode ser obtido acessando o seguinte endereço:<br><code>https://app.zapsign.com.br/conta/documentos?pasta=&#x3C;token_da_pasta></code></p><p>Se você ainda não souber o token, navegue até a pasta desejada a partir de:<br><code>https://app.zapsign.com.br/conta/documentos</code><br>e copie o valor do parâmetro <code>pasta</code> na URL após acessar a pasta.</p> |
| has\_simplified\_signature             | boolean        | Se verdadeiro, ativa a assinatura simplificada para todos os signatários no local informado pelo parâmetro `simplified_signature_position`                                                                                                                                                                                                                                                                                                                                                                                    |
| simplified\_signature\_position        | string         | <p></p><p>Define onde inserir o campo de assinatura simplificada. Valores aceitos:<br></p><p>"left": insere na lateral esquerda das páginas.<br></p><p>"bottom": insere no rodapé das páginas.<br></p><p>"right": insere na lateral direita das páginas.</p>                                                                                                                                                                                                                                                                  |

{% tabs %}
{% tab title="200 Documento criado com sucesso." %}
```javascript
{
    "open_id": 5,
    "token": "eb9c367a-e62f-4992-8360-b0219deaeecc",
    "status": "pending",
    "name": "oi",
    "original_file": "https://zapsign.s3.amazonaws.com/pdf/62c2b027-d8fc-4392-xas75-f3c46c3cfc7a/d33336-4182-8c8b-ded5287e4c0f.pdf",
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
        },
        {
            "token": "07fb0a0a-4b7d-49a5-bd7b-4958265c4e46",
            "sign_url": "https://app.zapsign.com.br/verificar/07fb0a0a-4b7d-49a5-bd7b-4958265c4e46",
            "status": "new",
            "name": "Fulano Siclano",
            "email": "",
            "phone_country": "",
            "phone_number": "",
            "times_viewed": 0,
            "last_view_at": null,
            "signed_at": null
        }
    ]
}
```
{% endtab %}
{% endtabs %}

#### Assinatura simplificada

A assinatura simplificada substitui o desenho da assinatura por um bloco de texto com dados do(s) signatário(s). Esse bloco é inserido automaticamente e costuma aparecer na margem lateral da página. Parâmetros aceitos:

`has_simplified_signature` (boolean): ativa a assinatura simplificada para todos os signatários.

* true: insere o bloco de texto; não há campo de desenho.
* false ou ausente: nenhum efeito de assinatura simplificada (fluxo normal de assinatura).

`simplified_signature_position` (string): posiciona o bloco de texto.

* "bottom": Insere a assinatura simplificada no rodapé das página.
* "left":  Insere a assinatura simplificada na lateral esquerda das páginas.
* "right"  Insere a assinatura simplificada na lateral direita das páginas.

### Configurando signatários

Esses campos permitem ajustar a experiência de assinatura para cada pessoa envolvida. Personalizando cada signatário, desde o método de autenticação até as preferências de contato, ordem de assinatura e mensagens automáticas.

**Documento** - raiz do JSON:

*   **Signers**&#x20;

    *   **auth\_mode** (string):\
        &#x20;

        <table><thead><tr><th width="262">auth_mode</th><th>Descrição</th><th>Custo</th></tr></thead><tbody><tr><td>"assinaturaTela"</td><td>Assinatura diretamente na tela.</td><td>Sem custo </td></tr><tr><td>"tokenEmail"</td><td>Envio de token via e-mail para autenticação.</td><td>Sem custo </td></tr><tr><td>"assinaturaTela-tokenEmail"</td><td>Combinação de assinatura na tela e token enviado por e-mail.</td><td>Sem custo </td></tr><tr><td>"tokenSms"</td><td>Envio de token via SMS para autenticação.</td><td>R$0,10 por envio</td></tr><tr><td>"assinaturaTela-tokenSms"</td><td>Combinação de assinatura na tela e token enviado por SMS.</td><td>R$0,10 por envio</td></tr><tr><td>"tokenWhatsapp"</td><td>Envio de token via WhatsApp para autenticação.</td><td>5 créditos</td></tr><tr><td>"assinaturaTela-tokenWhatsapp"</td><td>Combinação de assinatura na tela e token enviado por WhatsApp.</td><td>5 créditos</td></tr><tr><td>"certificadoDigital"</td><td>Autenticação com certificado digital.</td><td>5 créditos</td></tr></tbody></table>


    * **name** (string): O nome do signatário. Obrigatório.
    * **email** (string): Você pode definir o e-mail do signatário
    * **phone\_country** (string): Você pode definir o telefone (código do país) do signatário. Default: "" (sugestão: utilizar "55" para código do Brasil)
    * **phone\_number** (string): Você pode definir o telefone (DDD + número) do signatário. Exemplo: "11998989222". Default: ""
    * **signature\_placement** (string): Permite posicionar a assinatura no documento usando um texto âncora (sem necessidade de coordenadas x, y). Configure signature\_placement: "<<{identificador\_da\_assinatura}>>" e a assinatura será posicionada onde encontrar esse texto. Se o texto aparecer mais de uma vez, a assinatura será posicionada em todos os locais. Observação: o uso de << >> é altamente recomendado para evitar conflitos com o texto, mas não é obrigatório. Ex: "<\<signer1>>". Default: ""
    * **rubrica\_placement** (string): Permite posicionar a rubrica no documento usando um texto âncora (sem necessidade de coordenadas x, y). Configure rubrica\_placement: "<<{identificador\_da\_rubrica}>>" e a rubrica será posicionada onde encontrar esse texto. Se o texto aparecer mais de uma vez, a rubrica será posicionada em todos os locais. Observação: o uso de << >> é altamente recomendado para evitar conflitos com o texto, mas não é obrigatório. Ex: "<\<signer1Rubrica>>". Default: ""
    * **require\_cpf** (boolean): Você pedir o CPF do signatário. Se não preencher o número de CPF com o parâmetro "cpf", o signatário preencherá essa informação na assinatura do documento e ela será registrada no relatório de assinaturas.Default: false
    * **validate\_cpf** (boolean): se true valida o CPF, o nome e a data de nascimento na Receita Federal. Para utilizá-lo, é necessário preencher o campo "cpf", e o signatário preencherá a data de nascimento. Default: false.
    * **cpf** (string): Você informar o CPF do signatário. Default: ""
    * **send\_automatic\_email** (boolean): Se **true**, a ZapSign irá enviar um e-mail ao signatário com o link para assinar o documento. Se **false** (default), [você é quem se encarregará de compartilhar o link de assinatura com o signatário](https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta), seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. Observação: para isso funcionar, é obrigatório que o email do signatário seja definido.
    * **send\_automatic\_whatsapp** (boolean): Se **true**, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para assinar o documento. Se **false** (default), [você é quem se encarregará de compartilhar o link de assinatura com o signatário](https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta), seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. \
      Observação: para isso funcionar, é obrigatório que o phone\_country e phone\_number do signatário sejam definidos e **cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em** [**Configurações > Plano**](https://app.zapsign.com.br/conta/configuracoes?tab=plans)**.**
    * **send\_automatic\_whatsapp\_signed\_file** (boolean): Se **true**, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para o arquivo assinado. Se **false** (default), [você é quem se encarregará de compartilhar o link de assinatura com o signatário](https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta), seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. \
      Observação: para isso funcionar, é obrigatório que o phone\_country e phone\_number do signatário sejam definidos e **cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em** [**Configurações > Plano**](https://app.zapsign.com.br/conta/configuracoes?tab=plans)**.**
    * **order\_group** (integer)**:** Caso "signature\_order\_active" esteja ativo no document, esse campo controla a ordem de assinatura. Exemplo: Se o order\_group é 1, esse será o primeiro a assinar, se o order\_group for 2 esse será o segundo a assinar e assim por diante.
    * **custom\_message** (string): (se aplica para **send\_automatic\_email: true** e **send\_automatic\_whatsapp: true**). A custom\_message é a mensagem personalizada que você pode inserir no e-mail enviado pela ZapSign ao signatário. Exemplo: "Olá Fulano, \n Este é o seu contrato de trabalho. \n Abraços, Equipe XPTO". Envios por Whatsapp não devem conter quebras de linhas, tabs e mais de 4 espaços consecutivos". Default: ""
    * **lock\_email** (boolean): Você pode bloquear alterações ao e-mail do signatário. Default: false
    * **blank\_email** (boolean): Você pode não solicitar o email do signatário. Default: false
    * **hide\_email** (boolean): Você pode ocultar o email do signatário no relatório de assinaturas. Default: false
    * **lock\_phone** (boolean): Você pode bloquear alterações ao telefone do signatário. Default: false
    * **blank\_phone** (boolean): Você pode não solicitar o telefone do signatário. Default: false
    * **hide\_phone** (boolean): Você pode ocultar o telefone do signatário no relatório de assinaturas. Default: false
    * **lock\_name** (boolean): Você pode bloquear alterações ao nome do signatário. Default: false
    * **require\_selfie\_photo** (boolean): Você pode pedir que o signatário tire uma selfie enquanto assina. Default: false
    * **require\_document\_photo** (boolean): Você pode pedir que o signatário tire uma foto de seu documento pessoal enquanto assina (ex: RG ou CNH). Default: false
    * **selfie\_validation\_type (string):** Métodos avançados de biometria. Os disponíveis atualmente são:



    <table><thead><tr><th width="159">Selfie_validation_type</th><th width="290">Descrição</th><th width="109">Paises</th><th>Valor por validação</th></tr></thead><tbody><tr><td>"liveness-document-match"</td><td>Reconhecimento facial que solicita que o signatário faça o upload de uma foto do documento de identidade e grave o rosto. Valida que a pessoa é a mesma do documento e que está presente no momento da assinatura. Se você já tem o documento do signatário, leia a seção <strong>R</strong><a href="criar-documento.md#reconhecimento-facial"><strong>econhecimento Facial</strong>.</a></td><td>Todos os países</td><td>15 creditos</td></tr><tr><td>"liveness-NXCD"</td><td>Valida que a pessoa está presente no momento da assinatura com um vídeo passivo (liveness)</td><td>Todos os países</td><td>15 creditos </td></tr><tr><td><p>“face-match-and-datavalid”</p><p><br></p></td><td>Autenticação via verificação facial com correspondência no banco de dados do governo (Serpro), confirmando o CPF e a CNH. Para utilizá-lo, é necessário preencher o parametro <strong>"cpf"</strong></td><td>Disponível somente para o Brasil.</td><td>35 créditos</td></tr><tr><td><p>“identity-verification-global”</p><p><br></p></td><td>Verificação global da identidade do signatário no momento da assinatura, incluindo autenticação do documento e correspondência facial.</td><td>Todos os países</td><td>50 créditos</td></tr></tbody></table>

    Para mais informações sobre os métodos de autenticação, consulte o artigo [Criando documento,](https://clients.zapsign.com.br/help/criando-documentos#autentica%C3%A7%C3%B5es) na nossa central de ajuda.

{% hint style="info" %}
Cada 1 crédito equivale a R$0,10. Assim, 35 créditos equivalem a R$3,50, por exemplo. Adicione créditos na sua conta em [Configurações > Plano > Créditos](https://app.zapsign.com.br/conta/configuracoes/plans?tab=credits) ou converse com a nossa [equipe comercial.](https://api.whatsapp.com/send?phone=551140401991\&text=Quero%20cancelar%20meu%20plano%20e%20gostaria%20de%20atendimento.)
{% endhint %}

Além de configurar seu método de autenticação para cada signatário, você também pode configurar:

* **qualification** (string): Qualificação para aparecer no relatório de assinaturas. Ex: valor "testemunha" irá resultar em "Assinou como testemunha". Default: ""
* **external\_id** (string): ID do signatário na sua aplicação. Default: ""
* **redirect\_link** (string): link para redirecionamento após signatário assinar. Por exemplo: "https://www.seusite.com.br/agradecimento". Irá aparecer como um botão "CONTINUAR" abaixo dos botões "Baixar original" e "Baixar assinado". Lembre-se de inserir o http:// ou https:// no começo do link.  Default: ""

***

### Exemplos de requisição

#### Criar documento a partir de um PDF

{% embed url="https://www.postman.com/zapsign/zapsign-workspace/request/2iib1u6/create-doc-from-upload-pdf?ctx=documentation" %}
Upload de documento PDF
{% endembed %}

#### Criar documento a partir de um DOCX

{% embed url="https://www.postman.com/zapsign/zapsign-workspace/request/fbktel5/create-doc-from-upload-docx?ctx=documentation" %}
Upload de documento DOCX
{% endembed %}

<details>

<summary>Exemplo de requisição em Delphi</summary>

```javascript
var
  json : string;
  ArraySigner : TJSONArray;
  ObjDoc, ObjSigner : TJSONObject;
begin
   ObjDoc := TJSONObject.Create;
   ObjDoc.AddPair('name', 'Contrato de Locação');
   ObjDoc.AddPair('base64_pdf', 'ASFASDFKÇLKÇGÇO#OP%$%#WERP#@&*OSADFJF...');  // Arquivo base64

   ArraySigner := TJSONArray.Create;

   ObjSigner := TJSONObject.Create;
   ObjSigner.AddPair('name', 'João da Silva');
   ObjSigner.AddPair('email', 'joaosilva@gmail.com.br');
   ObjSigner.AddPair('phone_country', '55');
   ObjSigner.AddPair('phone_number', '11888121111');
   // Opcional caso queira impedir alteração 
   ObjSigner.AddPair('lock_name', TJSONTrue.Create);
   ObjSigner.AddPair('lock_email', TJSONTrue.Create);
   ObjSigner.AddPair('lock_phone', TJSONTrue.Create);

   ArraySigner.AddElement(ObjSigner);

   ObjDoc.AddPair('signers', ArraySigner);
   json := ObjDoc.ToString;

   ObjDoc.DisposeOf;

   RESTClient.BaseURL := 'https://api.zapsign.com.br/api/v1/docs/?api_token=...seu token..';
   Request_remete.ClearBody;
   Request_remete.Body.Add(json,ContentTypeFromString('application/json'));
   Request_remete.Execute;
end;
```



</details>

***

### O que faço com a resposta?

Após uma requisição bem sucedida, você deverá receber uma resposta como essa:

```javascript
{
    "open_id": 5,
    "token": "eb9c367a-e62f-4992-8360-b0219deaeecc",
    "status": "pending",
    "name": "Contrato de Admissão João",
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
        },
        {
            "token": "07fb0a0a-4b7d-49a5-bd7b-4958265c4e46",
            "sign_url": "https://app.zapsign.com.br/verificar/07fb0a0a-4b7d-49a5-bd7b-4958265c4e46",
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
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que o endpoint de [Detalhar documento](detalhar-documento.md) seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

O próximo passo é compartilhar os links de assinatura com cada signatário através da sua aplicação. Cada link é composto pela rota base:

```arduino
https://app.zapsign.com.br/verificar/{{signer_token}}
```

No exemplo acima, em que temos dois signatários, você deverá enviar dois links específicos, um para cada signatário, utilizando o respectivo token:

* **João da Silva**: [https://app.zapsign.com.br/verificar/921c115d-4a6e-445d-bdca-03fadedbbc0b](https://app.zapsign.com.br/verificar/921c115d-4a6e-445d-bdca-03fadedbbc0b)
* **Fulano Siclano**: [https://app.zapsign.com.br/verificar/07fb0a0a-4b7d-49a5-bd7b-4958265c4e46](https://app.zapsign.com.br/verificar/07fb0a0a-4b7d-49a5-bd7b-4958265c4e46)

Agora, basta aguardar que os signatários acessem os links e concluam a assinatura!

***

### **Reconhecimento Facial**

O método de autenticação valida a **presença física** da pessoa no momento da assinatura e garante que o rosto corresponde ao documento apresentado.

Se a empresa já possui a foto do documento de identidade do signatário, ela pode ser enviada na requisição para que o signatário apenas grave um vídeo do rosto, e esse vídeo será comparado com o documento que a empresa possui. Para isso, é necessário enviar os seguintes parâmetros:

* **document\_photo\_url** (string): URL pública da **frente** da foto do documento de identidade. Essa foto será comparada com o vídeo gravado pelo signatário durante a assinatura do documento.
* **document\_verse\_photo\_url** (string): URL pública do **verso** da foto do documento de identidade. Ambas as fotos, junto com uma captura do vídeo gravado pelo signatário, serão registradas no relatório de assinaturas.

{% hint style="warning" %}
**Importante**: Este método **não valida a autenticidade do documento de identidade**, apenas verifica a correspondência entre a pessoa e o documento apresentado. Para um nível maior de segurança, consulte o método de autenticação [**"Validação de Identidade"**.](https://clients.zapsign.com.br/help/valida%C3%A7%C3%A3o-de-identidade-da-zapsign)
{% endhint %}

Saiba mais sobre **reconhecimento facial** [clicando **aqui**.](https://clients.zapsign.com.br/help/como-funciona-o-reconhecimento-facial)

### Sobre o base64

Base64 é uma maneira simples de converter um arquivo em texto. Veja aqui uma definição mais completa [https://pt.wikipedia.org/wiki/Base64](https://pt.wikipedia.org/wiki/Base64). Assim, converter o arquivo em base64 e enviar como texto no corpo da requisição é mais fácil do que lidar com **multipart/form-data**, por exemplo.

Para testar a API, você pode converter manualmente seu PDF em base64 através de vários sites, como esse [https://products.aspose.app/pdf/pt/conversion/word-to-base64](https://products.aspose.app/pdf/pt/conversion/word-to-base64)

Quando a API já estiver integrada em seu sistema, procure a função adequada na sua linguagem de programação que pode converter o arquivo em base64.&#x20;

{% hint style="warning" %}
**Observação:** você deve enviar o parâmetro base64\_pdf apenas com a conversão do arquivo em base64. **Não** insira data:application/pdf;base64, na sua string.
{% endhint %}

Não quer trabalhar com base64? **Suba seu PDF em uma url pública e use o parâmetro url\_pdf.**

### Converse com o Gepeto!

Tem alguma duvida? Utilize nossa inteligência artificial treinada com toda a documentação da API =)

{% embed url="https://n8n.zapsign.com.br/webhook/fee2c476-7f23-4a4f-8928-5c7ab081ffcd/chat" %}
