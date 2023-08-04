# MassTransitAllog ( RabbitMQ )
# Exemplo de comunicação entre Producer e Consumer 
![Design sem nome (5)](https://github.com/leandro-guimaraes/MassTransitAllog/assets/85081592/766637cd-a81f-4d98-aa0f-7e36ab7402ff)

## Descrição

O projeto MassTransitAllog é um exemplo simples de comunicação assíncrona entre um Producer e um Consumer utilizando a biblioteca MassTransit, que é uma plataforma de mensagem de código aberto para o .NET.

## Projetos

A solução MassTransitAllog é composta por três projetos principais:

### MassTransitAllog.Shared

O projeto MassTransitAllog.Shared contém a definição de uma interface chamada INotificationCreated, que representa uma notificação criada. A interface possui os seguintes atributos:

```csharp
namespace MassTransitAllog.Shared;

public interface INotificationCreated
{
    public DateTime Date { get; set; }
    public string Message { get; set; }
    public string Author { get; set; }
}
```

### MassTransitAllog.Producer

O projeto MassTransitAllog.Producer é uma API Web ASP.NET Core que atua como o Producer do sistema. Ele possui uma rota "POST" em "/api/Notification" que recebe um objeto JSON contendo os atributos de uma notificação (Date, Message e Author). Ao receber essa notificação, o Producer publica um evento utilizando o MassTransit, que será consumido pelo Consumer.

### MassTransitAllog.Consumer

O projeto MassTransitAllog.Consumer é um aplicativo de console que atua como o Consumer do sistema. Ele consome os eventos de notificação criados pelo Producer e exibe as informações recebidas no console.

## Configuração

### MassTransit - Producer

O projeto MassTransitAllog.Producer utiliza o RabbitMQ como meio de transporte para a comunicação. Ele utiliza as seguintes bibliotecas MassTransit para essa finalidade:

- MassTransit
- MassTransit.Extensions.DependencyInjection
- MassTransit.RabbitMQ

Além disso, ele utiliza o Swagger (Swashbuckle) para fornecer uma interface interativa para testar a rota de criação de notificações.

![! image (httpsgithub comleandro-guimaraesMassTransitAllogassets850815928d4c394e-458e-4428-8d05-25ce5396e002)](https://github.com/leandro-guimaraes/MassTransitAllog/assets/85081592/1e990b47-500e-4f72-9c93-fa91098b8be1)

### MassTransit - Consumer

O projeto MassTransitAllog.Consumer também utiliza o RabbitMQ para consumir os eventos de notificação. Ele utiliza as bibliotecas MassTransit e MassTransit.RabbitMQ para essa finalidade.

### CloudAMQP

O projeto se integra com o serviço CloudAMQP, que é uma instância do RabbitMQ hospedada na nuvem. As configurações de conexão com o RabbitMQ são especificadas no arquivo "Program.cs" do projeto MassTransitAllog.Producer.

## Execução

Para executar o projeto, é necessário primeiro executar o MassTransitAllog.Producer e, em seguida, o MassTransitAllog.Consumer. Isso permitirá a comunicação assíncrona entre os dois projetos.

Ao criar uma notificação através do MassTransitAllog.Producer, você poderá visualizar a notificação sendo recebida pelo MassTransitAllog.Consumer no console.

## Notas

Este projeto foi criado para demonstração e aprendizado da biblioteca MassTransit e sua integração com o RabbitMQ.
