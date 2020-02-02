---
title: Poison Message Handling in MSMQ 4,0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: cc4da0deea0de2cd8b3bb8e8f2ba9b8a17e3cc60
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919397"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="c3045-102">Poison Message Handling in MSMQ 4,0</span><span class="sxs-lookup"><span data-stu-id="c3045-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="c3045-103">Cet exemple montre comment assurer la gestion des messages incohérents dans un service.</span><span class="sxs-lookup"><span data-stu-id="c3045-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="c3045-104">Cet exemple est basé sur l’exemple de [liaison MSMQ transactionnelle](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="c3045-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="c3045-105">Cet exemple utilise `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="c3045-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="c3045-106">Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="c3045-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="c3045-107">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="c3045-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="c3045-108">Cela signifie que le client envoie ses messages à cette file d'attente.</span><span class="sxs-lookup"><span data-stu-id="c3045-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="c3045-109">Le service reçoit des messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="c3045-109">The service receives messages from the queue.</span></span> <span data-ttu-id="c3045-110">Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="c3045-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="c3045-111">Un message incohérent est un message qui est lu à plusieurs reprises à partir d’une file d’attente lorsque le service qui le lit ne parvient pas à le traiter et met donc fin à la transaction sous laquelle le message est lu.</span><span class="sxs-lookup"><span data-stu-id="c3045-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="c3045-112">Dans ce cas, le message est de nouveau réessayé.</span><span class="sxs-lookup"><span data-stu-id="c3045-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="c3045-113">Cela peut théoriquement continuer indéfiniment en cas de problème avec le message.</span><span class="sxs-lookup"><span data-stu-id="c3045-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="c3045-114">Notez que cela peut uniquement se produire lorsque vous utilisez des transactions pour lire à partir de la file d'attente et appeler l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="c3045-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="c3045-115">Selon la version de MSMQ, NetMsmqBinding prend en charge la détection limitée ou complète des messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="c3045-116">Une fois que le message a été détecté comme étant incohérent, il est ensuite traité de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="c3045-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="c3045-117">À nouveau, NetMsmqBinding prend en charge la gestion limitée à la gestion complète de messages incohérents selon la version de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c3045-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="c3045-118">Cet exemple illustre les fonctionnalités d’empoisonnement limitées fournies sur la plateforme Windows Server 2003 et Windows XP, ainsi que les fonctionnalités incohérentes complètes fournies sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c3045-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="c3045-119">Dans les deux exemples, l'objectif est de déplacer le message incohérent de la file d'attente vers une autre file qui peut ensuite être prise en charge par un service de message incohérent.</span><span class="sxs-lookup"><span data-stu-id="c3045-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="c3045-120">Exemple de gestion de message incohérent dans MSMQ v4.0</span><span class="sxs-lookup"><span data-stu-id="c3045-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="c3045-121">Dans Windows Vista, MSMQ fournit une fonctionnalité de sous-file d’attente de messages incohérents qui peut être utilisée pour stocker les messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-121">In Windows Vista, MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="c3045-122">Cet exemple illustre la meilleure pratique pour gérer les messages incohérents à l’aide de Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c3045-122">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="c3045-123">La détection de messages incohérents dans Windows Vista est très complexe.</span><span class="sxs-lookup"><span data-stu-id="c3045-123">The poison message detection in Windows Vista is quite sophisticated.</span></span> <span data-ttu-id="c3045-124">Il existe 3 propriétés qui aident à la détection.</span><span class="sxs-lookup"><span data-stu-id="c3045-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="c3045-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est nombre de fois qu'un message donné est relu à partir de la file d'attente et est distribué à l'application pour traitement.</span><span class="sxs-lookup"><span data-stu-id="c3045-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="c3045-126">Un message est relu à partir de la file d'attente lorsqu'il est remis dans celle-ci parce qu'il ne peut pas être distribué à l'application ou l'application restaure la transaction dans l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="c3045-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="c3045-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> est le nombre de fois où le message est déplacé vers la file d'attente des nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="c3045-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="c3045-128">Lorsque <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est atteint, le message est déplacé dans la file d'attente des nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="c3045-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="c3045-129">La propriété <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> correspond à l'intervalle après lequel le message est déplacé de la file d'attente des nouvelles tentatives vers la file d'attente principale.</span><span class="sxs-lookup"><span data-stu-id="c3045-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="c3045-130">La propriété <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est réinitialisée à 0.</span><span class="sxs-lookup"><span data-stu-id="c3045-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="c3045-131">Le message est réessayé.</span><span class="sxs-lookup"><span data-stu-id="c3045-131">The message is tried again.</span></span> <span data-ttu-id="c3045-132">Si toutes les tentatives de lecture du message ont échoué, le message est alors marqué comme étant incohérent.</span><span class="sxs-lookup"><span data-stu-id="c3045-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="c3045-133">Une fois que le message est marqué comme étant incohérent, il est traité en fonction des paramètres dans l'énumération <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3045-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="c3045-134">Pour rappeler les valeurs possibles :</span><span class="sxs-lookup"><span data-stu-id="c3045-134">To reiterate the possible values:</span></span>

- <span data-ttu-id="c3045-135">Fault (valeur par défaut) : provoque l'échec de l'écouteur ainsi que de l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c3045-135">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="c3045-136">Drop : permet de supprimer le message.</span><span class="sxs-lookup"><span data-stu-id="c3045-136">Drop: To drop the message.</span></span>

- <span data-ttu-id="c3045-137">Move : permet de déplacer le message vers la sous-file d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="c3045-138">Cette valeur est disponible uniquement sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c3045-138">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="c3045-139">Reject : permet de rejeter le message en le renvoyant dans la file d'attente de lettres mortes de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="c3045-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="c3045-140">Cette valeur est disponible uniquement sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c3045-140">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="c3045-141">L'exemple montre comment utiliser la disposition `Move` pour le message incohérent.</span><span class="sxs-lookup"><span data-stu-id="c3045-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="c3045-142">`Move` permet de déplacer le message vers la sous-file d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-142">`Move` causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="c3045-143">Le contrat de service est `IOrderProcessor`, qui définit un service monodirectionnel qui peut être utilisé avec des files d'attente.</span><span class="sxs-lookup"><span data-stu-id="c3045-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="c3045-144">L'opération de service affiche un message indiquant qu'elle traite la commande.</span><span class="sxs-lookup"><span data-stu-id="c3045-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="c3045-145">Pour illustrer la fonctionnalité de message incohérent, l’opération de service `SubmitPurchaseOrder` lève une exception pour restaurer la transaction sur un appel aléatoire du service.</span><span class="sxs-lookup"><span data-stu-id="c3045-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="c3045-146">Le message est alors remis dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="c3045-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="c3045-147">Le message est par la suite marqué comme étant incohérent.</span><span class="sxs-lookup"><span data-stu-id="c3045-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="c3045-148">La configuration est définie pour déplacer le message incohérent vers  la sous-file d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="c3045-149">La configuration du service inclut les propriétés de message incohérent suivantes : `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay` et `receiveErrorHandling`, comme indiqué dans le fichier de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="c3045-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="c3045-150">Traitement des messages de la file d'attente de messages incohérents</span><span class="sxs-lookup"><span data-stu-id="c3045-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="c3045-151">Le service de message incohérent lit les messages de la file d'attente finale de messages incohérents et les traite.</span><span class="sxs-lookup"><span data-stu-id="c3045-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="c3045-152">Les messages de la file d'attente de messages incohérents sont adressés au service de traitement, qui peut être différent du point de terminaison de service de message incohérent.</span><span class="sxs-lookup"><span data-stu-id="c3045-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="c3045-153">Par conséquent, lorsque le service de message incohérent lit les messages de la file d’attente, la couche de canal WCF recherche l’incompatibilité dans les points de terminaison et ne distribue pas le message.</span><span class="sxs-lookup"><span data-stu-id="c3045-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="c3045-154">Dans ce cas, le message est adressé au service de traitement des commandes mais est reçu par le service de message incohérent.</span><span class="sxs-lookup"><span data-stu-id="c3045-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="c3045-155">Pour continuer à recevoir le message même s'il est adressé à un autre point de terminaison, nous devons ajouter un `ServiceBehavior` pour filtrer les adresses où le critère de correspondance doit correspondre aux points de terminaison de service auxquels le message est adressé.</span><span class="sxs-lookup"><span data-stu-id="c3045-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="c3045-156">Cela est nécessaire pour pouvoir traiter les messages que vous lisez à partir de la file d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="c3045-157">L'implémentation du service de message incohérent elle-même est très similaire à l'implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="c3045-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="c3045-158">Elle implémente le contrat et traite les commandes.</span><span class="sxs-lookup"><span data-stu-id="c3045-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="c3045-159">L'exemple de code se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="c3045-159">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="c3045-160">Contrairement au service de traitement des commandes qui lit les messages de la file d'attente de commande, le service de message incohérent lit les messages de la sous-file d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="c3045-161">La file d'attente de messages incohérents est une sous-file d'attente de la file d'attente principale ; elle est appelée « poison » et est générée automatiquement par MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c3045-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="c3045-162">Pour y accéder, indiquez le nom de la file d'attente principale suivi de « ; » et du nom de la sous-file d'attente (dans ce cas « poison »), tel qu'indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="c3045-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="c3045-163">Dans l'exemple pour MSMQ v3.0, le nom de la file d'attente de messages incohérents n'est pas une sous-file d'attente, mais la file d'attente vers laquelle nous avons déplacé le message.</span><span class="sxs-lookup"><span data-stu-id="c3045-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="c3045-164">Lorsque vous exécutez l'exemple, les activités du client, du service et du service de message incohérent s'affichent dans les fenêtres de console.</span><span class="sxs-lookup"><span data-stu-id="c3045-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="c3045-165">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="c3045-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="c3045-166">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter les services.</span><span class="sxs-lookup"><span data-stu-id="c3045-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="c3045-167">Le service commence à s'exécuter, à traiter les commandes et à mettre fin au traitement de manière aléatoire.</span><span class="sxs-lookup"><span data-stu-id="c3045-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="c3045-168">Si le message indique qu'il a traité la commande, vous pouvez réexécuter le client afin d'envoyer un autre message jusqu'à ce que vous constatiez que le service a réellement terminé un message.</span><span class="sxs-lookup"><span data-stu-id="c3045-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="c3045-169">Selon les paramètres de gestion de message incohérent configurés, une tentative de traitement du message est effectuée avant qu'il ne soit déplacé vers la file d'attente finale de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="c3045-170">Démarrez le service de message incohérent pour lire le message incohérent de la file d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="c3045-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="c3045-171">Dans cet exemple, le service de message incohérent lit le message et le traite.</span><span class="sxs-lookup"><span data-stu-id="c3045-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="c3045-172">Vous pouvez voir que la commande fournisseur qui a été terminée et marquée comme étant incohérente est lue par le service de message incohérent.</span><span class="sxs-lookup"><span data-stu-id="c3045-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3045-173">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c3045-173">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c3045-174">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3045-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c3045-175">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="c3045-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="c3045-176">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="c3045-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="c3045-177">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c3045-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="c3045-178">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="c3045-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="c3045-179">Ouvrez Gestionnaire de serveur dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="c3045-179">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="c3045-180">Développez l’onglet **fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="c3045-180">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="c3045-181">Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="c3045-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="c3045-182">Activez la case à cocher **transactionnelle** .</span><span class="sxs-lookup"><span data-stu-id="c3045-182">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="c3045-183">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="c3045-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="c3045-184">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3045-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="c3045-185">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, modifiez les noms de file d’attente afin qu’ils reflètent le nom d’hôte réel au lieu de localhost, puis suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c3045-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="c3045-186">Avec le transport de liaison `netMsmqBinding`, la sécurité est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3045-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="c3045-187">Les propriétés `MsmqAuthenticationMode` et `MsmqProtectionLevel` déterminent toutes deux le type de sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="c3045-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="c3045-188">Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`.</span><span class="sxs-lookup"><span data-stu-id="c3045-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="c3045-189">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine.</span><span class="sxs-lookup"><span data-stu-id="c3045-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="c3045-190">Si vous exécutez cet exemple sur un ordinateur ne faisant pas partie d'un domaine, vous recevez l'erreur suivante : "Le certificat Message Queuing interne pour l'utilisateur n'existe pas."</span><span class="sxs-lookup"><span data-stu-id="c3045-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="c3045-191">Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="c3045-191">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="c3045-192">Si votre ordinateur ne fait pas partie d'un domaine, désactivez la sécurité du transport en affectant `None` au mode d'authentification et au niveau de protection, tel qu'indiqué dans l'exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="c3045-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="c3045-193">Assurez-vous que le point de terminaison est associé à la liaison en définissant l'attribut bindingConfiguration du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c3045-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="c3045-194">Assurez-vous de modifier la configuration sur PoisonMessageServer, le serveur et le client avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="c3045-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c3045-195">L'affectation de `security mode` à `None` revient à affecter `MsmqAuthenticationMode` à la sécurité `MsmqProtectionLevel`, `Message` et `None`.</span><span class="sxs-lookup"><span data-stu-id="c3045-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="c3045-196">Pour que Meta Data Exchange fonctionne, nous enregistrons une URL avec une liaison http.</span><span class="sxs-lookup"><span data-stu-id="c3045-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="c3045-197">Cela demande que le service soit exécuté dans une fenêtre de commande élevée.</span><span class="sxs-lookup"><span data-stu-id="c3045-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="c3045-198">Sinon, vous recevez une exception telle que : `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span><span class="sxs-lookup"><span data-stu-id="c3045-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c3045-199">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c3045-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c3045-200">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c3045-200">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c3045-201">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3045-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3045-202">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c3045-202">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
