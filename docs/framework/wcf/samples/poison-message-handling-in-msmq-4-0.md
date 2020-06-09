---
title: Poison Message Handling in MSMQ 4,0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 54e69d60aabb3793ef4a8d800dd0e6238c28f231
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602438"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="f9fe0-102">Poison Message Handling in MSMQ 4,0</span><span class="sxs-lookup"><span data-stu-id="f9fe0-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="f9fe0-103">Cet exemple montre comment assurer la gestion des messages incohérents dans un service.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="f9fe0-104">Cet exemple est basé sur l’exemple de [liaison MSMQ transactionnelle](transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="f9fe0-104">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="f9fe0-105">Cet exemple utilise `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="f9fe0-106">Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="f9fe0-107">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f9fe0-108">Cela signifie que le client envoie ses messages à cette file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f9fe0-109">Le service reçoit des messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-109">The service receives messages from the queue.</span></span> <span data-ttu-id="f9fe0-110">Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="f9fe0-111">Un message incohérent est un message qui est lu à plusieurs reprises à partir d’une file d’attente lorsque le service qui le lit ne parvient pas à le traiter et met donc fin à la transaction sous laquelle le message est lu.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="f9fe0-112">Dans ce cas, le message est de nouveau réessayé.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="f9fe0-113">Cela peut théoriquement continuer indéfiniment en cas de problème avec le message.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="f9fe0-114">Cela peut se produire uniquement lorsque vous utilisez des transactions pour lire à partir de la file d’attente et appeler l’opération de service.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-114">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="f9fe0-115">Selon la version de MSMQ, NetMsmqBinding prend en charge la détection limitée ou complète des messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="f9fe0-116">Une fois que le message a été détecté comme étant incohérent, il est ensuite traité de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="f9fe0-117">À nouveau, NetMsmqBinding prend en charge la gestion limitée à la gestion complète de messages incohérents selon la version de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="f9fe0-118">Cet exemple illustre les fonctionnalités d’empoisonnement limitées fournies sur la plateforme Windows Server 2003 et Windows XP, ainsi que les fonctionnalités incohérentes complètes fournies sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="f9fe0-119">Dans les deux exemples, l’objectif est de déplacer le message incohérent hors de la file d’attente vers une autre file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-119">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="f9fe0-120">Cette file d’attente peut ensuite être desservie par un service de message incohérent.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-120">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="f9fe0-121">Exemple de gestion de message incohérent dans MSMQ v4.0</span><span class="sxs-lookup"><span data-stu-id="f9fe0-121">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="f9fe0-122">Dans Windows Vista, MSMQ offre une sous-file d’attente de messages incohérents qui peut être utilisée pour stocker les messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-122">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="f9fe0-123">Cet exemple illustre la meilleure pratique pour gérer les messages incohérents à l’aide de Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-123">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="f9fe0-124">La détection de messages incohérents dans Windows Vista est sophistiquée.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-124">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="f9fe0-125">Il existe 3 propriétés qui aident à la détection.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-125">There are 3 properties that help with detection.</span></span> <span data-ttu-id="f9fe0-126"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est nombre de fois qu'un message donné est relu à partir de la file d'attente et est distribué à l'application pour traitement.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-126">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="f9fe0-127">Un message est relu à partir de la file d'attente lorsqu'il est remis dans celle-ci parce qu'il ne peut pas être distribué à l'application ou l'application restaure la transaction dans l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-127">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="f9fe0-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> est le nombre de fois où le message est déplacé vers la file d'attente des nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="f9fe0-129">Lorsque <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est atteint, le message est déplacé dans la file d'attente des nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-129">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="f9fe0-130">La propriété <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> correspond à l'intervalle après lequel le message est déplacé de la file d'attente des nouvelles tentatives vers la file d'attente principale.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-130">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="f9fe0-131">La propriété <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> est réinitialisée à 0.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-131">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="f9fe0-132">Le message est réessayé.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-132">The message is tried again.</span></span> <span data-ttu-id="f9fe0-133">Si toutes les tentatives de lecture du message ont échoué, le message est alors marqué comme étant incohérent.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-133">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="f9fe0-134">Une fois que le message est marqué comme étant incohérent, il est traité en fonction des paramètres dans l'énumération <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-134">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="f9fe0-135">Pour rappeler les valeurs possibles :</span><span class="sxs-lookup"><span data-stu-id="f9fe0-135">To reiterate the possible values:</span></span>

- <span data-ttu-id="f9fe0-136">Fault (valeur par défaut) : provoque l'échec de l'écouteur ainsi que de l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-136">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="f9fe0-137">Drop : permet de supprimer le message.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-137">Drop: To drop the message.</span></span>

- <span data-ttu-id="f9fe0-138">Move : déplace le message vers la sous-file d’attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-138">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="f9fe0-139">Cette valeur est disponible uniquement sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-139">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="f9fe0-140">Reject : permet de rejeter le message en le renvoyant dans la file d'attente de lettres mortes de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-140">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="f9fe0-141">Cette valeur est disponible uniquement sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-141">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="f9fe0-142">L'exemple montre comment utiliser la disposition `Move` pour le message incohérent.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-142">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="f9fe0-143">`Move`provoque le déplacement du message vers la sous-file d’attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-143">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="f9fe0-144">Le contrat de service est `IOrderProcessor`, qui définit un service monodirectionnel qui peut être utilisé avec des files d'attente.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-144">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="f9fe0-145">L'opération de service affiche un message indiquant qu'elle traite la commande.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-145">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="f9fe0-146">Pour illustrer la fonctionnalité de message incohérent, l' `SubmitPurchaseOrder` opération de service lève une exception pour restaurer la transaction sur un appel aléatoire du service.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-146">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="f9fe0-147">Le message est alors remis dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-147">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="f9fe0-148">Le message est par la suite marqué comme étant incohérent.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-148">Eventually the message is marked as poison.</span></span> <span data-ttu-id="f9fe0-149">La configuration est configurée pour déplacer le message incohérent vers la sous-file d’attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-149">The configuration is set to move the poison message to the poison subqueue.</span></span>

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

 <span data-ttu-id="f9fe0-150">La configuration du service inclut les propriétés de message incohérent suivantes : `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay` et `receiveErrorHandling`, comme indiqué dans le fichier de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-150">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="f9fe0-151">Traitement des messages de la file d'attente de messages incohérents</span><span class="sxs-lookup"><span data-stu-id="f9fe0-151">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="f9fe0-152">Le service de message incohérent lit les messages de la file d'attente finale de messages incohérents et les traite.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-152">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="f9fe0-153">Les messages de la file d'attente de messages incohérents sont adressés au service de traitement, qui peut être différent du point de terminaison de service de message incohérent.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-153">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="f9fe0-154">Par conséquent, lorsque le service de message incohérent lit les messages de la file d’attente, la couche de canal WCF recherche l’incompatibilité dans les points de terminaison et ne distribue pas le message.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-154">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="f9fe0-155">Dans ce cas, le message est adressé au service de traitement des commandes mais est reçu par le service de message incohérent.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-155">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="f9fe0-156">Pour continuer à recevoir le message même s'il est adressé à un autre point de terminaison, nous devons ajouter un `ServiceBehavior` pour filtrer les adresses où le critère de correspondance doit correspondre aux points de terminaison de service auxquels le message est adressé.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-156">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="f9fe0-157">Cela est nécessaire pour pouvoir traiter les messages que vous lisez à partir de la file d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-157">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="f9fe0-158">L'implémentation du service de message incohérent elle-même est très similaire à l'implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-158">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="f9fe0-159">Elle implémente le contrat et traite les commandes.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-159">It implements the contract and processes the orders.</span></span> <span data-ttu-id="f9fe0-160">L'exemple de code se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="f9fe0-160">The code example is as follows.</span></span>

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

 <span data-ttu-id="f9fe0-161">Contrairement au service de traitement des commandes qui lit les messages de la file d’attente de commandes, le service de message incohérent lit les messages à partir de la sous-file d’attente empoisonnée.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-161">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="f9fe0-162">La file d’attente de messages incohérents est une sous-file d’attente de la file d’attente principale, appelée « incohérent » et générée automatiquement par MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-162">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="f9fe0-163">Pour y accéder, indiquez le nom de la file d’attente principale suivi par un « ; » et le nom de la sous-file d’attente, dans ce cas « poison », comme indiqué dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-163">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f9fe0-164">Dans l'exemple pour MSMQ v3.0, le nom de la file d'attente de messages incohérents n'est pas une sous-file d'attente, mais la file d'attente vers laquelle nous avons déplacé le message.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-164">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="f9fe0-165">Lorsque vous exécutez l'exemple, les activités du client, du service et du service de message incohérent s'affichent dans les fenêtres de console.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-165">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="f9fe0-166">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-166">You can see the service receive messages from the client.</span></span> <span data-ttu-id="f9fe0-167">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter les services.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-167">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="f9fe0-168">Le service commence à s'exécuter, à traiter les commandes et à mettre fin au traitement de manière aléatoire.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-168">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="f9fe0-169">Si le message indique qu'il a traité la commande, vous pouvez réexécuter le client afin d'envoyer un autre message jusqu'à ce que vous constatiez que le service a réellement terminé un message.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-169">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="f9fe0-170">Selon les paramètres de gestion de message incohérent configurés, une tentative de traitement du message est effectuée avant qu'il ne soit déplacé vers la file d'attente finale de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-170">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

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

 <span data-ttu-id="f9fe0-171">Démarrez le service de message incohérent pour lire le message incohérent de la file d'attente de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-171">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="f9fe0-172">Dans cet exemple, le service de message incohérent lit le message et le traite.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-172">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="f9fe0-173">Vous pouvez voir que la commande fournisseur qui a été terminée et marquée comme étant incohérente est lue par le service de message incohérent.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-173">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f9fe0-174">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f9fe0-174">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f9fe0-175">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f9fe0-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f9fe0-176">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-176">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f9fe0-177">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-177">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f9fe0-178">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-178">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f9fe0-179">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="f9fe0-179">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f9fe0-180">Ouvrez Gestionnaire de serveur dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-180">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f9fe0-181">Développez l’onglet **fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="f9fe0-181">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f9fe0-182">Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-182">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="f9fe0-183">Activez la case à cocher **transactionnelle** .</span><span class="sxs-lookup"><span data-stu-id="f9fe0-183">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f9fe0-184">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-184">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f9fe0-185">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f9fe0-185">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="f9fe0-186">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, modifiez les noms de file d’attente afin qu’ils reflètent le nom d’hôte réel au lieu de localhost, puis suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f9fe0-186">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

 <span data-ttu-id="f9fe0-187">Avec le transport de liaison `netMsmqBinding`, la sécurité est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-187">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="f9fe0-188">Les propriétés `MsmqAuthenticationMode` et `MsmqProtectionLevel` déterminent toutes deux le type de sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-188">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="f9fe0-189">Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-189">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="f9fe0-190">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-190">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="f9fe0-191">Si vous exécutez cet exemple sur un ordinateur ne faisant pas partie d'un domaine, vous recevez l'erreur suivante : "Le certificat Message Queuing interne pour l'utilisateur n'existe pas."</span><span class="sxs-lookup"><span data-stu-id="f9fe0-191">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="f9fe0-192">Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="f9fe0-192">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="f9fe0-193">Si votre ordinateur ne fait pas partie d'un domaine, désactivez la sécurité du transport en affectant `None` au mode d'authentification et au niveau de protection, tel qu'indiqué dans l'exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="f9fe0-193">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="f9fe0-194">Assurez-vous que le point de terminaison est associé à la liaison en définissant l'attribut bindingConfiguration du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-194">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="f9fe0-195">Avant d’exécuter l’exemple, assurez-vous de modifier la configuration sur PoisonMessageServer, sur le serveur et sur le client.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-195">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f9fe0-196">L'affectation de `security mode` à `None` revient à affecter `MsmqAuthenticationMode` à la sécurité `MsmqProtectionLevel`, `Message` et `None`.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-196">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="f9fe0-197">Pour que Meta Data Exchange fonctionne, nous enregistrons une URL avec une liaison http.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-197">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="f9fe0-198">Cela demande que le service soit exécuté dans une fenêtre de commande élevée.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-198">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="f9fe0-199">Dans le cas contraire, vous recevez une exception telle que : `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied` .</span><span class="sxs-lookup"><span data-stu-id="f9fe0-199">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f9fe0-200">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f9fe0-201">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f9fe0-202">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f9fe0-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f9fe0-203">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f9fe0-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
