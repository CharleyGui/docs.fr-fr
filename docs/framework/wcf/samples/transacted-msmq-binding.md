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
# <a name="transacted-msmq-binding"></a><span data-ttu-id="0dc0a-102">Transacted MSMQ Binding</span><span class="sxs-lookup"><span data-stu-id="0dc0a-102">Transacted MSMQ Binding</span></span>

<span data-ttu-id="0dc0a-103">Cet exemple montre comment effectuer la communication de messages mis en file d'attente avec transactions à l'aide de MSMQ (Message Queuing).</span><span class="sxs-lookup"><span data-stu-id="0dc0a-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="0dc0a-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="0dc0a-105">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="0dc0a-106">Cela signifie que le client envoie ses messages à cette file d'attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="0dc0a-107">Le service reçoit des messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-107">The service receives messages from the queue.</span></span> <span data-ttu-id="0dc0a-108">Par conséquent, il n'est pas nécessaire que le service et le client s'exécutent simultanément pour communiquer à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="0dc0a-109">Lorsque des transactions sont utilisées pour envoyer et recevoir des messages, il y a en fait 2 transactions distinctes.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="0dc0a-110">Lorsque le client envoie des messages dans l’étendue d’une transaction, la transaction est locale au client et au gestionnaire de files d’attente client.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="0dc0a-111">Lorsque le service reçoit des messages dans l'étendue de la transaction, la transaction est locale au service et au gestionnaire de files d'attente de réception.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="0dc0a-112">N’oubliez pas que le client et le service ne participent pas à la même transaction : ils utilisent des transactions différentes lorsqu’ils effectuent leurs opérations (telles que l’envoi et la réception) avec la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="0dc0a-113">Dans cet exemple, le client envoie un lot de messages au service à partir de l’étendue d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="0dc0a-114">Les messages envoyés à la file d’attente sont ensuite reçus par le service dans l’étendue de la transaction définie par le service.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="0dc0a-115">Le contrat de service est `IOrderProcessor`, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="0dc0a-116">L'interface définit un service monodirectionnel utilisable avec les files d'attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-116">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="0dc0a-117">Le comportement de service définit un comportement d'opération avec la valeur `TransactionScopeRequired` affectée à `true`.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="0dc0a-118">Ainsi, l’étendue de transaction qui est utilisée pour récupérer le message de la file d’attente est utilisée par tous les gestionnaires des ressources auxquels accède la méthode.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="0dc0a-119">Si, par ailleurs, la méthode lève une exception, le message est retourné à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="0dc0a-120">Si ce comportement d’opération n’est pas défini, un canal mis en file d’attente crée une transaction pour lire le message à partir de la file d’attente et le valide automatiquement avant sa distribution de sorte qu’en cas d’échec de l’opération, le message est perdu.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="0dc0a-121">Le scénario le plus courant est l’inscription des opérations de service dans la transaction utilisée pour lire le message à partir de la file d’attente, tel qu’indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

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

<span data-ttu-id="0dc0a-122">Le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-122">The service is self hosted.</span></span> <span data-ttu-id="0dc0a-123">Lors de l'utilisation du transport MSMQ, la file d'attente utilisée doit être créée au préalable.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="0dc0a-124">Cela peut s'effectuer manuellement ou via le code.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-124">This can be done manually or through code.</span></span> <span data-ttu-id="0dc0a-125">Dans cet exemple, le service contient du code permettant de vérifier l'existence de la file d'attente et de la créer en cas d'absence.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="0dc0a-126">Le nom de la file d'attente est lu depuis le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="0dc0a-127">L’adresse de base est utilisée par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le proxy vers le service.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

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

<span data-ttu-id="0dc0a-128">Le nom de file d'attente MSMQ est spécifié dans une section appSettings du fichier de configuration, tel qu'indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="0dc0a-129">Le nom de la file d’attente comporte un point (.) pour l’ordinateur local et des barres obliques inverses comme séparateur dans son chemin d’accès lors de la création de la file d’attente à l’aide de <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="0dc0a-130">Le point de terminaison Windows Communication Foundation (WCF) utilise l’adresse de file d’attente avec le schéma net. MSMQ, utilise « localhost » pour désigner l’ordinateur local et utilise des barres obliques dans son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="0dc0a-131">Le client crée une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-131">The client creates a transaction scope.</span></span> <span data-ttu-id="0dc0a-132">La communication avec la file d’attente a lieu dans l’étendue de la transaction, entraînant son traitement en tant qu’une unité atomique dans laquelle tous les messages sont envoyés à la file d’attente ou aucun des messages n’est envoyé à la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="0dc0a-133">La transaction est validée par l'appel de la méthode <xref:System.Transactions.TransactionScope.Complete%2A> sur l'étendue de la transaction.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

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

<span data-ttu-id="0dc0a-134">Pour vérifier que les transactions fonctionnent, modifiez le client en commentant l'étendue de la transaction tel qu'indiqué dans l'exemple de code suivant, reconstruisez la solution et exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="0dc0a-135">La transaction n'étant pas terminée, les messages ne sont pas envoyés à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="0dc0a-136">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0dc0a-137">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="0dc0a-138">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="0dc0a-139">Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="0dc0a-140">Vous pouvez exécuter le client, l'arrêter, puis démarrer le service et il recevra toujours les messages.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0dc0a-141">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="0dc0a-141">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0dc0a-142">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0dc0a-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0dc0a-143">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="0dc0a-144">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="0dc0a-145">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="0dc0a-146">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="0dc0a-146">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="0dc0a-147">Ouvrez Gestionnaire de serveur dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-147">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="0dc0a-148">Développez l’onglet **fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="0dc0a-148">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="0dc0a-149">Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="0dc0a-150">Activez la case à cocher **transactionnelle** .</span><span class="sxs-lookup"><span data-stu-id="0dc0a-150">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="0dc0a-151">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="0dc0a-152">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0dc0a-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="0dc0a-153">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0dc0a-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="0dc0a-154">Avec <xref:System.ServiceModel.NetMsmqBinding>, la sécurité du transport est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="0dc0a-155">La sécurité du transport MSMQ inclut deux propriétés pertinentes : <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> et <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="0dc0a-156">Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="0dc0a-157">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine et l’option d’intégration Active Directory pour MSMQ doit être installée.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="0dc0a-158">Si vous exécutez cet exemple sur un ordinateur qui ne satisfait pas ces critères, vous recevez une erreur.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="0dc0a-159">Pour exécuter l'exemple sur un ordinateur associé à un groupe de travail ou sans intégration Active Directory</span><span class="sxs-lookup"><span data-stu-id="0dc0a-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="0dc0a-160">Si votre ordinateur ne fait pas partie d'un domaine ou ne dispose pas de l'intégration Active Directory, désactivez la sécurité du transport en affectant `None` au mode d'authentification et au niveau de protection, tel qu'indiqué dans l'exemple de code de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

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

2. <span data-ttu-id="0dc0a-161">Assurez-vous de modifier la configuration sur le serveur et le client avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0dc0a-162">L'affectation de `security mode` à `None` revient à affecter <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> à la sécurité <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, `Message` et `None`.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-162">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0dc0a-163">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0dc0a-164">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-164">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0dc0a-165">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0dc0a-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0dc0a-166">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="0dc0a-166">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
