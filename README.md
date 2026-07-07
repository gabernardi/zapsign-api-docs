---
description: >-
  Crie com a API da ZapSign — gere, envie e acompanhe documentos para assinatura
  eletrônica de forma programática.
---

# ZapSign Developer Docs

{% columns %}
{% column width="66.66666666666666%" %}
**Integre com a ZapSign em minutos.**

**Uma chamada de API. Documentos prontos para assinatura eletrônica, integrados ao seu fluxo do início ao fim.**

Crie, envie e acompanhe documentos com segurança, visibilidade de status e validade jurídica — sem depender de processos manuais.
{% endcolumn %}

{% column width="33.33333333333334%" %}
<figure><img src=".gitbook/assets/shield-3d.webp" alt=""><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

<a href="como-comecar.md#e-como-obter-meu-api-token" class="button primary">Obter API key</a> <a href="como-comecar.md" class="button secondary">API overview</a>

{% hint style="info" %}
Se você ainda não realizou nenhuma integração com a ZapSign, recomendamos que você inicie pelo ambiente de testes (sandbox) [clicando aqui](https://sandbox.app.zapsign.com.br/acesso/entrar) para evitar cobranças.
{% endhint %}

### Informações-chave para usar a API

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>API REST</strong>: use os métodos GET e POST. Envie e receba dados em JSON.</td><td></td><td></td></tr><tr><td><strong>Campos vazios</strong>: não envie <code>null</code> em strings. Use <code>""</code> ou omita o campo.</td><td></td><td></td></tr><tr><td><strong>Tipos importam</strong>: <code>true</code> e <code>false</code> são booleanos. <code>"true"</code> e <code>"false"</code> são strings.</td><td></td><td></td></tr></tbody></table>

### Gerenciamento de Horários

* **Horários em UTC+0**: Nosso servidor armazena datas e horários no fuso horário UTC+0. Para exibir horários aos usuários, considere que o Brasil está no fuso horário UTC-03:00. A maioria dos frameworks e navegadores realiza automaticamente essa conversão ao lidar com objetos de datetime.

{% hint style="info" %}
Em caso de dúvidas, consulte nosso time de suporte [via Whatsapp](https://api.whatsapp.com/send?phone=551140401991\&text=Ol%C3%A1,%20gostaria%20de%20falar%20com%20o%20suporte) ou pelo email **support@zapsign.com.br.** Você também pode [falar com nossos especialistas](https://zapsign.com.br/contato/) para soluções personalizadas.
{% endhint %}

### Tire suas dúvidas com o Ask

Use o Ask, nosso assistente de IA, para encontrar respostas rápidas sobre a API da ZapSign.

Para começar, clique em **Ask** no topo da página, ao lado da busca.
