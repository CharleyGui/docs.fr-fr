---
title: MSMQ Activation
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 43d6cde7a9342b57933cd3e7475bd4412da86d92
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487555"
---
# <a name="msmq-activation"></a><span data-ttu-id="576dc-102">MSMQ Activation</span><span class="sxs-lookup"><span data-stu-id="576dc-102">MSMQ Activation</span></span>
<span data-ttu-id="576dc-103">Cet exemple illustre comment héberger des applications dans le service d'activation des processus Windows (WAS, Windows Process Activation Service), qui sont lues à partir d'une file d'attente de messages.</span><span class="sxs-lookup"><span data-stu-id="576dc-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="576dc-104">Cet exemple utilise le `netMsmqBinding` et est basé sur le [bidirectionnel Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="576dc-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="576dc-105">Dans cet exemple, le service est une application hébergée par le Web et le client est auto-hébergé. Les résultats, qui s'affichent sur la console, permettent d'observer le statut des bons de commande envoyés.</span><span class="sxs-lookup"><span data-stu-id="576dc-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="576dc-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="576dc-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="576dc-107">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="576dc-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="576dc-108">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="576dc-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  <span data-ttu-id="576dc-109">\<InstallDrive>:\WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="576dc-109">\<InstallDrive>:\WF_WCF_Samples</span></span>  
>   
>  <span data-ttu-id="576dc-110">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les WCF et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="576dc-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="576dc-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="576dc-111">This sample is located in the following directory.</span></span>  
>   
>  <span data-ttu-id="576dc-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="576dc-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>  
  
 <span data-ttu-id="576dc-113">Le service WAS, c’est-à-dire le nouveau mécanisme d’activation des processus pour [!INCLUDE[lserver](../../../../includes/lserver-md.md)], offre des fonctionnalités IIS désormais disponibles avec des applications non HTTP (auparavant disponibles uniquement avec des applications HTTP).</span><span class="sxs-lookup"><span data-stu-id="576dc-113">Windows Process Activation Service (WAS), the new process activation mechanism for [!INCLUDE[lserver](../../../../includes/lserver-md.md)], provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="576dc-114">Windows Communication Foundation (WCF) utilise l’interface d’adaptateur d’écouteur pour communiquer les demandes d’activation qui sont reçus sur les protocoles non-HTTP pris en charge par WCF, tels que TCP, canaux nommés et MSMQ.</span><span class="sxs-lookup"><span data-stu-id="576dc-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="576dc-115">Les fonctionnalités de réception des demandes sur les protocoles non-HTTP sont hébergées par les services Windows managés qui s'exécutent dans SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="576dc-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="576dc-116">Le service d'adaptateur (NetMsmqActivator) de l'écouteur Net.Msmq active les applications en file d'attente en fonction des messages figurant dans cette file.</span><span class="sxs-lookup"><span data-stu-id="576dc-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>  
  
 <span data-ttu-id="576dc-117">Le client envoie des bons de commande au service dans les limites de l’étendue d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="576dc-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="576dc-118">Le service traite les bons de commande qu'il reçoit via cette transaction.</span><span class="sxs-lookup"><span data-stu-id="576dc-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="576dc-119">Le service rappelle ensuite le client en utilisant l'état des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="576dc-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="576dc-120">Pour faciliter la communication bidirectionnelle, le client et service utilisent tous deux des files d'attente pour y placer les bons de commande et leur état.</span><span class="sxs-lookup"><span data-stu-id="576dc-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="576dc-121">Le contrat de service `IOrderProcessor` définit des opérations de service unidirectionnelles compatibles avec les files d'attente.</span><span class="sxs-lookup"><span data-stu-id="576dc-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="576dc-122">L'opération de service utilise le point de terminaison de réponse pour envoyer les états de bon de commande au client.</span><span class="sxs-lookup"><span data-stu-id="576dc-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="576dc-123">L'adresse du point de terminaison de réponse correspond à l'URI de la file d'attente utilisée pour renvoyer l'état des bons de commande au client.</span><span class="sxs-lookup"><span data-stu-id="576dc-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="576dc-124">L'application de traitement des bons de commande implémente ce contrat.</span><span class="sxs-lookup"><span data-stu-id="576dc-124">The order processing application implements this contract.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 <span data-ttu-id="576dc-125">Le contrat de réponse auquel envoyer l'état des bons de commande est spécifié par le client.</span><span class="sxs-lookup"><span data-stu-id="576dc-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="576dc-126">Le client implémente le contrat d'état des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="576dc-126">The client implements the order status contract.</span></span> <span data-ttu-id="576dc-127">Le service utilise le client généré de ce contrat pour renvoyer l'état des bons de commande au client.</span><span class="sxs-lookup"><span data-stu-id="576dc-127">The service uses the generated client of this contract to send order status back to the client.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 <span data-ttu-id="576dc-128">L'opération de service traite le bon de commande envoyé.</span><span class="sxs-lookup"><span data-stu-id="576dc-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="576dc-129">L’attribut <xref:System.ServiceModel.OperationBehaviorAttribute> est appliqué à l’opération de service pour indiquer l’inscription automatique dans la transaction utilisée pour recevoir les messages depuis la file d’attente ainsi que pour spécifier l’arrivée à échéance automatique de cette transaction au terme de l’opération de service.</span><span class="sxs-lookup"><span data-stu-id="576dc-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="576dc-130">La classe `Orders` encapsule la fonctionnalité de traitement des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="576dc-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="576dc-131">Dans cet exemple, elle ajoute les bons de commande à un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="576dc-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="576dc-132">Les opérations peuvent accéder à la transaction à laquelle l'opération de service s'est inscrite depuis la classe `Orders`.</span><span class="sxs-lookup"><span data-stu-id="576dc-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="576dc-133">L'opération de service, outre traiter des bons de commande envoyés, envoie une réponse au client l'informant de l'état des commandes.</span><span class="sxs-lookup"><span data-stu-id="576dc-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }
}
```  
  
 <span data-ttu-id="576dc-134">La liaison du client à utiliser est spécifiée à l'aide d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="576dc-134">The client binding to use is specified using a configuration file.</span></span>  
  
 <span data-ttu-id="576dc-135">Le nom de la file d'attente MSMQ est spécifié dans la section appSettings de ce fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="576dc-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="576dc-136">Le point de terminaison du service est défini dans la section System.ServiceModel de ce même fichier.</span><span class="sxs-lookup"><span data-stu-id="576dc-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="576dc-137">Le nom de la file d'attente MSMQ et l'adresse du point de terminaison utilisent des conventions d'adressage légèrement différentes.</span><span class="sxs-lookup"><span data-stu-id="576dc-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="576dc-138">Le nom de la file d'attente MSMQ utilise un point (.) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="576dc-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="576dc-139">L’adresse de point de terminaison WCF spécifie un net.msmq : schéma, utilise « localhost » pour l’ordinateur local et utilise des barres obliques dans son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="576dc-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="576dc-140">Pour lire une file d'attente hébergée sur un ordinateur distant, remplacez « . » et « localhost » par le nom de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="576dc-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>  
  
 <span data-ttu-id="576dc-141">Un fichier .svc comportant le nom de la classe est utilisé pour héberger le code de service dans WAS.</span><span class="sxs-lookup"><span data-stu-id="576dc-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>  
  
 <span data-ttu-id="576dc-142">Le fichier Service.svc contient une directive permettant de créer `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="576dc-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 <span data-ttu-id="576dc-143">Ce fichier contient également une directive d’assembly permettant de vérifier que System.Transactions.dll est chargé.</span><span class="sxs-lookup"><span data-stu-id="576dc-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>  
  
