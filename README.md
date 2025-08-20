# Informações gerais

Zapsign é uma plataforma de assinatura eletrônica de documentos que cumpre os requisitos da Medida Provisória 2.200-2/2001, garantindo autenticidade, integridade e não repúdio. Assim, todas as assinaturas realizadas através da ZapSign possuem validade jurídica.\


{% hint style="info" %}
Se você ainda não realizou nenhuma integração com a ZapSign, recomendamos que você inicie pelo ambiente de testes (sandbox) [clicando aqui](https://sandbox.app.zapsign.com.br/acesso/entrar) para evitar cobranças.
{% endhint %}

### Informações chaves para utilizar a API



<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>Trabalhamos com uma API REST</strong>, que utiliza os métodos GET e POST. Lemos tudo em JSON e nossas respostas também são em JSON.</td><td></td><td><a href=".gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr><tr><td><strong>Strings nulas</strong>: Nossa API não aceita strings definidas como <code>null</code>.. Se desejar que o campo fique vazio, envie-o como uma string vazia (<code>""</code>) ou simplesmente omita-o da sua requisição.</td><td></td><td><a href=".gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr><tr><td><strong>Booleanos vs. Strings</strong>: <code>true</code> e <code>false</code> (booleanos) não são equivalentes a <code>"true"</code> e <code>"false"</code> (strings). Certifique-se de usar o tipo correto para evitar falhas nos testes.</td><td></td><td><a href=".gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr></tbody></table>

***

### Gerenciamento de Horários

* **Horários em UTC+0**: Nosso servidor armazena datas e horários no fuso horário UTC+0. Para exibir horários aos usuários, considere que o Brasil está no fuso horário UTC-03:00. A maioria dos frameworks e navegadores realiza automaticamente essa conversão ao lidar com objetos de datetime.

{% hint style="info" %}
Em caso de dúvidas, consulte nosso time de suporte [via Whatsapp](https://api.whatsapp.com/send?phone=551140401991\&text=Ol%C3%A1,%20gostaria%20de%20falar%20com%20o%20suporte) ou pelo email **support@zapsign.com.br.**  Você também pode [falar com nossos especialistas](https://zapsign.com.br/contato/) para soluções personalizadas.
{% endhint %}

### Converse com o Gepeto!

Tem alguma duvida? Utilize nossa inteligência artificial treinada com toda a documentação da API =)

{% embed url="https://n8n.zapsign.com.br/webhook/fee2c476-7f23-4a4f-8928-5c7ab081ffcd/chat" %}
