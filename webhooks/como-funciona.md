# Como funcionam os Webhooks

Webhooks **são notificações automáticas essenciais para a integração entre sistemas,** pois notificam diretamente o seu servidor, eliminando a necessidade de verificar constantemente o status de uma operação.

**Com os webhooks você pode:**

* <mark style="background-color:blue;">**Reduzir de Consultas Repetitivas à API**</mark> para saber o status de um documento (prática comumente chamada de polling;<br>
* <mark style="background-color:blue;">**Sincronizar Sistemas e Integrações**</mark><mark style="background-color:blue;">,</mark> garantindo que informações entre diferentes plataformas estejam sempre atualizadas e consistentes.<br>
* <mark style="background-color:blue;">**Automatizar Processos Pós-Evento**</mark><mark style="background-color:blue;">,</mark> para que tarefas subsequentes sejam feitas automaticamente!

{% hint style="info" %}
Como confirmar a disponibilidade de webhooks? A disponibilidade de webhooks depende do plano, do mercado e das condições da sua conta. Consulte a página oficial de Planos e Preços do seu mercado (https://zapsign.com.br/planos-pre%C3%A7os) e confirme a habilitação em Configurações > Integrações > API ZapSign. Não presuma que o recurso seja gratuito ou esteja incluído em todas as contas. Para integrações, recomendamos usar webhooks para acompanhar eventos, reduzindo consultas repetitivas à API.
{% endhint %}

***

**A Zapsign oferece suporte a webhooks para que você seja notificado de eventos** como criação, assinatura, documento rejeitado, conclusão de documentos ou falha na entrega de email. Quando um evento desse tipo ocorre, enviamos uma requisição HTTP POST para o URL configurado em sua aplicação, contendo detalhes sobre o evento em formato JSON.\
<br>

<figure><img src="../.gitbook/assets/image (4).png" alt="fluxograma em azul mostrando como é o fluxo básico de criação de um webhook. "><figcaption><p>O fluxo básico de um webhook.</p></figcaption></figure>

<br>

{% hint style="warning" %}
A sua aplicação deve retornar o status 200 quando receber um webhook, caso contrário a ZapSign irá retentar o envio, gerando duplicidades e/ou requisições desnecessárias.
{% endhint %}



