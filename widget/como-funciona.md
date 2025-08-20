---
description: Configure Widgets no seu site de forma rápida e fácil!
---

# Como funciona o Widget

Com o widget da ZapSign, você integra a assinatura eletrônica diretamente no seu site, garantindo  uma experiência fluida e segura!

{% hint style="warning" %}
Para utilizar o widget, seu aplicativo deve ser uma aplicação web compatível com JavaScript.
{% endhint %}

### Adição do Widget ao seu site

**Para incorporar o widget da ZapSign** ao seu site, **utilize o código HTML fornecido abaixo.**&#x20;

```markup
<!DOCTYPE html>
<html>
<head>
	<title>Teste Widget ZapSign</title>
</head>
<body>
        <!-- Atenção: é importante que você inclua o atributo 'allow' no seu iframe para que possamos pedir a foto do signatario ou foto do documento do signatario caso você tenha optado por algum desses métodos de assinatura -->
	<iframe src="https://app.zapsign.com.br/verificar/TOKEN-DO-SIGNATÁRIO" width="100%" height="800px" allow="camera"></iframe>

	<script>		
			window.onmessage = function(e){
	        if(e.data === 'zs-doc-loaded'){
	        	alert('Doc loaded in iframe')
	        }
	        if(e.data === 'zs-doc-signed'){
	        	alert('Doc signed by signer')
	        }
	        if(e.data === 'zs-signed-file-ready'){
	        	alert('Signed file (final pdf) ready to download')
	        }
			};
	</script>

</body>
</html>
```

{% hint style="info" %}
Cada signatário possui seu próprio token e a vinculação acontece automaticamente ao criar o documento. Vá para o capítulo [Tipos de Tokens e Como Localizá-los](../tipos-de-tokens-e-como-localiza-los.md) para saber mais.
{% endhint %}

***

### Usando Window.onmessage com os Widgets

\
**A função `window.onmessage` é opcional,** mas ajuda a **fornecer feedback imediato aos usuários,** garantindo uma experiência de assinatura mais rápida e eficiente. \
**Os eventos disponíveis incluem:** carregamento do documento, conclusão da assinatura e disponibilidade do arquivo assinado para download.



<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><mark style="background-color:green;"><strong>zs-doc-loaded:</strong></mark> Indica que o PDF foi carregado na tela do signatário. </td><td></td><td><a href="../.gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr><tr><td><mark style="background-color:green;"><strong>zs-doc-signed:</strong></mark> Notifica quando o signatário conclui a assinatura do documento. </td><td></td><td><a href="../.gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr><tr><td><mark style="background-color:green;"><strong>zs-signed-file-ready:</strong></mark> Informa que o PDF assinado está pronto para download (neste momento, o botão "baixar assinado" é ativado).</td><td></td><td><a href="../.gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr></tbody></table>

***

### Atributo Allow

No widget da ZapSign, O atributo `allow` no elemento `<iframe>` permite o acesso à câmera do dispositivo quando necessário, como na captura de foto do signatário ou de um documento durante o processo de assinatura. **Adicionar `allow="camera"` garante que o widget possa solicitar a câmera, se essa opção de assinatura estiver habilitada.**

<figure><img src="https://github.com/AmandaAmani/documenta-ocurso/blob/main/allow%20camera.gif?raw=true" alt="pessoa inserindo um atributo allow dentro do seu iframe para que o usuário final possa utilizar a camera no fluxo de assinatura"><figcaption><p>Usuário utilizando o atributo allow no elemento iframe</p></figcaption></figure>



{% hint style="warning" %}
Documentos que utilizam **autenticação por reconhecimento facial exigem configurações adicionais para garantir a segurança de toda a aplicação.** Se precisar dessa funcionalidade ou tiver dúvidas em como incorporá-la em seu fluxo, entre em contato com nossa equipe de suporte através do e-mail support@zapsign.com.br
{% endhint %}
