---
title: Message Queuing to Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 4daa3694287f93aa42a139ed701578e26433bc44
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714830"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="f55a3-102">Message Queuing to Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f55a3-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="f55a3-103">Cet exemple montre comment une application Message Queuing (MSMQ) peut envoyer un message MSMQ à un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f55a3-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="f55a3-104">Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f55a3-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="f55a3-105">Le contrat de service est `IOrderProcessor`, qui définit un service monodirectionnel qui peut être utilisé avec des files d'attente.</span><span class="sxs-lookup"><span data-stu-id="f55a3-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="f55a3-106">Un message MSMQ n'ayant pas d'en-tête Action, il n'est donc pas possible de mapper automatiquement des messages MSMQ différents aux contrats d'opération.</span><span class="sxs-lookup"><span data-stu-id="f55a3-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="f55a3-107">Par conséquent, il ne peut y avoir qu'un seul contrat d'opération.</span><span class="sxs-lookup"><span data-stu-id="f55a3-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="f55a3-108">Si vous souhaitez définir plusieurs contrats d'opération pour le service, l'application doit fournir des informations sur l'en-tête dans le message MSMQ (par exemple, l'étiquette ou correlationID) qui peut être utilisé pour déterminer le contrat d'opération à distribuer.</span><span class="sxs-lookup"><span data-stu-id="f55a3-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>
  
 <span data-ttu-id="f55a3-109">Le message MSMQ ne contient pas d'informations concernant les en-têtes qui sont mappés à différents paramètres du contrat d'opération.</span><span class="sxs-lookup"><span data-stu-id="f55a3-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="f55a3-110">Le paramètre est de type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), lequel contient le message MSMQ sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="f55a3-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="f55a3-111">Le type "T" dans la classe <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) représente les données sérialisées dans le corps du message MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f55a3-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="f55a3-112">Dans cet exemple, le type `PurchaseOrder` est sérialisé dans le corps du message MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f55a3-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="f55a3-113">L'exemple de code suivant présente le contrat de service du service du traitement des commandes.</span><span class="sxs-lookup"><span data-stu-id="f55a3-113">The following sample code shows the service contract of the order processing service.</span></span>  

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

 <span data-ttu-id="f55a3-114">Le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="f55a3-114">The service is self hosted.</span></span> <span data-ttu-id="f55a3-115">Lorsque vous utilisez MSMQ, vous devez créer au préalable la file d'attente utilisée.</span><span class="sxs-lookup"><span data-stu-id="f55a3-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="f55a3-116">Cela peut s'effectuer manuellement ou via le code.</span><span class="sxs-lookup"><span data-stu-id="f55a3-116">This can be done manually or through code.</span></span> <span data-ttu-id="f55a3-117">Dans cet exemple, le service vérifie l'existence de la file d'attente et la crée, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f55a3-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="f55a3-118">Le nom de la file d'attente est lu depuis le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f55a3-118">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="f55a3-119">Le service crée et ouvre <xref:System.ServiceModel.ServiceHost> pour `OrderProcessorService`, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f55a3-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="f55a3-120">Le nom de file d'attente MSMQ est spécifié dans une section appSettings du fichier de configuration, tel qu'indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="f55a3-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f55a3-121">Le nom de la file d'attente utilise un point (.) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="f55a3-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="f55a3-122">L’adresse de point de terminaison WCF spécifie un schéma msmq. formatname et utilise localhost pour l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f55a3-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="f55a3-123">L'adresse de la file d'attente pour les règles d'adressage de chaque nom de format MSMQ suit le schéma msmq.formatname.</span><span class="sxs-lookup"><span data-stu-id="f55a3-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="f55a3-124">L'application cliente est une application MSMQ qui utilise la méthode <xref:System.Messaging.MessageQueue.Send%2A> pour envoyer un message fiable et transactionnel à la file d'attente, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f55a3-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="f55a3-125">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="f55a3-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f55a3-126">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="f55a3-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="f55a3-127">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="f55a3-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="f55a3-128">Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="f55a3-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="f55a3-129">Par exemple, vous pouvez exécuter le client, l'arrêtez, puis démarrer le service et il recevra toujours ses messages.</span><span class="sxs-lookup"><span data-stu-id="f55a3-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="f55a3-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f55a3-130">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="f55a3-131">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f55a3-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f55a3-132">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="f55a3-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f55a3-133">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="f55a3-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f55a3-134">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f55a3-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f55a3-135">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="f55a3-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f55a3-136">Ouvrez Gestionnaire de serveur dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f55a3-136">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f55a3-137">Développez l’onglet **fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="f55a3-137">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f55a3-138">Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="f55a3-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="f55a3-139">Activez la case à cocher **transactionnelle** .</span><span class="sxs-lookup"><span data-stu-id="f55a3-139">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f55a3-140">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f55a3-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f55a3-141">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f55a3-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="f55a3-142">Pour exécuter l’exemple dans une configuration à un seul ordinateur, suivez les instructions de la procédure d' [exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f55a3-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="f55a3-143">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="f55a3-143">To run the sample across computers</span></span>

1. <span data-ttu-id="f55a3-144">Copiez les fichiers programme du service figurant dans le dossier \service\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="f55a3-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="f55a3-145">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="f55a3-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="f55a3-146">Dans le fichier Client.exe.config, dans orderQueueName, remplacez « . » par le nom de l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="f55a3-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="f55a3-147">Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f55a3-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="f55a3-148">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f55a3-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f55a3-149">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f55a3-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f55a3-150">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f55a3-150">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f55a3-151">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f55a3-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f55a3-152">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f55a3-152">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="f55a3-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f55a3-153">See also</span></span>

- [<span data-ttu-id="f55a3-154">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="f55a3-154">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f55a3-155">Guide pratique pour échanger des messages avec des points de terminaison WCF et des applications Message Queuing</span><span class="sxs-lookup"><span data-stu-id="f55a3-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="f55a3-156">Message Queuing</span><span class="sxs-lookup"><span data-stu-id="f55a3-156">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
