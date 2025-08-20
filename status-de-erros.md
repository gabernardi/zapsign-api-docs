---
description: >-
  A ZapSign utiliza os códigos de status HTTP padrão. Erros 4xx ocorrem quando
  há um problema na solicitação enviada pelo cliente para a ZapSign. Já os erros
  5xx indicam possiveis problemas no servidor.
---

# Status de erros

Nossa aplicação sempre retorna um código de status 200 para respostas bem-sucedidas. Abaixo, listamos os principais erros que podem ocorrer e como contorná-los:

<table><thead><tr><th width="135">Código</th><th>Referência</th><th>Explicação</th></tr></thead><tbody><tr><td>400</td><td>BAD REQUEST</td><td>A ZapSign processa todas as requisições em JSON, cheque erros no formato como falta de virgulas, base64 mal formatados,etc </td></tr><tr><td>401</td><td>UNAUTHORIZED</td><td>O servidor não autorizou a requisição. Seu Access Token pode estar errado.</td></tr><tr><td>402</td><td>PAYMENT REQUIRED</td><td>O cliente não possui plano API. No ambiente de produção, é obrigatório possuir um plano para utilizar a API em produção. Navegue até configurações>planos e preços ou <a href="https://app.zapsign.co/conta/configuracoes/plans?tab=plans">clique aqui</a>.</td></tr><tr><td>403</td><td>FORBIDDEN</td><td>O servidor não autorizou a requisição. Verifique se o <a href="tipos-de-tokens-e-como-localiza-los.md">API token </a>utilizado corresponde ao ambiente que deseja utilizar.</td></tr><tr><td>404</td><td>NOT FOUND</td><td>O servidor não encontrou o recurso ou não está disposto a divulgar sua existência. Verifique a url utilizada ou o template ID se estiver utilizando <a href="facilitadores/sdks/sdk-em-go/requisicoes-para-documentos/criar-documento-via-modelo.md">modelos dinâmicos</a>.</td></tr><tr><td>406</td><td>NOT ACCEPTABLE</td><td>Verifique se está enviando sua request em Json. Lembre-se de checar strings e booleanos em todo o body.</td></tr><tr><td>429</td><td>TOO MANY REQUESTS</td><td>O cliente excedeu o limite de requisições permitidas em em nosso rate limit.</td></tr></tbody></table>



{% hint style="info" %}
Ainda precisa de ajuda? Consulte nossa equipe de suporte através do support@zapsign.com.br ou [WhatsApp.](https://api.whatsapp.com/send?phone=551140401991\&text=Ol%C3%A1,%20gostaria%20de%20falar%20com%20o%20suporte)
{% endhint %}
