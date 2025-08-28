# Atualizar signatário

Imagine que você precisa corrigir o nome ou o telefone de um signatário antes que ele assine o documento. Com este endpoint, **você pode atualizar os atributos de um signatário**, como nome, e-mail, telefone, ou modificar o modo de autenticação. Também é possível bloquear ou desbloquear esses atributos, dependendo da necessidade.&#x20;

{% hint style="warning" %}
Esse endpoint só funciona se o signatário ainda não tiver assinado o documento.
{% endhint %}

{% hint style="info" %}
**Dica**: você pode usar este endpoint para enviar lembretes por e-mail ou WhatsApp. Só é possível enviar no máximo 1 lembrete a cada 30 minutos.
{% endhint %}

### Exemplo de requisição



<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/signers/{{token_signatario}}/`

***

### Headers

<table><thead><tr><th>Name</th><th width="104">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Request Body

<table><thead><tr><th width="223">Name</th><th width="94">Type</th><th>Description</th></tr></thead><tbody><tr><td>redirect_link</td><td>string</td><td>Link para redirecionamento após signatário assinar. Lembre-se de inserir o http:// ou https:// no começo do link. Default: "" </td></tr><tr><td>name</td><td>string</td><td>Nome completo do signatário</td></tr><tr><td>email</td><td>string</td><td>E-mail do signatário</td></tr><tr><td>phone_country</td><td>string</td><td>Código do país do telefone do signatário (Ex: Brasil é 55)</td></tr><tr><td>phone_number</td><td>string</td><td>Telefone (com DDD) do signatário (Ex: 11989118800)</td></tr><tr><td>auth_mode</td><td>string</td><td>Você pode escolher o método de autenticação do signatário. Valores possíveis são: "assinaturaTela" (default), "tokenEmail", "assinaturaTela-tokenEmail", "tokenSms", "assinaturaTela-tokenSms" e "certificadoDigital". Obs: o "certificadoDigital" tem um custo de R$ 0,50 por signatário e CPF tem o custo de R$1,00 por assinatura realizada com sucesso.</td></tr><tr><td>lock_name</td><td>boolean</td><td>Bloquear alteração do nome pelo signatário.</td></tr><tr><td>lock_email</td><td>boolean</td><td>Bloquear alteração do e-mail pelo signatário.</td></tr><tr><td>lock_phone</td><td>boolean</td><td>Bloquear alteração do telefone pelo signatário.</td></tr><tr><td>qualification</td><td>string</td><td>Qualificação para aparecer no relatório de assinaturas. Ex: valor "testemunha" irá resultar em "Assinou como testemunha"</td></tr><tr><td>external_id</td><td>string</td><td>ID externo do signatário na sua aplicação.</td></tr><tr><td>send_automatic_whatsapp</td><td>boolean</td><td>Se <strong>true</strong>, a ZapSign irá enviar o link do documento ao WhatsApp do signatário. Se <strong>false</strong> (default), <strong>você é quem se encarregará de compartilhar o link de assinatura com o signatário.</strong><br>É obrigatório que o phone_country e phone_number do signatário sejam definidos para uso da função. <strong>Cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em</strong> <a href="https://app.zapsign.com.br/conta/configuracoes/plans?tab=credits"><strong>configurações>planos e preços.</strong></a></td></tr><tr><td>send_automatic_email</td><td>boolean</td><td>Se <strong>true</strong>, a ZapSign irá enviar um e-mail ao signatário com o link para assinar o documento. Se <strong>false</strong> (default), <strong>você é quem se encarregará de compartilhar o link de assinatura com o signatário.</strong> É obrigatório que o email do signatário seja definido.</td></tr><tr><td>send_automatic_whatsapp_signed_file</td><td>boolean</td><td>Se <strong>true</strong>, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para o arquivo assinado. Se <strong>false</strong> (default), <strong>você é quem se encarregará de compartilhar o arquivo assinado com o signatário.</strong><br>É obrigatório que o phone_country e phone_number do signatário sejam definidos para uso da função. <strong>Cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em</strong> <a href="https://app.zapsign.com.br/conta/configuracoes/plans?tab=credits"><strong>configurações>planos e preços</strong></a> </td></tr><tr><td><p>selfie_validation_type </p><p></p><p><br></p></td><td>String</td><td>Métodos avançados de biometria. Os disponíveis atualmente são:“face-match-and-datavalid”,“identity-verification-global”,"liveness-document-match" e "liveness-NXCD"</td></tr><tr><td>require_document_photo</td><td>Boolean</td><td>Você pode pedir que o signatário tire uma foto de seu documento pessoal enquanto assina (ex: RG ou CNH). Default: false</td></tr><tr><td>require_selfie_photo </td><td>Boolean</td><td>Você pode pedir que o signatário tire uma selfie enquanto assina. Default: false</td></tr><tr><td><p></p><p></p><p>require_cpf</p><p></p></td><td>Boolean</td><td>Você pedir o CPF do signatário. Se não preencher o número de CPF com o parâmetro "cpf", o signatário preencherá essa informação na assinatura do documento e ela será registrada no relatório de assinaturas.Default: false</td></tr><tr><td>cpf </td><td>String</td><td>Você informar o CPF do signatário.  Default: ""</td></tr><tr><td>validate_cpf</td><td>Boolean</td><td>Se true valida o CPF, o nome e a data de nascimento na Receita Federal. Para utilizá-lo, é necessário preencher o campo "cpf", e o signatário preencherá a data de nascimento. Default: false.</td></tr><tr><td>signature_placement</td><td>string</td><td>Permite posicionar a assinatura no documento usando um texto âncora (sem necessidade de coordenadas x, y). Configure signature_placement: "&#x3C;&#x3C;{identificador_da_assinatura}>>" e a assinatura será posicionada onde encontrar esse texto. Se o texto aparecer mais de uma vez, a assinatura será posicionada em todos os locais. Observação: o uso de &#x3C;&#x3C; >> é altamente recomendado para evitar conflitos com o texto, mas não é obrigatório. Ex: "&#x3C;>". Default: ""</td></tr><tr><td>rubrica_placement</td><td>string</td><td>Permite posicionar a rubrica no documento usando um texto âncora (sem necessidade de coordenadas x, y). Configure rubrica_placement: "&#x3C;&#x3C;{identificador_da_rubrica}>>" e a rubrica será posicionada onde encontrar esse texto. Se o texto aparecer mais de uma vez, a rubrica será posicionada em todos os locais. Observação: o uso de &#x3C;&#x3C; >> é altamente recomendado para evitar conflitos com o texto, mas não é obrigatório. Ex: "&#x3C;>". Default: ""</td></tr></tbody></table>

{% tabs %}
{% tab title="200 Signatário atualizado com sucesso" %}
```json
{
    "external_id": "",
    "sign_url": "https://app.zapsign.com.br/verificar/b5ade7f0-8bc2-463a-8475-d67eb7f58167",
    "token": "b5ade7f0-8bc2-463a-8475-d67eb7f58167",
    "status": "link-opened",
    "name": "Jane Doe",
    "lock_name": false,
    "email": "",
    "lock_email": false,
    "hide_email": false,
    "blank_email": false,
    "phone_country": "55",
    "phone_number": "",
    "lock_phone": false,
    "hide_phone": false,
    "blank_phone": false,
    "times_viewed": 2,
    "last_view_at": "2023-07-06T05:34:37.776131Z",
    "signed_at": null,
    "auth_mode": "assinaturaTela",
    "qualification": "",
    "require_selfie_photo": false,
    "require_document_photo": false,
    "geo_latitude": null,
    "geo_longitude": null,
    "redirect_link": "",
    "signature_image": null,
    "visto_image": null,
    "document_photo_url": "",
    "document_verse_photo_url": "",
    "selfie_photo_url": "",
    "selfie_photo_url2": "",
    "send_via": "email",
    "send_automatic_whatsapp_signed_file": null,
}
```
{% endtab %}
{% endtabs %}
