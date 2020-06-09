---
title: Volatile Queued Communication
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: a9f7e8a96fd293c7f87cc19846a42a42f28de288
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602338"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="ecca6-102">Volatile Queued Communication</span><span class="sxs-lookup"><span data-stu-id="ecca6-102">Volatile Queued Communication</span></span>

<span data-ttu-id="ecca6-103">Cet exemple montre comment procéder à la communication de messages volatils mis en file d'attente sur le transport MSMQ (Message Queuing).</span><span class="sxs-lookup"><span data-stu-id="ecca6-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="ecca6-104">Il utilise <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="ecca6-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="ecca6-105">Dans le cas présent, le service est une application console auto-hébergée qui vous permet d'observer le service qui reçoit les messages mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="ecca6-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="ecca6-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ecca6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ecca6-107">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="ecca6-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="ecca6-108">Cela signifie que le client envoie ses messages à cette file d'attente.</span><span class="sxs-lookup"><span data-stu-id="ecca6-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="ecca6-109">Le service reçoit des messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="ecca6-109">The service receives messages from the queue.</span></span> <span data-ttu-id="ecca6-110">Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="ecca6-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="ecca6-111">Lorsque vous envoyez un message sans assurances, MSMQ fait seulement de son mieux pour remettre le message, contrairement aux assurances Exactly Once selon lesquelles MSMQ garantit que le message est remis ou, s'il ne peut pas être remis, vous fait savoir que le message ne peut pas être remis.</span><span class="sxs-lookup"><span data-stu-id="ecca6-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>

<span data-ttu-id="ecca6-112">Dans certains scénarios, vous pouvez envoyer un message volatil sans assurances sur une file d'attente, lorsque la remise en temps opportun est plus importante que la perte des messages.</span><span class="sxs-lookup"><span data-stu-id="ecca6-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="ecca6-113">Les messages volatils ne survivent pas aux pannes du gestionnaire de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="ecca6-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="ecca6-114">Par conséquent si le gestionnaire de files d'attente tombe en panne, la file d'attente non transactionnelle utilisée pour stocker des messages volatils survit mais pas les messages eux-mêmes car ils ne sont pas stockés sur le disque.</span><span class="sxs-lookup"><span data-stu-id="ecca6-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>

> [!NOTE]
> <span data-ttu-id="ecca6-115">Vous ne pouvez pas envoyer de messages volatils sans assurances dans l’étendue d’une transaction à l’aide de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ecca6-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="ecca6-116">Vous devez également créer une file d’attente non transactionnelle pour envoyer des messages volatils.</span><span class="sxs-lookup"><span data-stu-id="ecca6-116">You also must create a non-transactional queue to send volatile messages.</span></span>

<span data-ttu-id="ecca6-117">Le contrat de service dans cet exemple est `IStockTicker`, qui définit les services unidirectionnels les mieux adaptés à une utilisation avec mise en file d’attente.</span><span class="sxs-lookup"><span data-stu-id="ecca6-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

<span data-ttu-id="ecca6-118">L'opération de service affiche le symbole de cotation et le cours des titres boursiers, comme le montre l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="ecca6-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>

```csharp
public class StockTickerService : IStockTicker
{
    public void StockTick(string symbol, float price)
    {
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);
     }
     …
}
```

<span data-ttu-id="ecca6-119">Le service est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="ecca6-119">The service is self hosted.</span></span> <span data-ttu-id="ecca6-120">Lors de l'utilisation du transport MSMQ, la file d'attente utilisée doit être créée au préalable.</span><span class="sxs-lookup"><span data-stu-id="ecca6-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="ecca6-121">Cela peut s'effectuer manuellement ou via le code.</span><span class="sxs-lookup"><span data-stu-id="ecca6-121">This can be done manually or through code.</span></span> <span data-ttu-id="ecca6-122">Dans cet exemple, le service contient du code pour vérifier pour l'existence de la file d'attente et la créer si besoin.</span><span class="sxs-lookup"><span data-stu-id="ecca6-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="ecca6-123">Le nom de la file d'attente est lu depuis le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ecca6-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="ecca6-124">L’adresse de base est utilisée par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le proxy pour le service.</span><span class="sxs-lookup"><span data-stu-id="ecca6-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get MSMQ queue name from app settings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName);

    // Create a ServiceHost for the StockTickerService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))
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

<span data-ttu-id="ecca6-125">Le nom de la file d'attente MSMQ est spécifié dans la section appSettings du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ecca6-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="ecca6-126">Le point de terminaison pour le service est défini dans la section system.serviceModel du fichier de configuration et spécifie la liaison `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="ecca6-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>