```svc  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 <span data-ttu-id="576dc-144">Le client crée une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="576dc-144">The client creates a transaction scope.</span></span> <span data-ttu-id="576dc-145">La communication avec le service s’effectuant dans les limites de l’étendue de la transaction, elle est considérée comme une unité atomique dans laquelle l’intégralité des messages réussissent ou échouent.</span><span class="sxs-lookup"><span data-stu-id="576dc-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="576dc-146">La transaction est validée par l'appel de la méthode `Complete` sur l'étendue de la transaction.</span><span class="sxs-lookup"><span data-stu-id="576dc-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
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
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
    serviceHost.Close();  
    }  
```  
  
 <span data-ttu-id="576dc-147">Le code du client implémente le contrat `IOrderStatus` pour pouvoir recevoir l'état des bons de commande depuis le service.</span><span class="sxs-lookup"><span data-stu-id="576dc-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="576dc-148">Dans ce cas, le code imprime l'état des bons de commande.</span><span class="sxs-lookup"><span data-stu-id="576dc-148">In this case, it prints out the order status.</span></span>  
  
```csharp  
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 <span data-ttu-id="576dc-149">La file d'attente de l'état des bons de commande est créée dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="576dc-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="576dc-150">La configuration du client intègre la configuration du service de l'état des bons de commande pour héberger le service de l'état des bons de commande, comme illustré dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="576dc-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="576dc-151">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent sur leur console respective.</span><span class="sxs-lookup"><span data-stu-id="576dc-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="576dc-152">Sur ces consoles, vous pouvez voir le serveur recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="576dc-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="576dc-153">Appuyez sur le bouton ENTER de chaque console pour fermer le serveur et le client.</span><span class="sxs-lookup"><span data-stu-id="576dc-153">Press ENTER in each console window to shut down the server and client.</span></span>  
  
 <span data-ttu-id="576dc-154">Le client affiche les informations d'état des bons de commande envoyées par le serveur :</span><span class="sxs-lookup"><span data-stu-id="576dc-154">The client displays the order status information sent by the server:</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="576dc-155">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="576dc-155">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="576dc-156">Vérifiez que IIS 7.0 est installé, car elles sont obligatoires pour l’activation WAS.</span><span class="sxs-lookup"><span data-stu-id="576dc-156">Ensure that IIS 7.0 is installed, as it is required for WAS activation.</span></span>  
  
2. <span data-ttu-id="576dc-157">Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="576dc-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="576dc-158">En outre, vous devez installer les composants d’activation non-HTTP de WCF :</span><span class="sxs-lookup"><span data-stu-id="576dc-158">In addition, you must install the WCF non-HTTP activation components:</span></span>  
  
    1. <span data-ttu-id="576dc-159">Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="576dc-159">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="576dc-160">Sélectionnez **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="576dc-160">Select **Programs and Features**.</span></span>  
  
    3. <span data-ttu-id="576dc-161">Cliquez sur **activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="576dc-161">Click **Turn Windows Features on or off**.</span></span>  
  
    4. <span data-ttu-id="576dc-162">Sous **résumé des fonctionnalités**, cliquez sur **ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="576dc-162">Under **Features Summary**, click **Add Features**.</span></span>  
  
    5. <span data-ttu-id="576dc-163">Développez le **Microsoft .NET Framework 3.0** nœud et vérifiez la **Activation Non-HTTP de Windows Communication Foundation** fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="576dc-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3. <span data-ttu-id="576dc-164">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="576dc-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="576dc-165">Exécutez le client en exécutant client.exe depuis une fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="576dc-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="576dc-166">Cette exécution génère la file d'attente et envoie un message à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="576dc-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="576dc-167">Laissez le client s'exécuter pour connaître le résultat de la lecture de ce message par le service.</span><span class="sxs-lookup"><span data-stu-id="576dc-167">Leave the client running to see the result of the service reading the message</span></span>  
  
5. <span data-ttu-id="576dc-168">Le service d'activation MSMQ s'exécute comme service réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="576dc-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="576dc-169">Par conséquent, la file d'attente utilisée pour activer l'application doit recevoir et lire les autorisations pour le service réseau.</span><span class="sxs-lookup"><span data-stu-id="576dc-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="576dc-170">Cette spécification peut être ajoutée à l'aide de Message Queuing et de la console MMC :</span><span class="sxs-lookup"><span data-stu-id="576dc-170">This can be added by using the Message Queuing MMC:</span></span>  
  
    1. <span data-ttu-id="576dc-171">À partir de la **Démarrer** menu, cliquez sur **exécuter**, puis tapez `Compmgmt.msc` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="576dc-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>  
  
    2. <span data-ttu-id="576dc-172">Sous **Services et Applications**, développez **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="576dc-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>  
  
    3. <span data-ttu-id="576dc-173">Cliquez sur **files d’attente privées**.</span><span class="sxs-lookup"><span data-stu-id="576dc-173">Click **Private Queues**.</span></span>  
  
    4. <span data-ttu-id="576dc-174">Avec le bouton droit de la file d’attente (servicemodelsamples/service.svc) et choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="576dc-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>  
  
    5. <span data-ttu-id="576dc-175">Sur le **sécurité** , cliquez sur **ajouter** et donner peek et recevoir des autorisations pour Service réseau.</span><span class="sxs-lookup"><span data-stu-id="576dc-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>  
  
6. <span data-ttu-id="576dc-176">Configurez le service d'activation des processus Windows de sorte à assurer la prise en charge de l'activation MSMQ.</span><span class="sxs-lookup"><span data-stu-id="576dc-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>  
  
     <span data-ttu-id="576dc-177">Pour des raisons pratiques, les étapes suivantes sont implémentées dans le fichier de commandes AddMsmqSiteBinding.cmd se trouvant dans le répertoire de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="576dc-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>  
  
    1. <span data-ttu-id="576dc-178">Pour assurer la prise en charge de l'activation de net.msmq, le site Web par défaut doit d'abord être lié au protocole net.msmq.</span><span class="sxs-lookup"><span data-stu-id="576dc-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="576dc-179">Cela peut être fait à l'aide d'appcmd.exe, installé avec l'ensemble d'outils de gestion d'IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="576dc-179">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="576dc-180">À partir d'une invite de commandes avec élévation de privilèges (administrateur), exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="576dc-180">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="576dc-181">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="576dc-181">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="576dc-182">Cette commande ajoute une liaison de site net.msmq au site web par défaut.</span><span class="sxs-lookup"><span data-stu-id="576dc-182">This command adds a net.msmq site binding to the default Web site.</span></span>  
  
    2. <span data-ttu-id="576dc-183">Bien que toutes les applications d’un site partagent la même liaison net.msmq, chacune d’elles peut activer de manière individuelle la prise en charge de net.msmq.</span><span class="sxs-lookup"><span data-stu-id="576dc-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="576dc-184">Pour activer net.msmq pour l'application /servicemodelsamples, exécutez la commande suivante à partir d'une invite de commandes avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="576dc-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="576dc-185">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="576dc-185">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="576dc-186">Cette commande permet d’accéder à l’aide de l’application `http://localhost/servicemodelsamples` et `net.msmq://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="576dc-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>
  
