# Criar uma Consulta (Check)

Se você está integrando os checks de antecedentes via API da ZapSign, este é o fluxo que recomendamos seguir para uma implementação correta e uma melhor experiência:

## 1. Criar um check de pessoa ou empresa

O primeiro passo é fazer uma solicitação ao nosso endpoint de criação de check.\
Após o envio, o check entra em processo de verificação.

⏱ **Tempo estimado de processamento:** entre 2 minutos e 2 horas, dependendo das bases de dados consultadas e do país.

## 2. [Utilizar o webhook de resultados](../../webhooks/eventos/antecedentes/consulta-concluida.md)

Recomendamos configurar um webhook para receber automaticamente uma notificação quando o check for concluído.

* Quando o check for finalizado, a ZapSign enviará uma notificação HTTP POST para o webhook configurado no seu sistema, informando que os resultados estão prontos para consulta.
* Assim, você evita a necessidade de fazer múltiplas requisições de consulta (polling) ao servidor.

## 3. Consultar os resultados

Após receber o webhook ou passado o tempo estimado de processamento, você pode obter os resultados através dos nossos endpoints:

* [**Detalhe do Check**](../../detalhe-do-check.md)\
  Este endpoint retorna o JSON completo com todas as informações encontradas, incluindo:
  * Score global
  * Detalhes por dataset
  * Severidades associadas a cada achado
* [**Consultar Check**](../../consultar-check.md)\
  Se precisar de uma versão legível e pronta para compartilhamento, é possível baixar o PDF do check.

{% hint style="success" %}
**Dica:** Utilizar o webhook junto com os endpoints de consulta garante um fluxo mais eficiente e automatizado, evitando esperas desnecessárias e chamadas redundantes à API.
{% endhint %}
