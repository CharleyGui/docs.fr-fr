---
title: Two-Way Communication
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 291380d656b0e22c7fdf1cb291c45d05359a95c8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591265"
---
# <a name="two-way-communication"></a>Two-Way Communication
Cet exemple montre comment effectuer une communication en file d'attente bidirectionnelle sur MSMQ. Cet exemple utilise la liaison `netMsmqBinding`. Dans le cas présent, le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple est basé sur la [liaison MSMQ transactionnelle](transacted-msmq-binding.md).  
  
 Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente. Le client envoie des messages à une file d'attente, et le service reçoit les messages de la file d'attente. Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.  
  
 Cet exemple illustre la communication bidirectionnelle à l'aide de files d'attente. Le client envoie des bons de commande à la file d'attente dans les limites de l'étendue d'une transaction. Le service reçoit les bons de commande, les traite puis rappelle le client avec l'état des bons dans la file d'attente dans les limites de l'étendue d'une transaction. Pour faciliter la communication bidirectionnelle, le client et service utilisent tous deux des files d'attente pour y placer les bons de commande et leur état.  
  
 Le contrat de service `IOrderProcessor` définit des opérations de service unidirectionnelles compatibles avec l'utilisation des files d'attente. L'opération de service inclut le point de terminaison de réponse auquel envoyer les états des bons de commande. Le point de terminaison de réponse est l'URI de la file d'attente pour renvoyer l'état du bon de commande au client. L'application de traitement des bons de commande implémente ce contrat.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 Le contrat de réponse auquel envoyer l'état des bons de commande est spécifié par le client. Le client implémente le contrat d'état des bons de commande. Le service utilise le proxy généré de ce contrat pour renvoyer l'état des bons de commande au client.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 L'opération de service traite le bon de commande envoyé. L'attribut <xref:System.ServiceModel.OperationBehaviorAttribute> est appliqué à l'opération de service pour spécifier l'inscription automatique dans la transaction utilisée pour recevoir les messages depuis la file d'attente et au terme automatique de la transaction une fois l'opération de service terminée. La classe `Orders` encapsule la fonctionnalité de traitement des bons de commande. Dans cet exemple, elle ajoute les bons de commande à un dictionnaire. Les opérations peuvent accéder à la transaction à laquelle l'opération de service s'est inscrite depuis la classe `Orders`.  
  
 L'opération de service, outre traiter des bons de commande envoyés, envoie une réponse au client l'informant de l'état des commandes.  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 Le nom de la file d'attente MSMQ est spécifié dans la section appSettings de ce fichier de configuration. Le point de terminaison du service est défini dans la section System.ServiceModel du fichier de configuration.  
  
> [!NOTE]
> Le nom de la file d'attente MSMQ et l'adresse du point de terminaison utilisent des conventions d'adressage légèrement différentes. Le nom de la file d’attente MSMQ utilise un point (.) pour l’ordinateur local et des barres obliques inverses comme séparateur dans son chemin d’accès. L’adresse de point de terminaison Windows Communication Foundation (WCF) spécifie un schéma net. msmq :, utilise « localhost » pour l’ordinateur local et utilise des barres obliques dans son chemin d’accès. Pour lire une file d'attente hébergée sur un ordinateur distant, remplacez « . » et « localhost » par le nom de cet ordinateur.  
  
 Le service est auto-hébergé. Lors de l'utilisation du transport MSMQ, la file d'attente utilisée doit être créée au préalable. Cela peut s'effectuer manuellement ou via le code. Dans cet exemple, le service vérifie l'existence de la file d'attente et la crée, si nécessaire. Le nom de la file d'attente est lu depuis le fichier de configuration. L’adresse de base est utilisée par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le proxy vers le service.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
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
    }  
}  
```

 Le client crée une transaction. La communication avec la file d’attente s’effectue dans les limites d’étendue de la transaction. Elle est donc considérée comme une unité atomique dans laquelle l’intégralité des messages réussissent ou échouent.  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 Le code du client implémente le contrat `IOrderStatus` pour pouvoir recevoir l'état des bons de commande depuis le service. Dans ce cas, le code imprime l'état des bons de commande.  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,
                                                           status);  
    }  
}  
```

 La file d'attente de l'état des bons de commande est créée dans la méthode `Main`. La configuration du client intègre la configuration du service de l'état des bons de commande pour héberger le service de l'état des bons de commande, comme illustré dans l'exemple de configuration suivant.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
              binding="netMsmqBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives. Vous pouvez voir le service recevoir des messages du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
 Le service affiche les informations des bons de commande et indique qu'il renvoie l'état de ces derniers à la file d'attente de l'état des bons de commande.  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 Le client affiche les informations relatives à l'état des bons de commande envoyées par le service.  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
    > [!NOTE]
    > Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, veillez à modifier le nom des points de terminaison dans la configuration du client pour qu'ils correspondent au code client.  
  
 Avec <xref:System.ServiceModel.NetMsmqBinding>, la sécurité du transport est activée par défaut. Il existe deux propriétés pertinentes pour la sécurité de transport MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> et <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` par défaut, le mode d’authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign` . Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine et l’option d’intégration d’Active Directory doit être installée pour MSMQ. Si vous exécutez cet exemple sur un ordinateur qui ne satisfait pas ces critères vous recevez une erreur.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail ou sans intégration Active Directory  
  
1. Si votre ordinateur ne fait pas partie d'un domaine ou ne dispose pas de l'intégration Active Directory, désactivez la sécurité de transport en affectant au mode d'authentification et niveau de protection la valeur `None` comme indiqué dans l'exemple de configuration suivant :  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. La désactivation de la sécurité pour une configuration client génère les éléments suivants :  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
                    binding="netMsmqBinding"
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. Le service pour cet exemple crée une liaison dans `OrderProcessorService`. Ajoutez une ligne de code après que la liaison a été instanciée pour affecter au mode de sécurité la valeur `None`.  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. Assurez-vous de modifier la configuration sur le serveur et le client avant d'exécuter l'exemple.  
  
    > [!NOTE]
    > L'affectation de la valeur `security mode` à `None` revient à affecter la valeur <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> aux modes de sécurité <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, `Message` ou `None`.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