7. <span data-ttu-id="576dc-187">Si vous ne l'avez pas fait précédemment, assurez-vous que le service d'activation MSMQ est activé.</span><span class="sxs-lookup"><span data-stu-id="576dc-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="576dc-188">À partir de la **Démarrer** menu, cliquez sur **exécuter**et le type `Services.msc`.</span><span class="sxs-lookup"><span data-stu-id="576dc-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="576dc-189">Dans la liste des services pour le **adaptateur d’écouteur Net.Msmq**.</span><span class="sxs-lookup"><span data-stu-id="576dc-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="576dc-190">Avec le bouton droit et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="576dc-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="576dc-191">Définir le **Type de démarrage** à **automatique**, cliquez sur **appliquer** et cliquez sur le **Démarrer** bouton.</span><span class="sxs-lookup"><span data-stu-id="576dc-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="576dc-192">Cette étape doit être effectuée à une seule reprise, avant la première utilisation du service d'adaptateur de l'écouteur Net.Msmq.</span><span class="sxs-lookup"><span data-stu-id="576dc-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>  
  
8. <span data-ttu-id="576dc-193">Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="576dc-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="576dc-194">En outre, modifiez le code du client qui envoie le bon de commande en fonction du nom de l'ordinateur figurant dans l'URI de la file d'attente lors de l'envoi de ce bon.</span><span class="sxs-lookup"><span data-stu-id="576dc-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="576dc-195">Utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="576dc-195">Use the following code:</span></span>  
  
    ```csharp  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. <span data-ttu-id="576dc-196">Supprimez la liaison de site net.msmq que vous avez ajoutée dans le cadre de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="576dc-196">Remove the net.msmq site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="576dc-197">Pour des raisons pratiques, les étapes suivantes sont implémentées dans le fichier de commandes RemoveMsmqSiteBinding.cmd situé dans le répertoire de l'exemple :</span><span class="sxs-lookup"><span data-stu-id="576dc-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>  
  
    1. <span data-ttu-id="576dc-198">Supprimez net.msmq de la liste de protocoles actifs en exécutant la commande suivante à partir d'une invite de commandes avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="576dc-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="576dc-199">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="576dc-199">This command is a single line of text.</span></span>  
  
    2. <span data-ttu-id="576dc-200">Supprimez la liaison du site net.msmq en exécutant la commande suivante à partir d'une invite de commandes avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="576dc-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="576dc-201">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="576dc-201">This command is a single line of text.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="576dc-202">L'exécution du fichier de commandes réinitialise le DefaultAppPool de sorte qu'il s'exécute en utilisant .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="576dc-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="576dc-203">Avec le transport de liaison `netMsmqBinding`, la sécurité est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="576dc-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="576dc-204">Les propriétés `MsmqAuthenticationMode` et `MsmqProtectionLevel` déterminent toutes deux le type de sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="576dc-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="576dc-205">Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`.</span><span class="sxs-lookup"><span data-stu-id="576dc-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="576dc-206">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine.</span><span class="sxs-lookup"><span data-stu-id="576dc-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="576dc-207">Si vous exécutez cet exemple sur un ordinateur qui ne fait pas partie d’un domaine, l’erreur suivante est reçue : « L’utilisateur interne message queuing certificat n’existe pas ».</span><span class="sxs-lookup"><span data-stu-id="576dc-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="576dc-208">Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="576dc-208">To run the sample on a computer joined to a workgroup</span></span>  
  
