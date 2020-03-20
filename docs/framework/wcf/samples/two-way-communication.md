---
title: Two-Way Communication
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 56f789fe185cb2885c215e9512e82ae2fbb64a36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143757"
---
# <a name="two-way-communication"></a><span data-ttu-id="fca88-102">Two-Way Communication</span><span class="sxs-lookup"><span data-stu-id="fca88-102">Two-Way Communication</span></span>
<span data-ttu-id="fca88-103">Cet exemple montre comment effectuer une communication en file d'attente bidirectionnelle sur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fca88-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="fca88-104">Cet exemple utilise la liaison `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="fca88-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="fca88-105">Dans le cas présent, le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="fca88-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fca88-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fca88-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fca88-107">Cet échantillon est basé sur la [liaison MSMQ transigée](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="fca88-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="fca88-108">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="fca88-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="fca88-109">Le client envoie des messages à une file d'attente, et le service reçoit les messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="fca88-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="fca88-110">Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="fca88-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="fca88-111">Cet exemple illustre la communication bidirectionnelle à l'aide de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="fca88-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="fca88-112">Le client envoie des bons de commande à la file d'attente dans les limites de l'étendue d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="fca88-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="fca88-113">Le service reçoit les bons de commande, les traite puis rappelle le client avec l'état des bons dans la file d'attente dans les limites de l'étendue d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="fca88-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="fca88-114">Pour faciliter la communication bidirectionnelle, le client et service utilisent tous deux des files d'attente pour y placer les bons de commande et leur état.</span><span class="sxs-lookup"><span data-stu-id="fca88-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="fca88-115">Le contrat de service `IOrderProcessor` définit des opérations de service unidirectionnelles compatibles avec l'utilisation des files d'attente.</span><span class="sxs-lookup"><span data-stu-id="fca88-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="fca88-116">L'opération de service inclut le point de terminaison de réponse auquel envoyer les états des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="fca88-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="fca88-117">Le point de terminaison de réponse est l'URI de la file d'attente pour renvoyer l'état du bon de commande au client.</span><span class="sxs-lookup"><span data-stu-id="fca88-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="fca88-118">L'application de traitement des bons de commande implémente ce contrat.</span><span class="sxs-lookup"><span data-stu-id="fca88-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="fca88-119">Le contrat de réponse auquel envoyer l'état des bons de commande est spécifié par le client.</span><span class="sxs-lookup"><span data-stu-id="fca88-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="fca88-120">Le client implémente le contrat d'état des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="fca88-120">The client implements the order status contract.</span></span> <span data-ttu-id="fca88-121">Le service utilise le proxy généré de ce contrat pour renvoyer l'état des bons de commande au client.</span><span class="sxs-lookup"><span data-stu-id="fca88-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="fca88-122">L'opération de service traite le bon de commande envoyé.</span><span class="sxs-lookup"><span data-stu-id="fca88-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="fca88-123">L'attribut <xref:System.ServiceModel.OperationBehaviorAttribute> est appliqué à l'opération de service pour spécifier l'inscription automatique dans la transaction utilisée pour recevoir les messages depuis la file d'attente et au terme automatique de la transaction une fois l'opération de service terminée.</span><span class="sxs-lookup"><span data-stu-id="fca88-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="fca88-124">La classe `Orders` encapsule la fonctionnalité de traitement des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="fca88-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="fca88-125">Dans cet exemple, elle ajoute les bons de commande à un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="fca88-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="fca88-126">Les opérations peuvent accéder à la transaction à laquelle l'opération de service s'est inscrite depuis la classe `Orders`.</span><span class="sxs-lookup"><span data-stu-id="fca88-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="fca88-127">L'opération de service, outre traiter des bons de commande envoyés, envoie une réponse au client l'informant de l'état des commandes.</span><span class="sxs-lookup"><span data-stu-id="fca88-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

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

 <span data-ttu-id="fca88-128">Le nom de la file d'attente MSMQ est spécifié dans la section appSettings de ce fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="fca88-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="fca88-129">Le point de terminaison du service est défini dans la section System.ServiceModel du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="fca88-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fca88-130">Le nom de la file d'attente MSMQ et l'adresse du point de terminaison utilisent des conventions d'adressage légèrement différentes.</span><span class="sxs-lookup"><span data-stu-id="fca88-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="fca88-131">Le nom de la file d’attente MSMQ utilise un point (.) pour l’ordinateur local et des barres obliques inverses comme séparateur dans son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="fca88-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="fca88-132">L’adresse de point de terminaison de la Windows Communication Foundation (WCF) spécifie un net.msmq : schéma, utilisation du « localhost » pour la machine locale et utilise des barres obliques avant sur son passage.</span><span class="sxs-lookup"><span data-stu-id="fca88-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="fca88-133">Pour lire une file d'attente hébergée sur un ordinateur distant, remplacez « . » et « localhost » par le nom de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fca88-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="fca88-134">Le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="fca88-134">The service is self hosted.</span></span> <span data-ttu-id="fca88-135">Lors de l'utilisation du transport MSMQ, la file d'attente utilisée doit être créée au préalable.</span><span class="sxs-lookup"><span data-stu-id="fca88-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="fca88-136">Cela peut s'effectuer manuellement ou via le code.</span><span class="sxs-lookup"><span data-stu-id="fca88-136">This can be done manually or through code.</span></span> <span data-ttu-id="fca88-137">Dans cet exemple, le service vérifie l'existence de la file d'attente et la crée, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fca88-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="fca88-138">Le nom de la file d'attente est lu depuis le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="fca88-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="fca88-139">L’adresse de base est utilisée par [l’outil utilitaire De métadonnées De ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le proxy au service.</span><span class="sxs-lookup"><span data-stu-id="fca88-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="fca88-140">Le client crée une transaction.</span><span class="sxs-lookup"><span data-stu-id="fca88-140">The client creates a transaction.</span></span> <span data-ttu-id="fca88-141">La communication avec la file d’attente s’effectue dans les limites d’étendue de la transaction. Elle est donc considérée comme une unité atomique dans laquelle l’intégralité des messages réussissent ou échouent.</span><span class="sxs-lookup"><span data-stu-id="fca88-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

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

 <span data-ttu-id="fca88-142">Le code du client implémente le contrat `IOrderStatus` pour pouvoir recevoir l'état des bons de commande depuis le service.</span><span class="sxs-lookup"><span data-stu-id="fca88-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="fca88-143">Dans ce cas, le code imprime l'état des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="fca88-143">In this case, it prints out the order status.</span></span>  

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

 <span data-ttu-id="fca88-144">La file d'attente de l'état des bons de commande est créée dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="fca88-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="fca88-145">La configuration du client intègre la configuration du service de l'état des bons de commande pour héberger le service de l'état des bons de commande, comme illustré dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="fca88-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="fca88-146">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="fca88-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="fca88-147">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="fca88-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="fca88-148">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="fca88-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="fca88-149">Le service affiche les informations des bons de commande et indique qu'il renvoie l'état de ces derniers à la file d'attente de l'état des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="fca88-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
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
  
 <span data-ttu-id="fca88-150">Le client affiche les informations relatives à l'état des bons de commande envoyées par le service.</span><span class="sxs-lookup"><span data-stu-id="fca88-150">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fca88-151">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="fca88-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fca88-152">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="fca88-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fca88-153">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fca88-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fca88-154">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fca88-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fca88-155">Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, veillez à modifier le nom des points de terminaison dans la configuration du client pour qu'ils correspondent au code client.</span><span class="sxs-lookup"><span data-stu-id="fca88-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="fca88-156">Avec <xref:System.ServiceModel.NetMsmqBinding>, la sécurité du transport est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="fca88-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="fca88-157">Il existe deux propriétés pertinentes pour <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` la sécurité des transports MSMQ, et par défaut, le mode d’authentification est réglé `Windows` et le niveau de protection est fixé à `Sign`.</span><span class="sxs-lookup"><span data-stu-id="fca88-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="fca88-158">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine et l’option d’intégration d’Active Directory doit être installée pour MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fca88-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="fca88-159">Si vous exécutez cet exemple sur un ordinateur qui ne satisfait pas ces critères vous recevez une erreur.</span><span class="sxs-lookup"><span data-stu-id="fca88-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="fca88-160">Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail ou sans intégration Active Directory</span><span class="sxs-lookup"><span data-stu-id="fca88-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="fca88-161">Si votre ordinateur ne fait pas partie d'un domaine ou ne dispose pas de l'intégration Active Directory, désactivez la sécurité de transport en affectant au mode d'authentification et niveau de protection la valeur `None` comme indiqué dans l'exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="fca88-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2. <span data-ttu-id="fca88-162">La désactivation de la sécurité pour une configuration client génère les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="fca88-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3. <span data-ttu-id="fca88-163">Le service pour cet exemple crée une liaison dans `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="fca88-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="fca88-164">Ajoutez une ligne de code après que la liaison a été instanciée pour affecter au mode de sécurité la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="fca88-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="fca88-165">Assurez-vous de modifier la configuration sur le serveur et le client avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="fca88-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fca88-166">L'affectation de la valeur `security mode` à `None` revient à affecter la valeur <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> aux modes de sécurité <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, `Message` ou `None`.</span><span class="sxs-lookup"><span data-stu-id="fca88-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fca88-167">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fca88-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fca88-168">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="fca88-168">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fca88-169">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="fca88-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fca88-170">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="fca88-170">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
