---
title: Dead Letter Queues
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 5025aa784817d1189f23918eacfef275abf968e1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921436"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="1cdaf-102">Dead Letter Queues</span><span class="sxs-lookup"><span data-stu-id="1cdaf-102">Dead Letter Queues</span></span>
<span data-ttu-id="1cdaf-103">Cet exemple montre comment gérer et traiter des messages n'ayant pas pu être remis.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="1cdaf-104">Il est basé sur l’exemple de [liaison MSMQ transactionnelle](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="1cdaf-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="1cdaf-105">Cet exemple utilise la liaison `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="1cdaf-106">Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="1cdaf-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="1cdaf-108">Cet exemple illustre la file d’attente de lettres mortes d’une application qui est uniquement disponible sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-108">This sample demonstrates each application dead letter queue that is only available on Windows Vista.</span></span> <span data-ttu-id="1cdaf-109">L’exemple peut être modifié pour utiliser les files d’attente par défaut à l’ensemble du système pour MSMQ 3,0 sur Windows Server 2003 et Windows XP.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on Windows Server 2003 and Windows XP.</span></span>

 <span data-ttu-id="1cdaf-110">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="1cdaf-111">Cela signifie que le client envoie ses messages à cette file d'attente.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="1cdaf-112">Le service reçoit des messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-112">The service receives messages from the queue.</span></span> <span data-ttu-id="1cdaf-113">Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="1cdaf-114">Parce que la communication en file d'attente peut impliquer une certaine latence, vous pouvez associer une valeur de durée de vie au message afin de garantir que le message n'est pas remis à l'application une fois le délai passé.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="1cdaf-115">Il existe également des cas où une application doit être informée en cas d'échec de remise du message.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="1cdaf-116">Dans tous ces cas, comme lorsque la durée de vie du message a expiré ou que le message n'a pas été remis, il est mis dans une file d'attente de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="1cdaf-117">L’application émettrice peut lire ensuite les messages dans la file d’attente de lettres mortes et effectuer des actions correctives qui varient d’aucune action à la correction des raisons pour remise non réussie et au renvoi du message.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="1cdaf-118">La file d’attente de lettres mortes dans la liaison `NetMsmqBinding` est exprimée dans les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="1cdaf-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="1cdaf-119">La propriété <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> permet d'exprimer le type de file d'attente de lettres mortes requis par le client.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="1cdaf-120">L'énumération a les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="1cdaf-120">This enumeration has the following values:</span></span>

