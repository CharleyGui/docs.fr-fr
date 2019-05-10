---
title: Windows Communication Foundation to Message Queuing
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: e0c4fa3e3f475b2d0996885d8eda91faabc9ba93
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625786"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="ba2f6-102">Windows Communication Foundation to Message Queuing</span><span class="sxs-lookup"><span data-stu-id="ba2f6-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="ba2f6-103">Cet exemple montre comment une application Windows Communication Foundation (WCF) peut envoyer un message à une application Message Queuing (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="ba2f6-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="ba2f6-104">Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="ba2f6-105">Il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="ba2f6-106">Le service reçoit des messages de la file d'attente et traite les commandes.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="ba2f6-107">Le service crée une file d'attente transactionnelle et définit un gestionnaire de messages reçus, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

```csharp
static void Main(string[] args)
{
    if (!MessageQueue.Exists(
              ConfigurationManager.AppSettings["queueName"]))
       MessageQueue.Create(
           ConfigurationManager.AppSettings["queueName"], true);
        //Connect to the queue
        MessageQueue Queue = new
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);
    Queue.ReceiveCompleted +=
                 new ReceiveCompletedEventHandler(ProcessOrder);
    Queue.BeginReceive();
    Console.WriteLine("Order Service is running");
    Console.ReadLine();
}
```

 <span data-ttu-id="ba2f6-108">Lorsqu'un message est reçu dans la file d'attente, le gestionnaire de messages `ProcessOrder` est appelé.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

```csharp
public static void ProcessOrder(Object source,
    ReceiveCompletedEventArgs asyncResult)
{
    try
    {
        // Connect to the queue.
        MessageQueue Queue = (MessageQueue)source;
        // End the asynchronous receive operation.
        System.Messaging.Message msg =
                     Queue.EndReceive(asyncResult.AsyncResult);
        msg.Formatter = new System.Messaging.XmlMessageFormatter(
                                new Type[] { typeof(PurchaseOrder) });
        PurchaseOrder po = (PurchaseOrder) msg.Body;
        Random statusIndexer = new Random();
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
        Console.WriteLine("Processing {0} ", po);
        Queue.BeginReceive();
    }
    catch (System.Exception ex)
    {
        Console.WriteLine(ex.Message);
    }

}
```

 <span data-ttu-id="ba2f6-109">Le service extrait `ProcessOrder` du corps du message MSMQ et traite la commande.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="ba2f6-110">Le nom de file d'attente MSMQ est spécifié dans une section appSettings du fichier de configuration, tel qu'indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
>  <span data-ttu-id="ba2f6-111">Le nom de la file d'attente utilise un point (.) pour l'ordinateur local et des barres obliques inverses comme séparateur dans son chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="ba2f6-112">Le client crée une commande fournisseur et la soumet dans l’étendue d’une transaction, tel qu’indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

```csharp
// Create the purchase order
PurchaseOrder po = new PurchaseOrder();
// Fill in the details
...

OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");

MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    client.SubmitPurchaseOrder(ordermsg);
    scope.Complete();
}
Console.WriteLine("Order has been submitted:{0}", po);

//Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

 <span data-ttu-id="ba2f6-113">Le client utilise un client personnalisé pour envoyer le message MSMQ à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="ba2f6-114">Étant donné que l’application qui reçoit et traite le message est une application MSMQ et non une application WCF, il n’existe aucun contrat de service implicite entre les deux applications.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="ba2f6-115">Par conséquent, nous ne pouvons pas créer de proxy à l'aide de l'outil Svcutil.exe dans ce scénario.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="ba2f6-116">Le client personnalisé est essentiellement la même pour toutes les applications WCF qui utilisent le `MsmqIntegration` liaison pour envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="ba2f6-117">Contrairement aux autres clients, il n'inclut pas de plage d'opérations de service.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="ba2f6-118">Il s'agit uniquement d'une opération d'envoi de message.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-118">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor
{
    public OrderProcessorClient(){}

    public OrderProcessorClient(string configurationName)
        : base(configurationName)
    { }

    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SubmitPurchaseOrder(msg);
    }
}
```

 <span data-ttu-id="ba2f6-119">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ba2f6-120">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ba2f6-121">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="ba2f6-122">Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="ba2f6-123">Par exemple, vous pouvez exécuter le client, l'arrêtez, puis démarrer le service et il recevra toujours ses messages.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
>  <span data-ttu-id="ba2f6-124">Cet exemple requiert l'installation de Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="ba2f6-125">Consultez les instructions d’installation dans [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="ba2f6-125">See the installation instructions in [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="ba2f6-126">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ba2f6-126">To setup, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ba2f6-127">Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba2f6-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ba2f6-128">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="ba2f6-129">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="ba2f6-130">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="ba2f6-131">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="ba2f6-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1. <span data-ttu-id="ba2f6-132">Ouvrez le Gestionnaire de serveur dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-132">Open Server Manager in Visual Studio 2012.</span></span>  
  
    2. <span data-ttu-id="ba2f6-133">Développez le **fonctionnalités** onglet.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-133">Expand the **Features** tab.</span></span>  
  
    3. <span data-ttu-id="ba2f6-134">Avec le bouton droit **files d’attente de messages privées**, puis sélectionnez **New**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4. <span data-ttu-id="ba2f6-135">Vérifier le **transactionnel** boîte.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-135">Check the **Transactional** box.</span></span>  
  
    5. <span data-ttu-id="ba2f6-136">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3. <span data-ttu-id="ba2f6-137">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba2f6-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ba2f6-138">Pour exécuter l’exemple dans une configuration d’ordinateur unique, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba2f6-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ba2f6-139">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="ba2f6-139">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="ba2f6-140">Copiez les fichiers programme du service figurant dans le dossier \service\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2. <span data-ttu-id="ba2f6-141">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3. <span data-ttu-id="ba2f6-142">Dans le fichier Client.exe.config, modifiez l'adresse de point de terminaison client afin de remplacer « . » par le nom de l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4. <span data-ttu-id="ba2f6-143">Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="ba2f6-144">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba2f6-145">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ba2f6-146">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ba2f6-147">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba2f6-148">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ba2f6-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="ba2f6-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba2f6-149">See also</span></span>

- [<span data-ttu-id="ba2f6-150">Guide pratique pour Échanger des Messages avec les points de terminaison WCF et Message Queuing des Applications</span><span class="sxs-lookup"><span data-stu-id="ba2f6-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="ba2f6-151">Message Queuing</span><span class="sxs-lookup"><span data-stu-id="ba2f6-151">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
