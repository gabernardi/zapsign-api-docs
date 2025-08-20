---
description: >-
  Para oferecer uma experiência de uso mais estável e eficiente, implementamos
  políticas de rate limit que garantem a melhor performance possível da nossa
  API para todos os usuários.
---

# Políticas de Rate Limit

### Limite geral e aplicação

Para todos os endpoints públicos da aplicação, **o rate limit é definido como 500 requisições por minuto.** Este limite **é aplicado por IP ou por token de autenticação válido,** garantindo que cada entidade (IP ou token) tenha uma cota justa de uso.

***

### Funcionamento do Rate Limit

* **Limite de Requisições**: Cada IP ou token de autenticação válido está autorizado a realizar até 500 requisições por minuto aos endpoints públicos da aplicação.
* **Janelas de Tempo**: A contagem de requisições é feita em janelas de tempo de 1 minuto, reiniciando a cada novo minuto.
* **Feedback de Limite Atingido**: Quando o limite de 500 requisições por minuto é atingido por um IP ou token específico, as requisições subsequentes dentro do mesmo período de 1 minuto receberão uma resposta com código de status HTTP 429 (Too Many Requests).

### Melhores Práticas para Desenvolvedores

Para evitar atingir o limite de requisições, recomendamos seguir estas melhores práticas:

1. **Implementar Caching**: Utilize técnicas de caching para reduzir o número de requisições repetidas ao servidor.
2. **Otimização de Requisições**: Agrupe múltiplas operações em uma única requisição quando possível.
3. **Gestão de Erros**: Implemente uma lógica de retry exponencial para lidar com respostas de limite excedido (HTTP 429).

###

{% hint style="info" %}
### Suporte e Contato

Caso você encontre problemas relacionados ao rate limit ou precise de um limite personalizado para necessidades específicas, entre em contato com nossa equipe de suporte através do support@zapsign.com.br ou [WhatsApp.](https://api.whatsapp.com/send?phone=551140401991\&text=Ol%C3%A1,%20gostaria%20de%20falar%20com%20o%20suporte)
{% endhint %}
