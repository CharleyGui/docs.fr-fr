---
title: Dead Letter Queues
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 8ea2ea530db8745c3802f9f39793ffd77ddd0008
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575288"
---
# <a name="dead-letter-queues"></a>Dead Letter Queues
Cet exemple montre comment gérer et traiter des messages n'ayant pas pu être remis. Il est basé sur l’exemple de [liaison MSMQ transactionnelle](transacted-msmq-binding.md) . Cet exemple utilise la liaison `netMsmqBinding`. Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

> [!NOTE]
> Cet exemple illustre la file d’attente de lettres mortes d’une application qui est uniquement disponible sur Windows Vista. L’exemple peut être modifié pour utiliser les files d’attente par défaut à l’ensemble du système pour MSMQ 3,0 sur Windows Server 2003 et Windows XP.

 Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente. Cela signifie que le client envoie ses messages à cette file d'attente. Le service reçoit des messages de la file d'attente. Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.

 Parce que la communication en file d'attente peut impliquer une certaine latence, vous pouvez associer une valeur de durée de vie au message afin de garantir que le message n'est pas remis à l'application une fois le délai passé. Il existe également des cas où une application doit être informée en cas d'échec de remise du message. Dans tous ces cas, comme lorsque la durée de vie du message a expiré ou que le message n'a pas été remis, il est mis dans une file d'attente de lettres mortes. L’application émettrice peut lire ensuite les messages dans la file d’attente de lettres mortes et effectuer des actions correctives qui varient d’aucune action à la correction des raisons pour remise non réussie et au renvoi du message.

 La file d’attente de lettres mortes dans la liaison `NetMsmqBinding` est exprimée dans les propriétés suivantes :

- La propriété <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> permet d'exprimer le type de file d'attente de lettres mortes requis par le client. L'énumération a les valeurs suivantes :

- `None` : aucune file d'attente de lettres mortes n'est requise par le client.

- `System`  la file d'attente de lettres mortes du système est utilisée pour stocker les lettres mortes. La file d'attente de lettres mortes du système est partagée par toutes les applications exécutées sur l'ordinateur.

- `Custom` : une file d'attente de lettres mortes personnalisée spécifiée à l'aide de la propriété <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> est utilisée pour stocker des messages morts. Cette fonctionnalité est disponible uniquement sur Windows Vista. Elle est utilisée lorsque l'application doit utiliser sa propre file d'attente de lettres mortes au lieu de la partager avec d'autres applications exécutées sur le même ordinateur.

- La propriété <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> permet d'exprimer la file d'attente spécifique à utiliser comme file d'attente de lettres mortes. Disponible uniquement dans Windows Vista.

 Dans cet exemple, le client envoie un lot de messages au service à partir de l’étendue d’une transaction et indique un valeur arbitraire faible de durée de vie pour ces messages (approximativement 2 secondes). Le client indique également la file d'attente de lettres mortes personnalisée à utiliser pour mettre les messages qui ont expiré en file d'attente.

 L'application cliente peut lire les messages dans la file d'attente de lettres mortes. Elle tente ensuite de renvoyer le message ou de corriger l'erreur qui a provoqué la mise en file d'attente de lettres mortes du message et de renvoyer le message. Dans l'exemple, le client affiche un message d'erreur.

 Le contrat de service est `IOrderProcessor`, tel qu'indiqué dans l'exemple de code suivant.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Le code de service dans l’exemple est celui de la [liaison MSMQ traitée](transacted-msmq-binding.md).

 La communication avec le service a lieu dans l'étendue d'une transaction. Le service lit des messages à partir de la file d'attente, effectue l'opération puis affiche les résultats de cette dernière. L'application crée également une file d'attente de lettres mortes pour les messages de lettres mortes.

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

        // Create the purchase order
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

        //Create a transaction scope.
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 La configuration du client spécifie une durée courte pour que le message atteigne le service. Si le message n'est pas transmis dans la durée définie, il expire et est déplacé vers la file d'attente de lettres mortes.

> [!NOTE]
> Le client a la possibilité de remettre le message à la file d'attente du service dans le délai spécifié. Pour être sûr de voir le service de lettres mortes en action, vous devez exécuter le client avant de démarrer le service. Le message expire et est remis au service de lettres mortes.

 L'application doit définir la file d'attente à utiliser comme file d'attente de lettres mortes. Si aucune file d’attente n’est spécifiée, la file d’attente de lettres mortes transactionnelle du système par défaut est utilisée pour mettre en file d’attente les messages morts. Dans cet exemple, l'application cliente spécifie sa propre file d'attente de lettres mortes.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 Le service de lettres mortes lit les messages à partir de la file d'attente de lettres mortes. Le service de message de lettres mortes implémente le contrat `IOrderProcessor`. Toutefois, son implémentation n'est pas de traiter les commandes. Le service de message de lettres mortes est un service client et n'a pas la fonctionnalité de traitement de commandes.

