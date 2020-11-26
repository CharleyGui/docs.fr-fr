---
title: Custom Binding Imperative
ms.date: 03/30/2017
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
ms.openlocfilehash: 6be5105831fa3845db9a55a14a7ed8821dc1cbc4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241913"
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="5ea79-102">Custom Binding Imperative</span><span class="sxs-lookup"><span data-stu-id="5ea79-102">Custom Binding Imperative</span></span>

<span data-ttu-id="5ea79-103">L’exemple montre comment écrire du code impératif pour définir et utiliser des liaisons personnalisées sans utiliser un fichier de configuration ou un client Windows Communication Foundation (WCF) généré.</span><span class="sxs-lookup"><span data-stu-id="5ea79-103">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a Windows Communication Foundation (WCF) generated client.</span></span> <span data-ttu-id="5ea79-104">Il combine les fonctionnalités fournies par le transport HTTP et le canal de session fiable pour créer une liaison HTTP fiable.</span><span class="sxs-lookup"><span data-stu-id="5ea79-104">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="5ea79-105">Cet exemple est basé sur le [prise en main](getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="5ea79-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ea79-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="5ea79-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5ea79-107">Sur le client et le service, une liaison personnalisée est créée et contient deux éléments de liaison (Reliable Session et HTTP) :</span><span class="sxs-lookup"><span data-stu-id="5ea79-107">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="5ea79-108">Sur le service, la liaison est utilisée en ajoutant un point de terminaison à ServiceHost :</span><span class="sxs-lookup"><span data-stu-id="5ea79-108">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="5ea79-109">Sur le client, la liaison est utilisée par <xref:System.ServiceModel.ChannelFactory> pour créer un canal au service :</span><span class="sxs-lookup"><span data-stu-id="5ea79-109">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="5ea79-110">Ce canal permet ensuite d'interagir avec le service :</span><span class="sxs-lookup"><span data-stu-id="5ea79-110">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="5ea79-111">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="5ea79-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5ea79-112">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="5ea79-112">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5ea79-113">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5ea79-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5ea79-114">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ea79-114">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5ea79-115">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ea79-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5ea79-116">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ea79-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5ea79-117">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5ea79-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5ea79-118">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5ea79-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5ea79-119">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5ea79-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ea79-120">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5ea79-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="5ea79-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ea79-121">See also</span></span>

- [<span data-ttu-id="5ea79-122">Exemples de liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="5ea79-122">Custom Binding Samples</span></span>](custom-binding.md)
