---
title: Message Correlation
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: c6c68ec36ecee294aa217f77f462dcea31f1e211
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557968"
---
# <a name="message-correlation"></a>Message Correlation

Cet exemple montre comment une application Message Queuing (MSMQ) peut envoyer un message MSMQ à un service Windows Communication Foundation (WCF) et comment les messages peuvent être corrélés entre les applications de l’expéditeur et du récepteur dans un scénario de demande/réponse. Cet exemple utilise la liaison msmqIntegrationBinding. Dans le cas présent, le service est une application console auto-hébergée qui vous permet d'observer le service qui reçoit les messages mis en file d'attente. k

 Le service traite le message reçu de l'expéditeur et lui renvoie un message de réponse. L'expéditeur met en corrélation la réponse qu'il a reçue à la demande qu'il a envoyée à l'origine. Les propriétés `MessageID` et `CorrelationID` du message sont utilisées pour mettre en corrélation les messages de demande et de réponse.

 Le contrat de service `IOrderProcessor` définit une opération de service unidirectionnelle qui convient à l'utilisation de la mise en file d'attente. Un message MSMQ n'ayant pas d'en-tête Action, il n'est donc pas possible de mapper automatiquement des messages MSMQ différents aux contrats d'opération. Par conséquent, il ne peut y avoir qu'un seul contrat d'opération dans ce cas. Si vous souhaitez définir plusieurs contrats d'opération dans le service, l'application doit fournir des informations sur l'en-tête dans le message MSMQ (par exemple, l'étiquette ou correlationID) qui peut être utilisé pour déterminer le contrat d'opération à distribuer.

 En outre, le message MSMQ ne contient pas d'informations concernant les en-têtes qui sont mappés à différents paramètres du contrat d'opération. Par conséquent, il ne peut y avoir qu'un seul paramètre dans le contrat d'opération. Le paramètre est de type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> , qui contient le message MSMQ sous-jacent. Le type « T » dans la classe `MsmqMessage<T>` représente les données sérialisées dans le corps du message MSMQ. Dans cet exemple, le type `PurchaseOrder` est sérialisé dans le corps du message MSMQ.

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 L'opération de service traite le bon de commande et en affiche le contenu et l'état dans la fenêtre de console du service. L’<xref:System.ServiceModel.OperationBehaviorAttribute> configure l’opération pour l’inscrire dans une transaction avec la file d’attente et marquer la transaction comme complète lorsque l’opération est retournée. Le `PurchaseOrder` contient les détails de la commande qui doivent être traités par le service.

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 Le service utilise un client `OrderResponseClient` personnalisé pour envoyer le message MSMQ à la file d'attente. Étant donné que l’application qui reçoit et traite le message est une application MSMQ et non une application WCF, il n’existe pas de contrat de service implicite entre les deux applications. Par conséquent, nous ne pouvons pas créer de proxy à l'aide de l'outil Svcutil.exe dans ce scénario.

 Le proxy personnalisé est fondamentalement le même pour toutes les applications WCF qui utilisent la `msmqIntegrationBinding` liaison pour envoyer des messages. Contrairement aux autres proxys, il n'inclut pas de plage d'opérations de service. Il s'agit uniquement d'une opération d'envoi de message.

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 Le service est auto-hébergé. Lors de l'utilisation du transport d'intégration MSMQ, la file d'attente utilisée doit être créée au préalable. Cela peut s'effectuer manuellement ou via le code. Dans cet exemple, le service contient le code <xref:System.Messaging> pour vérifier l'existence de la file d'attente et la créer si besoin. Le nom de la file d'attente est lu depuis le fichier de configuration.

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
            serviceHost.Open();
            // The service can now be accessed.
            Console.WriteLine("The service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.ReadLine();
            // Close the ServiceHost to shutdown the service.
            serviceHost.Close();
      }
}
```

 La file d'attente MSMQ à laquelle les demandes de bon de commande sont envoyées est spécifiée dans la section appSettings du fichier de configuration. Les points de terminaison du client et du service sont définis dans la section system.serviceModel du fichier de configuration. Tous deux spécifient la liaison `msmqIntegrationbinding`.

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 L'application cliente utilise <xref:System.Messaging> pour envoyer un message durable et transactionnel à la file d'attente. Le corps du message contient le bon de commande.

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
    // Create the purchase order.
    PurchaseOrder po = new PurchaseOrder();
    po.CustomerId = "somecustomer.com";
    po.PONumber = Guid.NewGuid().ToString();
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
    lineItem1.ProductId = "Blue Widget";
    lineItem1.Quantity = 54;
    lineItem1.UnitCost = 29.99F;

    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
    lineItem2.ProductId = "Red Widget";
    lineItem2.Quantity = 890;
    lineItem2.UnitCost = 45.89F;

    po.orderLineItems = new PurchaseOrderLineItem[2];
    po.orderLineItems[0] = lineItem1;
    po.orderLineItems[1] = lineItem2;

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 La file d'attente MSMQ à partir de laquelle les réponses à la commande sont reçues est spécifiée dans une section appSettings du fichier de configuration, comme le montre l'exemple de configuration suivant.

> [!NOTE]
> Le nom de la file d'attente utilise un point (.) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès. L’adresse de point de terminaison WCF spécifie un schéma msmq. formatname et utilise « localhost » pour l’ordinateur local. Un nom de format correct suit msmq.formatname dans l'URI d'après les règles d'adressage MSMQ.

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 L'application cliente enregistre l'`messageID` du message de demande de commande qu'elle envoie au service et attend une réponse du service. Une fois qu'une réponse arrive dans la file d'attente, le client le met en corrélation avec le message de commande qu'il a envoyé à l'aide de la propriété `correlationID` du message, qui contient l'`messageID` du message de commande que le client a envoyé au service à l'origine.

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives. Vous pouvez voir le service recevoir des messages du client et renvoyer une réponse au client. Le client affiche la réponse reçue du service. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.

> [!NOTE]
> Cet exemple requiert l'installation de MSMQ (Message Queuing). Consultez les instructions d'installation de MSMQ dans la section « Voir aussi ».

## <a name="set-up-build-and-run-the-sample"></a>Configurer, générer et exécuter l’exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Si le service est exécuté en premier, il vérifie que la file d'attente existe. Si la file d'attente n'existe pas, le service en crée une. Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ. Procédez comme suit pour créer une file d'attente dans Windows 2008 :

    1. Ouvrez Gestionnaire de serveur dans Visual Studio 2012.

    2. Développez l’onglet **fonctionnalités** .

    3. Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.

    4. Activez la case à cocher **transactionnelle** .

    5. Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.

3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

4. Pour exécuter l’exemple dans une configuration à un seul ordinateur, suivez les instructions de la procédure d' [exécution des exemples de Windows Communication Foundation](running-the-samples.md).

## <a name="run-the-sample-across-computers"></a>Exécuter l’exemple sur plusieurs ordinateurs

1. Copiez les fichiers programme du service figurant dans le dossier \service\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur de service.

2. Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.

3. Dans le fichier Client.exe.config, dans orderQueueName, remplacez « . » par le nom de l'ordinateur de service.

4. Dans le fichier Service.exe.config, modifiez l'adresse de point de terminaison client afin de remplacer « . » par le nom de l'ordinateur client.

5. Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.

6. Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a>Voir aussi

- [Mise en file d'attente dans WCF](../feature-details/queuing-in-wcf.md)
- [Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))