1. <span data-ttu-id="576dc-209">Si votre ordinateur ne fait pas partie d'un domaine, désactivez la sécurité du transport en affectant au mode d'authentification et au niveau de protection la valeur None, tel qu'indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="576dc-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2. <span data-ttu-id="576dc-210">Modifiez la configuration du serveur et du client avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="576dc-210">Change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="576dc-211">L'affectation de `security mode` à `None` revient à affecter `MsmqAuthenticationMode` aux modes de sécurité `MsmqProtectionLevel`, `Message` et `None`.</span><span class="sxs-lookup"><span data-stu-id="576dc-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="576dc-212">Pour permettre l'activation sur un ordinateur associé à un groupe de travail, le service d'activation et le processus de travail doivent tous deux être exécutés sous un compte d'utilisateur spécifique (compte identique pour les deux) et les listes ACL correspondant à ce compte doivent figurer dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="576dc-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>  
  
     <span data-ttu-id="576dc-213">Pour modifier l'identité sous laquelle s'exécute le processus de travail :</span><span class="sxs-lookup"><span data-stu-id="576dc-213">To change the identity that the worker process runs under:</span></span>  
  
    1. <span data-ttu-id="576dc-214">Exécutez Inetmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="576dc-214">Run Inetmgr.exe.</span></span>  
  
    2. <span data-ttu-id="576dc-215">Sous **Pools d’applications**, avec le bouton droit le **AppPool** (généralement **DefaultAppPool**) et choisissez **Set Defaults de Pool d’Application...** .</span><span class="sxs-lookup"><span data-stu-id="576dc-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>  
  
    3. <span data-ttu-id="576dc-216">Modifiez les propriétés Identity en fonction du compte d'utilisateur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="576dc-216">Change the Identity properties to use the specific user account.</span></span>  
  
     <span data-ttu-id="576dc-217">Pour modifier l'identité sous laquelle s'exécute le service d'activation :</span><span class="sxs-lookup"><span data-stu-id="576dc-217">To change the identity that the Activation Service runs under:</span></span>  
  
    1. <span data-ttu-id="576dc-218">Exécutez Services.msc.</span><span class="sxs-lookup"><span data-stu-id="576dc-218">Run Services.msc.</span></span>  
  
    2. <span data-ttu-id="576dc-219">Cliquez sur le **Net.MsmqListener Adapter**, puis choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="576dc-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>  
  
4. <span data-ttu-id="576dc-220">Modifier le compte dans le **ouverture de session** onglet.</span><span class="sxs-lookup"><span data-stu-id="576dc-220">Change the account in the **LogOn** tab.</span></span>  
  
5. <span data-ttu-id="576dc-221">Au niveau des groupes de travail, le service doit également s'exécuter à l'aide d'un jeton non restreint.</span><span class="sxs-lookup"><span data-stu-id="576dc-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="576dc-222">Pour ce faire, utilisez la ligne suivante dans une fenêtre de commande :</span><span class="sxs-lookup"><span data-stu-id="576dc-222">To do this, run the following in a command window:</span></span>  
  
    ```console  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="576dc-223">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="576dc-223">See also</span></span>

- [<span data-ttu-id="576dc-224">Hébergement AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="576dc-224">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
