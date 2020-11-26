---
title: Net.TCP Port Sharing, exemple
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: fa62734ed6a4a016011c9f29b3665dae05a000c6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235374"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="7ff9c-102">Net.TCP Port Sharing, exemple</span><span class="sxs-lookup"><span data-stu-id="7ff9c-102">Net.TCP Port Sharing Sample</span></span>

<span data-ttu-id="7ff9c-103">Le protocole TCP/IP utilise un numéro à 16 bits, appelé un port, pour différencier des connexions vers des applications réseau multiples qui s'exécutent sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="7ff9c-104">Si une application écoute un port, tout le trafic TCP de ce port va à cette application.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="7ff9c-105">Les autres applications ne peuvent pas écouter en même temps ce port.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7ff9c-106">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7ff9c-107">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7ff9c-108">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7ff9c-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7ff9c-109">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="7ff9c-110">De nombreux protocoles utilisent un numéro de port standard ou par défaut.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="7ff9c-111">Par exemple, le protocole HTTP utilise en général le port TCP 80.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="7ff9c-112">Internet Information Services (IIS) a un écouteur qui partage un port entre plusieurs applications HTTP.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="7ff9c-113">IIS écoute directement le port et envoie les messages à l'application appropriée en fonction des informations du flux de messages.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="7ff9c-114">Cela permet à plusieurs applications HTTP d'utiliser le même numéro de port sans devoir rivaliser pour réserver le port pour recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="7ff9c-115">Le partage de ports NetTcp est une fonctionnalité de Windows Communication Foundation (WCF) qui permet de la même manière à plusieurs applications réseau de partager un port unique.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="7ff9c-116">Le service de partage de ports NetTcp accepte les connexions utilisant le protocole net.tcp et transfère les messages en fonction de leur adresse de destination.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="7ff9c-117">Le service de partage de ports NetTcp n'est pas activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="7ff9c-118">Avant d'exécuter cet exemple, vous devez activer le service manuellement.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="7ff9c-119">Pour plus d’informations, consultez [Comment : activer le service de partage de ports net. TCP](../feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="7ff9c-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="7ff9c-120">Si le service est désactivé, une exception est levée lorsque l'application serveur est démarrée.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="7ff9c-121">Le partage de ports est activé sur le serveur en définissant la propriété <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> de la liaison <xref:System.ServiceModel.NetTcpBinding> ou de l'élément de liaison <xref:System.ServiceModel.Channels.TcpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="7ff9c-122">Le client n'a pas besoin de savoir comment le partage de ports a été configuré pour l'utiliser sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="7ff9c-123">Activation du partage de ports</span><span class="sxs-lookup"><span data-stu-id="7ff9c-123">Enabling Port Sharing</span></span>  

 <span data-ttu-id="7ff9c-124">Le code suivant illustre l'activation du partage de ports sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="7ff9c-125">Il démarre une instance du service `ICalculator` sur un port fixe avec un chemin d’accès URI aléatoire.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="7ff9c-126">Bien que deux services puissent partager le même port, leurs adresses de point de terminaison globales doivent demeurer uniques afin que le service de partage de ports NetTcp puisse router les messages vers l'application qui convient.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 <span data-ttu-id="7ff9c-127">Avec le partage de ports activé, vous pouvez exécuter plusieurs fois le service sans conflit de numéro de port.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="7ff9c-128">Si vous modifiez le code pour désactiver le partage de ports, le fait de démarrer deux copies des résultats du service fait échouer la seconde avec une <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="7ff9c-129">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="7ff9c-129">Running the Sample</span></span>  

 <span data-ttu-id="7ff9c-130">Vous pouvez utiliser le client test pour vérifier que les messages sont correctement routés aux services qui partagent le port.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 <span data-ttu-id="7ff9c-131">Chaque instance du service imprime son nombre et adresse uniques.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="7ff9c-132">Par exemple, vous pouvez voir le texte suivant lorsque vous exécutez service.exe.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="7ff9c-133">Entrez le numéro de service que vous voyez lorsque vous exécutez client.exe.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7ff9c-134">Cet exemple peut être exécuté dans une configuration à plusieurs ordinateurs en modifiant l'adresse générée que le client utilise.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="7ff9c-135">Dans Client.cs, modifiez la chaîne de mise en forme de l'adresse du point de terminaison pour la faire correspondre à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="7ff9c-136">Remplacez toute référence au « localhost » par l'adresse IP de l'ordinateur serveur.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="7ff9c-137">Vous devez recompiler l'exemple après avoir apporté cette modification.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7ff9c-138">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="7ff9c-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7ff9c-139">Installez ASP.NET 4,0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-139">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="7ff9c-140">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7ff9c-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="7ff9c-141">Activez le service de partage de ports NetTcp comme décrit précédemment dans la section d'introduction.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4. <span data-ttu-id="7ff9c-142">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7ff9c-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="7ff9c-143">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7ff9c-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="7ff9c-144">Les détails d'exécution spécifiques de cet exemple sont inclus dans la section Exécution de l'exemple ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7ff9c-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
