---
description: Struct para a criação de documentos
---

# DocFromTemplate

### Propriedades:

<table><thead><tr><th width="275">Nome</th><th width="213.33333333333331" align="center">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>signer_name</td><td align="center"><pre class="language-go"><code class="lang-go">string
</code></pre></td><td>Nome do signatário</td></tr><tr><td>template_id</td><td align="center"><pre class="language-go"><code class="lang-go">string
</code></pre></td><td>Id do modelo</td></tr><tr><td>data</td><td align="center">List&#x3C;<a href="deparatemplate.md">DeParaTemplate</a>></td><td>Lista de "de para" das variáveis do modelo</td></tr><tr><td>send_automatic_email</td><td align="center"><pre class="language-go"><code class="lang-go">bool
</code></pre></td><td>Se <strong>true</strong>, a ZapSign irá enviar um e-mail ao signatário com o link para assinar o documento. Se <strong>false</strong> (default), você é quem se encarregará de compartilhar o link de assinatura com o signatário, seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. Observação: para isso funcionar, é obrigatório que o email do signatário seja definido com um campo dinâmico, por exemplo {{EMAIL DO CLIENTE}}, e esse valor seja enviado junto da requisição.</td></tr><tr><td>send_automatic_whatsapp</td><td align="center"><pre class="language-go"><code class="lang-go">bool
</code></pre></td><td>Se <strong>true</strong>, a ZapSign irá enviar uma mensagem por WhatsApp ao signatário com o link para assinar o documento. Se <strong>false</strong> (default), <a href="https://docs.zapsign.com.br/documentos/criar-documento#o-que-fazer-com-a-resposta">você é quem se encarregará de compartilhar o link de assinatura com o signatário</a>, seja pelo seu site, widget, WhatsApp, SMS, e-mail, chat etc. Observação: para isso funcionar, é obrigatório que o phone_country e phone_number do signatário sejam definidos e <strong>cada envio automático via WhatsApp custa R$ 0,50. Adicione créditos em</strong> <a href="https://app.zapsign.com.br/conta/configuracoes?tab=plans"><strong>Configurações > Plano</strong></a><strong>.</strong></td></tr><tr><td>custom_message </td><td align="center"><pre class="language-go"><code class="lang-go">string
</code></pre></td><td>(apenas relevante caso <strong>send_automatic_email: true</strong>). A custom_message é a mensagem personalizada que você pode inserir no e-mail enviado pela ZapSign ao signatário. Exemplo: "Olá Fulano, \n Este é o seu contrato de trabalho. \n Abraços, Equipe XPTO". O símbolo \n serve para "pular uma linha" no texto do e-mail. Default: ""</td></tr><tr><td>signer_has_incomplete_fields </td><td align="center"><pre class="language-go"><code class="lang-go">bool
</code></pre></td><td>Caso definido como <em>true</em>, o signatário será direcionado para preencher o formulário do modelo antes de assinar o documento. Observação: valores enviados em <em>data</em> já estarão preenchidos, sem que o signatário precise preencher novamente. Default: false.</td></tr></tbody></table>

