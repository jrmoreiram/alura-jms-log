# Curso de JMS e ActiveMQ: mensageria com Java

### Mãos à obra: Projeto log

Criando um novo projeto para enviar mensagens JMS com prioridades e outras configurações.

**1)** Com ActiveMQ rodando acessado o console de administração:

**2)** No console criado uma nova fila: fila.log

**3)** Agora no Eclipse criado um novo projeto jms-log. Copie o JAR activemq-all-5.12.0.jar do projeto anterior e configure o classpath.

**4)** No projeto jms-log criado uma nova classe ProcessadorLog para consumir as mensagens JMS.

**Em caso de dúvida olhe nas classes criadas no projeto anterior:** [alura-jms](https://github.com/jrmoreiram/alura-jms)

**5)** Na pasta src criado um novo arquivo jndi.properties:
```
java.naming.factory.initial = org.apache.activemq.jndi.ActiveMQInitialContextFactory
java.naming.provider.url = tcp://localhost:61616
queue.LOG = fila.log
```

**6)** Criado a classe para enviar mensagens JMS para a fila.log. Chame a classe de ProdutorMensagemLog.

**7)** Testando o envio da mensagem com um tempo de vida de 5s:
```
Message message = session.createTextMessage("INFO | .....");
producer.send(message,DeliveryMode.NON_PERSISTENT, 1, 5000);
```

**8)** Sem ter nenhum consumidor online, envie uma mensagem para a fila.log. Verifique no console de administração do ActiveMQ se a mensagem realmente chegou.
