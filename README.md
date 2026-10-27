# RabbitMQ com Docker Compose

Este repositório fornece uma configuração Docker Compose para executar um contêiner RabbitMQ com a interface de gerenciamento habilitada. É uma configuração de infraestrutura compartilhada; não contém código de aplicação.

## Requisitos

- Docker com suporte a Docker Compose.
- Portas `5672` e `15672` disponíveis no computador onde o contêiner será executado.

## Uso

Na raiz do repositório, inicie o serviço em segundo plano:

```sh
docker compose up -d
```

O serviço expõe a porta `5672` para conexões AMQP e a porta `15672` para a interface de gerenciamento. Em uma execução local, a interface fica disponível em `http://localhost:15672`.

Para acompanhar os logs:

```sh
docker compose logs -f rabbitmq
```

Para parar e remover o contêiner criado pelo Compose:

```sh
docker compose down
```

O volume nomeado `rabbitmq_data` armazena os dados do RabbitMQ e permanece após `docker compose down`. O Compose também cria a rede bridge `rabbitmq_shared`. O serviço tem uma verificação de saúde baseada em `rabbitmq-diagnostics check_port_connectivity` e está configurado para reiniciar automaticamente.

## Licença

Este repositório não contém um arquivo de licença. A definição de uma licença requer decisão dos responsáveis pelo projeto.