> [!NOTE]
> <span data-ttu-id="ecca6-127">Le nom de la file d’attente comprend un point (.) pour l’ordinateur local et des barre obliques inverses dans son chemin d’accès lors de la création d’une file d’attente à l’aide de <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="ecca6-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="ecca6-128">L’adresse de point de terminaison Windows Communication Foundation (WCF) spécifie un schéma net. msmq :, utilise « localhost » pour l’ordinateur local et des barres obliques dans son chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ecca6-128">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>

<span data-ttu-id="ecca6-129">Les assurances et la durabilité ou la volatilité des messages sont également spécifiées dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="ecca6-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>

```xml
<appSettings>
  <!-- use appSetting to configure MSMQ queue name -->
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />
</appSettings>

<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"
             behaviorConfiguration="CalculatorServiceBehavior">
    ...
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                binding="netMsmqBinding"
                bindingConfiguration="volatileBinding"
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />
    ...
    </service>
  </services>

  <bindings>
    <netMsmqBinding>
      <binding name="volatileBinding"
             durable="false"
           exactlyOnce="false"/>
    </netMsmqBinding>
  </bindings>
  ...
</system.serviceModel>
```

<span data-ttu-id="ecca6-130">Étant donné que l'exemple envoie des messages mis en file d'attente en utilisant une file d'attente non transactionnelle, les messages traités ne peuvent pas être envoyés à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="ecca6-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>

```csharp
// Create a client.
Random r = new Random(137);

StockTickerClient client = new StockTickerClient();

float price = 43.23F;
for (int i = 0; i < 10; i++)
{
    float increment = 0.01f * (r.Next(10));
    client.StockTick("zzz" + i, price + increment);
}

//Closing the client gracefully cleans up resources.
client.Close();
```

<span data-ttu-id="ecca6-131">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="ecca6-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ecca6-132">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="ecca6-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ecca6-133">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="ecca6-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="ecca6-134">Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="ecca6-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="ecca6-135">Vous pouvez exécuter le client, l'arrêter, puis démarrer le service et il recevra encore ses messages.</span><span class="sxs-lookup"><span data-stu-id="ecca6-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Stock Tick zzz0:43.25
Stock Tick zzz1:43.23
Stock Tick zzz2:43.28
Stock Tick zzz3:43.3
Stock Tick zzz4:43.23
Stock Tick zzz5:43.25
Stock Tick zzz6:43.25
Stock Tick zzz7:43.24
Stock Tick zzz8:43.32
Stock Tick zzz9:43.3
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ecca6-136">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ecca6-136">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ecca6-137">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecca6-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ecca6-138">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecca6-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="ecca6-139">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ecca6-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="ecca6-140">Avec <xref:System.ServiceModel.NetMsmqBinding>, la sécurité du transport est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="ecca6-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="ecca6-141">Il existe deux propriétés pertinentes pour la sécurité de transport MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> et <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` par défaut, le mode d’authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign` .</span><span class="sxs-lookup"><span data-stu-id="ecca6-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="ecca6-142">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine et l’option d’intégration d’Active Directory doit être installée pour MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ecca6-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="ecca6-143">Si vous exécutez cet exemple sur un ordinateur qui ne satisfait pas ces critères vous recevez une erreur.</span><span class="sxs-lookup"><span data-stu-id="ecca6-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="ecca6-144">Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail ou sans intégration Active Directory</span><span class="sxs-lookup"><span data-stu-id="ecca6-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>

1. <span data-ttu-id="ecca6-145">Si votre ordinateur ne fait pas partie d'un domaine ou ne dispose pas de l'intégration Active Directory, désactivez la sécurité de transport en affectant au mode d'authentification et au niveau de protection la valeur `None` comme indiqué dans l'exemple de code de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="ecca6-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>

    ```xml
    <system.serviceModel>
        <services>
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"
                   behaviorConfiguration="StockTickerServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>

            <!-- Define NetMsmqEndpoint -->
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                      binding="netMsmqBinding"
                      bindingConfiguration="volatileBinding"
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />

          </service>
        </services>

        <bindings>
          <netMsmqBinding>
            <binding name="volatileBinding"
                  durable="false"
                  exactlyOnce="false">
              <security mode="None" />
            </binding>
          </netMsmqBinding>
        </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="StockTickerServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="ecca6-146">Assurez-vous de modifier la configuration sur le serveur et le client avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ecca6-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ecca6-147">L'affectation de `security mode` à `None` revient à affecter <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> à la sécurité <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, `Message` et `None`.</span><span class="sxs-lookup"><span data-stu-id="ecca6-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ecca6-148">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ecca6-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ecca6-149">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ecca6-149">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ecca6-150">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ecca6-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ecca6-151">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ecca6-151">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`
