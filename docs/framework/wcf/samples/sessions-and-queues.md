---
title: Sessions and Queues
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 489a8f5e782faca679991809e575e98153de95e0
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140599"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="9105f-102">Sessions and Queues</span><span class="sxs-lookup"><span data-stu-id="9105f-102">Sessions and Queues</span></span>
<span data-ttu-id="9105f-103">Cet exemple montre comment envoyer et recevoir un ensemble de messages connexes dans une communication en file d'attente sur le transport (Message Queuing ou MSMQ).</span><span class="sxs-lookup"><span data-stu-id="9105f-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="9105f-104">Cet exemple utilise la liaison `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="9105f-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="9105f-105">Le service est une application console auto-hébergée qui permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="9105f-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9105f-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9105f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9105f-107">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9105f-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9105f-108">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="9105f-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9105f-109">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="9105f-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9105f-110">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="9105f-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="9105f-111">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="9105f-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="9105f-112">Cela signifie que le client envoie ses messages à cette file d'attente.</span><span class="sxs-lookup"><span data-stu-id="9105f-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="9105f-113">Le service reçoit des messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="9105f-113">The service receives messages from the queue.</span></span> <span data-ttu-id="9105f-114">Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="9105f-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="9105f-115">Quelquefois, un client envoie un ensemble de messages connexes dans un groupe.</span><span class="sxs-lookup"><span data-stu-id="9105f-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="9105f-116">Lorsque les messages doivent être traités ensemble ou dans un ordre spécifié, une file d'attente peut être utilisée pour les regrouper, afin qu'ils soient traités par une application de réception unique.</span><span class="sxs-lookup"><span data-stu-id="9105f-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="9105f-117">Cela est particulièrement important lorsqu'il existe plusieurs applications de réception sur un groupe de serveurs et qu'il est nécessaire de garantir qu'un groupe de messages sera traité par la même application de réception.</span><span class="sxs-lookup"><span data-stu-id="9105f-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="9105f-118">Les sessions mises en file d'attente sont un mécanisme utilisé pour envoyer et recevoir un ensemble de messages connexes qui doivent être traités en une fois.</span><span class="sxs-lookup"><span data-stu-id="9105f-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="9105f-119">Les sessions mises en file d'attente requièrent qu'une transaction expose ce modèle.</span><span class="sxs-lookup"><span data-stu-id="9105f-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="9105f-120">Dans l’exemple, le client envoie plusieurs messages au service dans le cadre d’une session, dans une étendue de transaction unique.</span><span class="sxs-lookup"><span data-stu-id="9105f-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="9105f-121">Le contrat de service est `IOrderTaker`, qui définit un service monodirectionnel qui peut être utilisé avec des files d'attente.</span><span class="sxs-lookup"><span data-stu-id="9105f-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="9105f-122">Le <xref:System.ServiceModel.SessionMode> utilisé dans le contrat illustré dans l'exemple de code suivant indique que les messages font partie de la session.</span><span class="sxs-lookup"><span data-stu-id="9105f-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 <span data-ttu-id="9105f-123">Le service définit des opérations de service de manière à ce que la première opération s’inscrive dans une transaction mais ne complète pas automatiquement la transaction.</span><span class="sxs-lookup"><span data-stu-id="9105f-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="9105f-124">Les opérations suivantes s'inscrivent également dans la même transaction mais ne se complètent pas automatiquement.</span><span class="sxs-lookup"><span data-stu-id="9105f-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="9105f-125">La dernière opération de la session complète automatiquement la transaction.</span><span class="sxs-lookup"><span data-stu-id="9105f-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="9105f-126">Donc, la même transaction est utilisée pour plusieurs appels d’opération dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="9105f-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="9105f-127">Si chacune des opérations lève une exception, la transaction est restaurée et la session est remise dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="9105f-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="9105f-128">À l'achèvement réussi de la dernière opération, la transaction est validée.</span><span class="sxs-lookup"><span data-stu-id="9105f-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="9105f-129">Le service utilise `PerSession` comme <xref:System.ServiceModel.InstanceContextMode> pour recevoir tous les messages dans une session sur la même instance du service.</span><span class="sxs-lookup"><span data-stu-id="9105f-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 <span data-ttu-id="9105f-130">Le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="9105f-130">The service is self hosted.</span></span> <span data-ttu-id="9105f-131">Lors de l'utilisation du transport MSMQ, la file d'attente utilisée doit être créée au préalable.</span><span class="sxs-lookup"><span data-stu-id="9105f-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="9105f-132">Cela peut s'effectuer manuellement ou via le code.</span><span class="sxs-lookup"><span data-stu-id="9105f-132">This can be done manually or through code.</span></span> <span data-ttu-id="9105f-133">Dans cet exemple, le service contient le code <xref:System.Messaging> pour vérifier l'existence de la file d'attente et la crée si besoin.</span><span class="sxs-lookup"><span data-stu-id="9105f-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="9105f-134">Le nom de la file d'attente est lu depuis le fichier de configuration à l'aide de la classe <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="9105f-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();
    }  
}  
```

 <span data-ttu-id="9105f-135">Le nom de la file d'attente MSMQ est spécifié dans la section appSettings de ce fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="9105f-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="9105f-136">Le point de terminaison pour le service est défini dans la section system.serviceModel du fichier de configuration et spécifie la liaison `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="9105f-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9105f-137">Le client crée une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="9105f-137">The client creates a transaction scope.</span></span> <span data-ttu-id="9105f-138">Tous les messages dans la session sont envoyés à la file d’attente dans l’étendue de transaction, traitée comme une unité atomique dans laquelle tous les messages réussissent ou échouent.</span><span class="sxs-lookup"><span data-stu-id="9105f-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="9105f-139">La transaction est validée en appelant <xref:System.Transactions.TransactionScope.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="9105f-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> <span data-ttu-id="9105f-140">Vous pouvez utiliser une seule transaction pour tous les messages dans la session et tous les messages dans la session doit être envoyés avant de valider la transaction.</span><span class="sxs-lookup"><span data-stu-id="9105f-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="9105f-141">La fermeture du client entraîne la fermeture de la session.</span><span class="sxs-lookup"><span data-stu-id="9105f-141">Closing the client closes the session.</span></span> <span data-ttu-id="9105f-142">Par conséquent, le client doit être fermé avant que la transaction soit terminée pour envoyer tous les messages dans la session à la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="9105f-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="9105f-143">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="9105f-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9105f-144">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="9105f-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="9105f-145">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="9105f-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="9105f-146">Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="9105f-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="9105f-147">Vous pouvez exécuter le client, l'arrêter, puis démarrer le service et il recevra encore ses messages.</span><span class="sxs-lookup"><span data-stu-id="9105f-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="9105f-148">Sur le client.</span><span class="sxs-lookup"><span data-stu-id="9105f-148">On the client.</span></span>  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="9105f-149">Sur le service.</span><span class="sxs-lookup"><span data-stu-id="9105f-149">On the service.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9105f-150">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="9105f-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9105f-151">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9105f-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9105f-152">Pour générer l’édition C#, C++ ou Visual Basic .NET de la solution, suivez les instructions de la [création des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9105f-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9105f-153">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9105f-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="9105f-154">Avec <xref:System.ServiceModel.NetMsmqBinding>, la sécurité du transport est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="9105f-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="9105f-155">Il existe deux propriétés pertinentes pour la sécurité de transport MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` à savoir, et par défaut, le mode `Windows` d’authentification a la valeur et le `Sign`niveau de protection a la valeur.</span><span class="sxs-lookup"><span data-stu-id="9105f-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="9105f-156">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine et l’option d’intégration d’Active Directory doit être installée pour MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9105f-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="9105f-157">Si vous exécutez cet exemple sur un ordinateur qui ne satisfait pas ces critères vous recevez une erreur.</span><span class="sxs-lookup"><span data-stu-id="9105f-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="9105f-158">Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail ou sans intégration Active Directory</span><span class="sxs-lookup"><span data-stu-id="9105f-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="9105f-159">Si votre ordinateur ne fait pas partie d'un domaine ou ne dispose pas de l'intégration Active Directory, désactivez la sécurité de transport en affectant au mode d'authentification et niveau de protection la valeur `None` comme indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="9105f-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="9105f-160">Assurez-vous de modifier la configuration sur le serveur et le client avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="9105f-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9105f-161">L'affectation de `None` au mode de sécurité revient à affecter <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> à la sécurité <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, `Message` et `None`.</span><span class="sxs-lookup"><span data-stu-id="9105f-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
