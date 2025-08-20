# Como funciona Carimbo de Tempo?

O Carimbo de Tempo é uma solução de segurança avançada que **fortalece o processo de assinatura** de documentos ao registrar **não apenas a data e hora do dispositivo do signatário, mas também a data e hora de um servidor externo** aprovado por uma Autoridade Certificadora de Tempo (ACT).

***

### Na ZapSign, temos dois jeitos de aplicar o carimbo de Tempo

Você pode usar dois endpoints diferentes para adicionar o carimbo de tempo a um documento já assinado, **cada um deles traz resultados diferentes no PDF.**

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>Carimbo de tempo Padrão</strong></td><td>Documento assinado eletronicamente e você quer adicionar um selo de integridade adicional</td><td><a href="../.gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr><tr><td><strong>Carimbo de tempo com preservação de assinatura</strong></td><td>Documento já assinado com certificado digital ICP-Brasil e você quer manter essa assinatura visível no ITI</td><td><a href="../.gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr></tbody></table>

### &#x20;Comparando os dois caminhos

| Objetivo                                  | Endpoint                  | Resultado visual                                     |
| ----------------------------------------- | ------------------------- | ---------------------------------------------------- |
| Apenas garantir a data/hora               | `/timestamp/`             | Exibe carimbo técnico no validador, sem nome         |
| Garantir data/hora + mostrar quem assinou | `/timestamp/no-signature` | Mostra nome do signatário + carimbo ICP no validador |

***

### Requisitos

* Documento assinado com até **10MB** (PDF ou DOCX);
* Chave da API ativa;
* Função ativa no plano &#x20;

{% hint style="info" %}
[Fale com um especialista](https://api.whatsapp.com/send?phone=551140401991\&text=Ol%C3%A1,%20sou%20amanda@zapsign.com.br%20e%20gostaria%20de%20falar%20com%20vendas%20para%20comprar%20Carimbo%20de%20tempo) para adicionar a funcionalidade ao seu plano!
{% endhint %}

Na proxima seção, vamos testar a aplicação do Carimbo de Tempo Padrão ao documento.
