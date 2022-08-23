# Curso de JMS e ActiveMQ: mensageria com Java

### Mãos à obra: Projeto log

Criando um novo projeto para enviar mensagens JMS com prioridades e outras configurações.

**1)** Com ActiveMQ rodando acesse o console de administração:

**2)** No console crie uma nova fila: fila.log

**3)** Agora no Eclipse crie um novo projeto jms-log. Copie o JAR activemq-all-5.12.0.jar do projeto anterior e configure o classpath.

**4)** No projeto jms-log crie uma nova classe ProcessadorLog para consumir as mensagens JMS.

**[Em dúvida olhe nas classes criadas no projeto anterior.](https://github.com/jrmoreiram/alura-jms)**

**5)** Na pasta src crie um novo arquivo jndi.properties:
```
java.naming.factory.initial = org.apache.activemq.jndi.ActiveMQInitialContextFactory
java.naming.provider.url = tcp://localhost:61616
queue.LOG = fila.log
```

**6)** Agora crie a classe para enviar mensagens JMS para a fila.log. Chame a classe de ProdutorMensagemLog.

**7)** Teste o envio da mensagem com um tempo de vida de 5s:
```
Message message = session.createTextMessage("INFO | .....");
producer.send(message,DeliveryMode.NON_PERSISTENT, 1, 5000);
```

**8)** Sem ter nenhum consumidor online, envie uma mensagem para a fila.log. Verifique no console de administração do ActiveMQ se a mensagem realmente chegou.
