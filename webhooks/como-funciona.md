# Como funcionam os Webhooks

Webhooks **são notificações automáticas essenciais para a integração entre sistemas,** pois notificam diretamente o seu servidor, eliminando a necessidade de verificar constantemente o status de uma operação.

**Com os webhooks você pode:**

* <mark style="background-color:blue;">**Reduzir de Consultas Repetitivas à API**</mark> para saber o status de um documento (prática comumente chamada de polling;\

* <mark style="background-color:blue;">**Sincronizar Sistemas e Integrações**</mark><mark style="background-color:blue;">,</mark> garantindo que informações entre diferentes plataformas estejam sempre atualizadas e consistentes.\

* <mark style="background-color:blue;">**Automatizar Processos Pós-Evento**</mark><mark style="background-color:blue;">,</mark> para que tarefas subsequentes sejam feitas automaticamente!

{% hint style="info" %}
<mark style="color:red;">**Preciso ter um Plano de API para usar webhooks?**</mark>**&#x20;Não**, os webhooks estão disponíveis **gratuitamente para todos os usuários.** No entanto, recomendamos fortemente que os usuários da API utilizem webhooks em vez de fazer polling.
{% endhint %}

***

**A Zapsign oferece suporte a webhooks para que você seja notificado de eventos** como criação, assinatura, documento rejeitado, conclusão de documentos ou falha na entrega de email. Quando um evento desse tipo ocorre, enviamos uma requisição HTTP POST para o URL configurado em sua aplicação, contendo detalhes sobre o evento em formato JSON.\
\


<figure><img src="../.gitbook/assets/image (4).png" alt="fluxograma em azul mostrando como é o fluxo básico de criação de um webhook. "><figcaption><p>O fluxo básico de um webhook.</p></figcaption></figure>

\


{% hint style="warning" %}
A sua aplicação deve retornar o status 200 quando receber um webhook, caso contrário a ZapSign irá retentar o envio, gerando duplicidades e/ou requisições desnecessárias.
{% endhint %}



