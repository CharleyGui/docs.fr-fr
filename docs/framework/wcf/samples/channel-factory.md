---
title: Fabrique de canaux
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 2aa44c4ef274fa548d490b0d8a648457a7b1e03b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600657"
---
# <a name="channel-factory"></a><span data-ttu-id="8e92e-102">Fabrique de canaux</span><span class="sxs-lookup"><span data-stu-id="8e92e-102">Channel Factory</span></span>

<span data-ttu-id="8e92e-103">Cet exemple montre comment une application cliente peut créer un canal avec la classe <xref:System.ServiceModel.ChannelFactory> au lieu d'un client généré.</span><span class="sxs-lookup"><span data-stu-id="8e92e-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="8e92e-104">Cet exemple est basé sur le [prise en main](getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="8e92e-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="8e92e-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8e92e-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="8e92e-106">Cet exemple utilise la classe <xref:System.ServiceModel.ChannelFactory%601> pour créer un canal à un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="8e92e-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="8e92e-107">En général, pour créer un canal vers un point de terminaison de service, vous générez un type de client avec l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) et créez une instance du type généré.</span><span class="sxs-lookup"><span data-stu-id="8e92e-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="8e92e-108">Vous pouvez également créer un canal en utilisant la classe <xref:System.ServiceModel.ChannelFactory%601>, comme le montre cet exemple.</span><span class="sxs-lookup"><span data-stu-id="8e92e-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="8e92e-109">Le service créé par l’exemple de code suivant est identique au service dans le [prise en main](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8e92e-109">The service created by the following sample code is identical to the service in the [Getting Started](getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="8e92e-110">Si vous exécutez cet exemple dans un scénario à plusieurs ordinateurs, vous devez remplacer « localhost » dans le code précédent par le nom qualifié complet de l'ordinateur qui exécute le service.</span><span class="sxs-lookup"><span data-stu-id="8e92e-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="8e92e-111">Cet exemple n'utilise pas de configuration pour définir l'adresse de point de terminaison, donc cela doit être fait dans le code.</span><span class="sxs-lookup"><span data-stu-id="8e92e-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="8e92e-112">Une fois le canal créé, les opérations de service peuvent être appelées comme pour un client généré.</span><span class="sxs-lookup"><span data-stu-id="8e92e-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="8e92e-113">Pour fermer le canal, il faut d'abord le caster en une interface <xref:System.ServiceModel.IClientChannel>.</span><span class="sxs-lookup"><span data-stu-id="8e92e-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="8e92e-114">Cela est dû au fait que le canal, tel que généré, est déclaré dans l'application cliente à l'aide de l'interface `ICalculator`, qui possède des méthodes comme `Add` et `Subtract` mais pas `Close`.</span><span class="sxs-lookup"><span data-stu-id="8e92e-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="8e92e-115">La méthode `Close` provient de l'interface <xref:System.ServiceModel.ICommunicationObject>.</span><span class="sxs-lookup"><span data-stu-id="8e92e-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="8e92e-116">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="8e92e-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8e92e-117">Appuyez sur ENTER dans la fenêtre de l'application pour fermer l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="8e92e-117">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8e92e-118">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="8e92e-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8e92e-119">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8e92e-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="8e92e-120">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8e92e-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="8e92e-121">Notez que cet exemple n'active pas la publication des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8e92e-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="8e92e-122">Vous devez d'abord activer la publication des métadonnées pour cet exemple pour régénérer le type de client.</span><span class="sxs-lookup"><span data-stu-id="8e92e-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="8e92e-123">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8e92e-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="8e92e-124">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="8e92e-124">To run the sample cross machine</span></span>

1. <span data-ttu-id="8e92e-125">Remplacez « localhost » dans le code suivant par le nom qualifié complet de l'ordinateur qui exécute le service.</span><span class="sxs-lookup"><span data-stu-id="8e92e-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="8e92e-126">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8e92e-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8e92e-127">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="8e92e-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8e92e-128">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8e92e-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e92e-129">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="8e92e-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
