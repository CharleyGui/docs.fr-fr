---
title: Transacted MSMQ Binding
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: fa53099caba144f321698f180fe18f7614a1fa64
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596563"
---
# <a name="transacted-msmq-binding"></a>Transacted MSMQ Binding

Cet exemple montre comment effectuer la communication de messages mis en file d'attente avec transactions à l'aide de MSMQ (Message Queuing).

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente. Cela signifie que le client envoie ses messages à cette file d'attente. Le service reçoit des messages de la file d'attente. Par conséquent, il n'est pas nécessaire que le service et le client s'exécutent simultanément pour communiquer à l'aide d'une file d'attente.

Lorsque des transactions sont utilisées pour envoyer et recevoir des messages, il y a en fait 2 transactions distinctes. Lorsque le client envoie des messages dans l’étendue d’une transaction, la transaction est locale au client et au gestionnaire de files d’attente client. Lorsque le service reçoit des messages dans l'étendue de la transaction, la transaction est locale au service et au gestionnaire de files d'attente de réception. N’oubliez pas que le client et le service ne participent pas à la même transaction : ils utilisent des transactions différentes lorsqu’ils effectuent leurs opérations (telles que l’envoi et la réception) avec la file d’attente.

Dans cet exemple, le client envoie un lot de messages au service à partir de l’étendue d’une transaction. Les messages envoyés à la file d’attente sont ensuite reçus par le service dans l’étendue de la transaction définie par le service.

Le contrat de service est `IOrderProcessor`, tel qu'indiqué dans l'exemple de code suivant. L'interface définit un service monodirectionnel utilisable avec les files d'attente.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

Le comportement de service définit un comportement d'opération avec la valeur `TransactionScopeRequired` affectée à `true`. Ainsi, l’étendue de transaction qui est utilisée pour récupérer le message de la file d’attente est utilisée par tous les gestionnaires des ressources auxquels accède la méthode. Si, par ailleurs, la méthode lève une exception, le message est retourné à la file d'attente. Si ce comportement d’opération n’est pas défini, un canal mis en file d’attente crée une transaction pour lire le message à partir de la file d’attente et le valide automatiquement avant sa distribution de sorte qu’en cas d’échec de l’opération, le message est perdu. Le scénario le plus courant est l’inscription des opérations de service dans la transaction utilisée pour lire le message à partir de la file d’attente, tel qu’indiqué dans le code suivant.

```csharp
 // This service class that implements the service contract.
 // This added code writes output to the console window.
 public class OrderProcessorService : IOrderProcessor
 {
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
     public void SubmitPurchaseOrder(PurchaseOrder po)
     {
         Orders.Add(po);
         Console.WriteLine("Processing {0} ", po);
     }
  …
}
```

Le service est auto-hébergé. Lors de l'utilisation du transport MSMQ, la file d'attente utilisée doit être créée au préalable. Cela peut s'effectuer manuellement ou via le code. Dans cet exemple, le service contient du code permettant de vérifier l'existence de la file d'attente et de la créer en cas d'absence. Le nom de la file d'attente est lu depuis le fichier de configuration. L’adresse de base est utilisée par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le proxy vers le service.

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get the MSMQ queue name from appSettings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);

    // Create a ServiceHost for the OrderProcessorService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shut down the service.
        serviceHost.Close();
    }
}
```

Le nom de file d'attente MSMQ est spécifié dans une section appSettings du fichier de configuration, tel qu'indiqué dans l'exemple de configuration suivant.

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> Le nom de la file d’attente comporte un point (.) pour l’ordinateur local et des barres obliques inverses comme séparateur dans son chemin d’accès lors de la création de la file d’attente à l’aide de <xref:System.Messaging>. Le point de terminaison Windows Communication Foundation (WCF) utilise l’adresse de file d’attente avec le schéma net. MSMQ, utilise « localhost » pour désigner l’ordinateur local et utilise des barres obliques dans son chemin d’accès.

Le client crée une étendue de transaction. La communication avec la file d’attente a lieu dans l’étendue de la transaction, entraînant son traitement en tant qu’une unité atomique dans laquelle tous les messages sont envoyés à la file d’attente ou aucun des messages n’est envoyé à la file d’attente. La transaction est validée par l'appel de la méthode <xref:System.Transactions.TransactionScope.Complete%2A> sur l'étendue de la transaction.

```csharp
// Create a client.
OrderProcessorClient client = new OrderProcessorClient();

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

// Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    // Make a queued call to submit the purchase order.
    client.SubmitPurchaseOrder(po);
    // Complete the transaction.
    scope.Complete();
}

// Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

Pour vérifier que les transactions fonctionnent, modifiez le client en commentant l'étendue de la transaction tel qu'indiqué dans l'exemple de code suivant, reconstruisez la solution et exécutez le client.

```csharp
//scope.Complete();
```

La transaction n'étant pas terminée, les messages ne sont pas envoyés à la file d'attente.

Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives. Vous pouvez voir le service recevoir des messages du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client. Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément. Vous pouvez exécuter le client, l'arrêter, puis démarrer le service et il recevra toujours les messages.

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd
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

4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

Avec <xref:System.ServiceModel.NetMsmqBinding>, la sécurité du transport est activée par défaut. La sécurité du transport MSMQ inclut deux propriétés pertinentes : <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> et <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`. Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine et l’option d’intégration Active Directory pour MSMQ doit être installée. Si vous exécutez cet exemple sur un ordinateur qui ne satisfait pas ces critères, vous recevez une erreur.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Pour exécuter l'exemple sur un ordinateur associé à un groupe de travail ou sans intégration Active Directory

1. Si votre ordinateur ne fait pas partie d'un domaine ou ne dispose pas de l'intégration Active Directory, désactivez la sécurité du transport en affectant `None` au mode d'authentification et au niveau de protection, tel qu'indiqué dans l'exemple de code de configuration suivant.

    ```xml
    <system.serviceModel>
      <services>
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"
                 behaviorConfiguration="OrderProcessorServiceBehavior">
          <host>
            <baseAddresses>
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
            </baseAddresses>
          </host>
          <!-- Define NetMsmqEndpoint. -->
          <endpoint
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"
              binding="netMsmqBinding"
              bindingConfiguration="Binding1"
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
          <endpoint address="mex"
                    binding="mexHttpBinding"
                    contract="IMetadataExchange" />
        </service>
      </services>

      <bindings>
        <netMsmqBinding>
          <binding name="Binding1">
            <security mode="None" />
          </binding>
        </netMsmqBinding>
      </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="OrderProcessorServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. Assurez-vous de modifier la configuration sur le serveur et le client avant d'exécuter l'exemple.

    > [!NOTE]
    > L'affectation de `security mode` à `None` revient à affecter <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> à la sécurité <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, `Message` et `None`.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