- <span data-ttu-id="1cdaf-121">`None` : aucune file d'attente de lettres mortes n'est requise par le client.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-121">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="1cdaf-122">`System`  la file d'attente de lettres mortes du système est utilisée pour stocker les lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="1cdaf-123">La file d'attente de lettres mortes du système est partagée par toutes les applications exécutées sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="1cdaf-124">`Custom` : une file d'attente de lettres mortes personnalisée spécifiée à l'aide de la propriété <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> est utilisée pour stocker des messages morts.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="1cdaf-125">Cette fonctionnalité est disponible uniquement sur Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-125">This feature is only available on Windows Vista.</span></span> <span data-ttu-id="1cdaf-126">Elle est utilisée lorsque l'application doit utiliser sa propre file d'attente de lettres mortes au lieu de la partager avec d'autres applications exécutées sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="1cdaf-127">La propriété <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> permet d'exprimer la file d'attente spécifique à utiliser comme file d'attente de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="1cdaf-128">Disponible uniquement dans Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-128">This is available only in Windows Vista.</span></span>

 <span data-ttu-id="1cdaf-129">Dans cet exemple, le client envoie un lot de messages au service à partir de l’étendue d’une transaction et indique un valeur arbitraire faible de durée de vie pour ces messages (approximativement 2 secondes).</span><span class="sxs-lookup"><span data-stu-id="1cdaf-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="1cdaf-130">Le client indique également la file d'attente de lettres mortes personnalisée à utiliser pour mettre les messages qui ont expiré en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="1cdaf-131">L'application cliente peut lire les messages dans la file d'attente de lettres mortes. Elle tente ensuite de renvoyer le message ou de corriger l'erreur qui a provoqué la mise en file d'attente de lettres mortes du message et de renvoyer le message.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="1cdaf-132">Dans l'exemple, le client affiche un message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="1cdaf-133">Le contrat de service est `IOrderProcessor`, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="1cdaf-134">Le code de service dans l’exemple est celui de la [liaison MSMQ traitée](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="1cdaf-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="1cdaf-135">La communication avec le service a lieu dans l'étendue d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="1cdaf-136">Le service lit des messages à partir de la file d'attente, effectue l'opération puis affiche les résultats de cette dernière.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="1cdaf-137">L'application crée également une file d'attente de lettres mortes pour les messages de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

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

 <span data-ttu-id="1cdaf-138">La configuration du client spécifie une durée courte pour que le message atteigne le service.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="1cdaf-139">Si le message n'est pas transmis dans la durée définie, il expire et est déplacé vers la file d'attente de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="1cdaf-140">Le client a la possibilité de remettre le message à la file d'attente du service dans le délai spécifié.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="1cdaf-141">Pour être sûr de voir le service de lettres mortes en action, vous devez exécuter le client avant de démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="1cdaf-142">Le message expire et est remis au service de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="1cdaf-143">L'application doit définir la file d'attente à utiliser comme file d'attente de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="1cdaf-144">Si aucune file d’attente n’est spécifiée, la file d’attente de lettres mortes transactionnelle du système par défaut est utilisée pour mettre en file d’attente les messages morts.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="1cdaf-145">Dans cet exemple, l'application cliente spécifie sa propre file d'attente de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

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

 <span data-ttu-id="1cdaf-146">Le service de lettres mortes lit les messages à partir de la file d'attente de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="1cdaf-147">Le service de message de lettres mortes implémente le contrat `IOrderProcessor`.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="1cdaf-148">Toutefois, son implémentation n'est pas de traiter les commandes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="1cdaf-149">Le service de message de lettres mortes est un service client et n'a pas la fonctionnalité de traitement de commandes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="1cdaf-150">La file d'attente de lettres mortes est une file d'attente cliente et est locale sur le gestionnaire de files d'attente client.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="1cdaf-151">L'implémentation du service de lettres mortes vérifie le motif d'échec de remise d'un message et prend les mesures adéquates.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="1cdaf-152">Le motif d'échec de remise d'un message est capturé dans les deux énumérations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> et <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="1cdaf-153">Vous pouvez récupérer <xref:System.ServiceModel.Channels.MsmqMessageProperty> dans <xref:System.ServiceModel.OperationContext> comme illustré dans l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="1cdaf-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

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

 <span data-ttu-id="1cdaf-154">Les messages dans la file d'attente de lettres mortes sont des messages adressés au service qui est le traite le message.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="1cdaf-155">Par conséquent, lorsque le service de message de lettres mortes lit des messages à partir de la file d’attente, la couche de canal Windows Communication Foundation (WCF) recherche l’incompatibilité dans les points de terminaison et ne distribue pas le message.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="1cdaf-156">Dans ce cas, le message est adressé au service de traitement des commandes mais est reçu par le service de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="1cdaf-157">Pour recevoir un message adressé à un point de terminaison différent, un filtre d'adresse pouvant correspondre à n'importe quelle adresse est spécifié dans `ServiceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="1cdaf-158">Cela est requis pour traiter correctement les messages lus à partir de la file d'attente de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="1cdaf-159">Dans cet exemple, le service de message de lettres mortes renvoie le message si la raison de l’échec est que le message a expiré. Pour toutes les autres raisons, il affiche l’échec de la remise, comme indiqué dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="1cdaf-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="1cdaf-160">L'exemple suivant affiche la configuration pour un message de lettres mortes :</span><span class="sxs-lookup"><span data-stu-id="1cdaf-160">The following sample shows the configuration for a dead-letter message:</span></span>

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

 <span data-ttu-id="1cdaf-161">Lors de l'exécution de l'exemple, vous devez exécuter 3 fichiers exécutables pour voir comment la file d'attente de lettres mortes fonctionne pour chaque application : le client, le service et un service de lettres mortes qui lit les messages de la file d'attente de lettres mortes pour chaque application et renvoie le message au service.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="1cdaf-162">Ce sont toutes des applications console avec la sortie dans les fenêtres de console.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="1cdaf-163">En raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="1cdaf-164">Vous pouvez exécuter le client, l'arrêter, puis démarrer le service et il recevra encore ses messages.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="1cdaf-165">Vous devez démarrer le service et le fermer pour que la file d'attente soit créée.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="1cdaf-166">Lorsque le client est exécuté, il affiche le message :</span><span class="sxs-lookup"><span data-stu-id="1cdaf-166">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="1cdaf-167">Le client a essayé d'envoyer le message mais avec un délai d'attente court, le message a expiré et est maintenant mis dans la file d'attente de lettres mortes pour chaque application.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="1cdaf-168">Vous exécutez alors le service de lettres mortes qui lit le message, affiche le code d'erreur et renvoie le message au service.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

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

 <span data-ttu-id="1cdaf-169">Le service démarre puis lit le message renvoyé et le traite.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-169">The service starts and then reads the resent message and processes it.</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1cdaf-170">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="1cdaf-170">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="1cdaf-171">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cdaf-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1cdaf-172">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="1cdaf-173">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="1cdaf-174">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="1cdaf-175">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="1cdaf-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="1cdaf-176">Ouvrez Gestionnaire de serveur dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-176">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="1cdaf-177">Développez l’onglet **fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="1cdaf-177">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="1cdaf-178">Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="1cdaf-179">Activez la case à cocher **transactionnelle** .</span><span class="sxs-lookup"><span data-stu-id="1cdaf-179">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="1cdaf-180">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="1cdaf-181">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cdaf-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="1cdaf-182">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, modifiez les noms de file d’attente de manière appropriée, en remplaçant localhost par le nom complet de l’ordinateur et suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cdaf-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="1cdaf-183">Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="1cdaf-183">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="1cdaf-184">Si votre ordinateur ne fait pas partie d'un domaine, désactivez la sécurité du transport en affectant `None` au mode d'authentification et au niveau de protection, tel qu'indiqué dans l'exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="1cdaf-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="1cdaf-185">Assurez-vous que le point de terminaison est associé à la liaison en définissant l’attribut `bindingConfiguration` du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="1cdaf-186">Assurez-vous de modifier la configuration sur DeadLetterService, le serveur et le client avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1cdaf-187">L'affectation de `security mode` à `None` revient à affecter `MsmqAuthenticationMode` aux modes de sécurité `MsmqProtectionLevel`, `Message` et `None`.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="1cdaf-188">Comments</span><span class="sxs-lookup"><span data-stu-id="1cdaf-188">Comments</span></span>
 <span data-ttu-id="1cdaf-189">Avec le transport de liaison `netMsmqBinding`, la sécurité est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="1cdaf-190">Les propriétés `MsmqAuthenticationMode` et `MsmqProtectionLevel` déterminent toutes deux le type de sécurité du transport.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="1cdaf-191">Par défaut, le mode d'authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="1cdaf-192">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="1cdaf-193">Si vous exécutez cet exemple sur un ordinateur ne faisant pas partie d'un domaine, vous recevez l'erreur suivante : "Le certificat Message Queuing interne pour l'utilisateur n'existe pas."</span><span class="sxs-lookup"><span data-stu-id="1cdaf-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1cdaf-194">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1cdaf-195">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-195">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1cdaf-196">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cdaf-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1cdaf-197">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="1cdaf-197">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
