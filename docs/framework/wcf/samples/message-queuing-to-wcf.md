---
title: Message Queuing to Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 82e71afc911bff2504be15f7f9f2e736d943972b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584959"
---
# <a name="message-queuing-to-windows-communication-foundation"></a>Message Queuing to Windows Communication Foundation

Cet exemple montre comment une application Message Queuing (MSMQ) peut envoyer un message MSMQ à un service Windows Communication Foundation (WCF). Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.

 Le contrat de service est `IOrderProcessor`, qui définit un service monodirectionnel qui peut être utilisé avec des files d'attente. Un message MSMQ n'ayant pas d'en-tête Action, il n'est donc pas possible de mapper automatiquement des messages MSMQ différents aux contrats d'opération. Par conséquent, il ne peut y avoir qu'un seul contrat d'opération. Si vous souhaitez définir plusieurs contrats d'opération pour le service, l'application doit fournir des informations sur l'en-tête dans le message MSMQ (par exemple, l'étiquette ou correlationID) qui peut être utilisé pour déterminer le contrat d'opération à distribuer.

 Le message MSMQ ne contient pas d'informations concernant les en-têtes qui sont mappés à différents paramètres du contrat d'opération. Le paramètre est de type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), lequel contient le message MSMQ sous-jacent. Le type "T" dans la classe <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) représente les données sérialisées dans le corps du message MSMQ. Dans cet exemple, le type `PurchaseOrder` est sérialisé dans le corps du message MSMQ.

 L'exemple de code suivant présente le contrat de service du service du traitement des commandes.

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 Le service est auto-hébergé. Lorsque vous utilisez MSMQ, vous devez créer au préalable la file d'attente utilisée. Cela peut s'effectuer manuellement ou via le code. Dans cet exemple, le service vérifie l'existence de la file d'attente et la crée, si nécessaire. Le nom de la file d'attente est lu depuis le fichier de configuration.

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 Le service crée et ouvre <xref:System.ServiceModel.ServiceHost> pour `OrderProcessorService`, tel qu'indiqué dans l'exemple de code suivant.

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 Le nom de file d'attente MSMQ est spécifié dans une section appSettings du fichier de configuration, tel qu'indiqué dans l'exemple de configuration suivant.

> [!NOTE]
> Le nom de la file d'attente utilise un point (.) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès. L’adresse de point de terminaison WCF spécifie un schéma msmq. formatname et utilise localhost pour l’ordinateur local. L'adresse de la file d'attente pour les règles d'adressage de chaque nom de format MSMQ suit le schéma msmq.formatname.

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 L'application cliente est une application MSMQ qui utilise la méthode <xref:System.Messaging.MessageQueue.Send%2A> pour envoyer un message fiable et transactionnel à la file d'attente, tel qu'indiqué dans l'exemple de code suivant.

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

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

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives. Vous pouvez voir le service recevoir des messages du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client. Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément. Par exemple, vous pouvez exécuter le client, l'arrêtez, puis démarrer le service et il recevra toujours ses messages.

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

4. Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.

5. Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`

## <a name="see-also"></a>Voir aussi

- [Files d'attente dans WCF](../feature-details/queues-in-wcf.md)
- [Comment : échanger des messages avec des points de terminaison WCF et des applications Message Queuing](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))
