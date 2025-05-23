🧪 Prova Técnica – Desenvolvedor Java

🎯 Objetivo  
Avaliar a capacidade de desenvolver uma API REST utilizando Java, com foco em estrutura de código, modelagem de negócios, domínio de boas práticas, uso de ferramentas e clareza de raciocínio.

💼 Desafio Técnico  
Desenvolver uma API REST para simular um sistema de **cashback** em um ambiente de meios de pagamento.

Funcionalidades obrigatórias  

Criar compra com:  
- Cliente (nome, CPF, e-mail)  
- Valor da compra  
- Data da compra  
- Forma de pagamento (CARTÃO_CREDITO, CARTÃO_DEBITO, PIX)

- Ao criar uma compra, a API deve receber a requisição e imediatamente enviar a transação completa para processamento via fila.  
- O envio pode ser implementado utilizando uma fila simples (por exemplo, `ApplicationEventPublisher` do Spring) ou uma fila real (RabbitMQ, Kafka ou SNS), conforme preferir.  
- O processamento da compra, incluindo o cálculo e crédito do cashback no saldo do cliente, deve ser realizado de forma assíncrona pelo consumidor da fila.  
- A resposta da API para a criação da compra deve ser enviada imediatamente após o envio da transação para a fila, confirmando apenas o recebimento da transação para processamento, sem aguardar o cálculo do cashback.  

A aplicação das regras de cashback deve considerar:  
- Compras até R$ 100 → 5% de cashback  
- De R$ 100,01 até R$ 500 → 10%  
- Acima de R$ 500 → 15%  

Consultar compra por ID, retornando também:  
- Valor do cashback gerado  

Listar compras com filtros opcionais:  
- Por cliente  
- Por forma de pagamento  
- Por intervalo de datas  

Gerar relatório analítico contendo:  
- Total de cashback pago pelo sistema  
- Valor médio de cashback por cliente  
- Total de compras por forma de pagamento  

Simular resgate de cashback:  
- Criar um endpoint que "resgate" o cashback acumulado de um cliente e zere seu saldo de cashback  
- Armazenar o histórico de resgates realizados com: data, valor e cliente  

🔧 Requisitos Técnicos  
Você deve utilizar obrigatoriamente:  

- Java 17 ou Java 21  
- Spring Boot (qualquer versão compatível com Java 17 ou 21)  
- Persistência com JPA + banco de dados H2 ou MongoDB  
- Validações com Bean Validation  
- Mapeamento adequado entre entidades (Cliente, Compra, Cashback, Resgate)  
- Testes unitários (JUnit + Mockito)  
- Versionamento com Git (repositório público no GitHub)  
- README com instruções claras de execução  

**Diferencial:**  
- Implementar a aplicação utilizando **Spring WebFlux**  

✅ Entrega  
Você deve entregar:  

Repositório público no GitHub chamado **prova-java-cashback**  
Um README.md com:  
- Descrição do projeto  
- Como rodar a aplicação (com mvn ou gradle)  
- Exemplos de requisições (via curl, Postman, etc.)  
- Quais funcionalidades foram implementadas  
- Observações (se houver algo não concluído ou limitações)  

🚫 Regras  
- A prova é individual  
- O uso de frameworks e bibliotecas auxiliares é permitido, mas evite gerar código automático (ex: via ChatGPT)  
- A entrega deve ser feita no prazo combinado  
- Qualquer dúvida durante a execução, entre em contato com os avaliadores.  

💡 Dica  
Organize o projeto como se fosse para produção. Esperamos ver boas práticas como:  

- Separação de camadas
- Uso correto de DTOs e entidades  
- Tratamento de erros e respostas adequadas da API  
- Código limpo e testável