> [!NOTE]
> La file d'attente de lettres mortes est une file d'attente cliente et est locale sur le gestionnaire de files d'attente client.

 L'implémentation du service de lettres mortes vérifie le motif d'échec de remise d'un message et prend les mesures adéquates. Le motif d'échec de remise d'un message est capturé dans les deux énumérations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> et <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Vous pouvez récupérer <xref:System.ServiceModel.Channels.MsmqMessageProperty> dans <xref:System.ServiceModel.OperationContext> comme illustré dans l'exemple de code suivant :

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 Les messages dans la file d'attente de lettres mortes sont des messages adressés au service qui est le traite le message. Par conséquent, lorsque le service de message de lettres mortes lit des messages à partir de la file d’attente, la couche de canal Windows Communication Foundation (WCF) recherche l’incompatibilité dans les points de terminaison et ne distribue pas le message. Dans ce cas, le message est adressé au service de traitement des commandes mais est reçu par le service de lettres mortes. Pour recevoir un message adressé à un point de terminaison différent, un filtre d'adresse pouvant correspondre à n'importe quelle adresse est spécifié dans `ServiceBehavior`. Cela est requis pour traiter correctement les messages lus à partir de la file d'attente de lettres mortes.

 Dans cet exemple, le service de message de lettres mortes renvoie le message si la raison de l’échec est que le message a expiré. Pour toutes les autres raisons, il affiche l’échec de la remise, comme indiqué dans l’exemple de code suivant :

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 L'exemple suivant affiche la configuration pour un message de lettres mortes :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 Lors de l'exécution de l'exemple, vous devez exécuter 3 fichiers exécutables pour voir comment la file d'attente de lettres mortes fonctionne pour chaque application : le client, le service et un service de lettres mortes qui lit les messages de la file d'attente de lettres mortes pour chaque application et renvoie le message au service. Ce sont toutes des applications console avec la sortie dans les fenêtres de console.

> [!NOTE]
> En raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément. Vous pouvez exécuter le client, l'arrêter, puis démarrer le service et il recevra encore ses messages. Vous devez démarrer le service et le fermer pour que la file d'attente soit créée.

 Lorsque le client est exécuté, il affiche le message :

```console
Press <ENTER> to terminate client.
```

 Le client a essayé d'envoyer le message mais avec un délai d'attente court, le message a expiré et est maintenant mis dans la file d'attente de lettres mortes pour chaque application.

 Vous exécutez alors le service de lettres mortes qui lit le message, affiche le code d'erreur et renvoie le message au service.

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 Le service démarre puis lit le message renvoyé et le traite.

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Si le service est exécuté en premier, il vérifie que la file d'attente existe. Si la file d'attente n'existe pas, le service en crée une. Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ. Procédez comme suit pour créer une file d'attente dans Windows 2008 :

    1. Ouvrez Gestionnaire de serveur dans Visual Studio 2012.

    2. Développez l’onglet **fonctionnalités** .

    3. Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.

    4. Activez la case à cocher **transactionnelle** .

    5. Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.

3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, modifiez les noms de file d’attente de manière appropriée, en remplaçant localhost par le nom complet de l’ordinateur et suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail

1. Si votre ordinateur ne fait pas partie d'un domaine, désactivez la sécurité du transport en affectant `None` au mode d'authentification et au niveau de protection, tel qu'indiqué dans l'exemple de configuration suivant :

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Assurez-vous que le point de terminaison est associé à la liaison en définissant l’attribut `bindingConfiguration` du point de terminaison.

2. Assurez-vous de modifier la configuration sur DeadLetterService, le serveur et le client avant d'exécuter l'exemple.

    > [!NOTE]
    > L'affectation de `security mode` à `None` revient à affecter `MsmqAuthenticationMode` aux modes de sécurité `MsmqProtectionLevel`, `Message` et `None`.

## <a name="comments"></a>Commentaires
 Avec le transport de liaison `netMsmqBinding`, la sécurité est activée par défaut. Les propriétés `MsmqAuthenticationMode` et `MsmqProtectionLevel` déterminent toutes deux le type de sécurité du transport. Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`. Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine. Si vous exécutez cet exemple sur un ordinateur ne faisant pas partie d'un domaine, vous recevez l'erreur suivante : "Le certificat Message Queuing interne pour l'utilisateur n'existe pas."

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
