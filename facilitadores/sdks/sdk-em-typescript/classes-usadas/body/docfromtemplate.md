---
description: Classe para a criação de documentos
---

# DocFromTemplate

Classe herdada da classe [Doc](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/doc)

### Propriedades:

<table><thead><tr><th width="275">nome</th><th width="213.33333333333331" align="center">tipo</th><th>descrição</th></tr></thead><tbody><tr><td>signer_name</td><td align="center">string</td><td>nome do signatário</td></tr><tr><td>template_id</td><td align="center">string</td><td>id do modelo</td></tr><tr><td>data</td><td align="center"><a href="https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/deparatemplate">DeParaTemplate</a>[]</td><td>array de "de para" das variáveis do modelo</td></tr><tr><td>send_automatic_email</td><td align="center">boolean</td><td>Se <strong>true</strong>, a ZapSign irá enviar um e-mail ao signatário com o link para assinar o documento. Se <strong>false</strong> (default), você é quem se encarregará de compartilhar o link de assinatura com o signatário, seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. Observação: para isso funcionar, é obrigatório que o email do signatário seja definido com um campo dinâmico, por exemplo {{EMAIL DO CLIENTE}}, e esse valor seja enviado junto da requisição.</td></tr><tr><td>send_automatic_whatsapp</td><td align="center">boolean</td><td>Se <strong>true</strong>, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para assinar o documento. Se <strong>false</strong> (default), <a href="https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta">você é quem se encarregará de compartilhar o link de assinatura com o signatário</a>, seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. Observação: para isso funcionar, é obrigatório que o phone_country e phone_number do signatário sejam definidos e <strong>cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em</strong> <a href="https://app.zapsign.com.br/conta/configuracoes?tab=plans"><strong>Configurações > Plano</strong></a><strong>.</strong></td></tr><tr><td>custom_message </td><td align="center">string</td><td>(apenas relevante caso <strong>send_automatic_email: true</strong>). A custom_message é a mensagem personalizada que você pode inserir no e-mail enviado pela ZapSign ao signatário. Exemplo: "Olá Fulano, \n Este é o seu contrato de trabalho. \n Abraços, Equipe XPTO". O símbolo \n serve para "pular uma linha" no texto do e-mail. Default: ""</td></tr><tr><td>signer_has_incomplete_fields </td><td align="center">boolean</td><td>Caso definido como <em>true</em>, o signatário será direcionado para preencher o formulário do modelo antes de assinar o documento. Observação: valores enviados em <em>data</em> já estarão preenchidos, sem que o signatário precise preencher novamente. Default: false.</td></tr></tbody></table>

### Override:

DocFromTemplate não recebe signatários, então não é possivel realizar metodos como:&#x20;

* getSigners
* setSigners
