---
title: Utiliser la fermeture et l’abandon pour libérer des ressources de client WCF
description: La méthode dispose peut échouer et lever des exceptions en cas de défaillance du réseau. Cela peut provoquer un comportement indésirable. Utilisez plutôt Close et Abort pour libérer des ressources client lorsque le réseau a échoué.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: b338b760f461d7b773f43dd1f5e6dbce98f9e15a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599917"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="6cc39-105">Fermez et abandonnez les ressources Release en toute sécurité lorsque les connexions réseau ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="6cc39-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="6cc39-106">Cet exemple illustre l’utilisation `Close` des `Abort` méthodes et pour nettoyer les ressources lors de l’utilisation d’un client typé.</span><span class="sxs-lookup"><span data-stu-id="6cc39-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="6cc39-107">L' `using` instruction provoque des exceptions lorsque la connexion réseau n’est pas fiable.</span><span class="sxs-lookup"><span data-stu-id="6cc39-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="6cc39-108">Cet exemple est basé sur le [prise en main](getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="6cc39-108">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="6cc39-109">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="6cc39-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="6cc39-110">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6cc39-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="6cc39-111">Cet exemple contient deux des problèmes fréquents susceptibles de survenir lorsque l'instruction « using » C# est utilisée avec les clients typés ainsi que le code permettant de procéder au nettoyage adéquat après la survenue d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="6cc39-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="6cc39-112">L'instruction « using » C# provoque l'appel de `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="6cc39-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="6cc39-113">Cette méthode est identique à la méthode `Close`(), laquelle peut lever des exceptions lorsqu'une erreur réseau se produit.</span><span class="sxs-lookup"><span data-stu-id="6cc39-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="6cc39-114">L'appel de `Dispose`() se produit de manière implicite au niveau de l'accolade fermante du bloc « using », cette source d'exceptions a peu de chance d'être remarquée par une personne lisant le code ou par la personne chargée de le rédiger.</span><span class="sxs-lookup"><span data-stu-id="6cc39-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="6cc39-115">Cela représente une source potentielle d'erreurs d'application.</span><span class="sxs-lookup"><span data-stu-id="6cc39-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="6cc39-116">Le premier problème, illustré dans la méthode `DemonstrateProblemUsingCanThrow`, réside dans le fait que l'accolade fermante lève une exception et que le code figurant après cette accolade ne s'exécute pas :</span><span class="sxs-lookup"><span data-stu-id="6cc39-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="6cc39-117">Même si rien à l'intérieur du bloc « using » ne provoque la levée d'une exception ou si toutes les exceptions à l'intérieur de ce bloc sont interceptées, le code `Console.WriteLine` peut ne pas s'exécuter, l'appel implicite de `Dispose`() risquant de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="6cc39-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="6cc39-118">Le second problème, illustré dans la méthode `DemonstrateProblemUsingCanThrowAndMask`, est une autre conséquence du problème résultant de la levée d'une exception par l'accolade fermante :</span><span class="sxs-lookup"><span data-stu-id="6cc39-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="6cc39-119">La méthode `Dispose`() survenant à l'intérieur d'un bloc « finally », l'exception `ApplicationException` ne sera pas visible en dehors du bloc « using » si la méthode `Dispose`() échoue.</span><span class="sxs-lookup"><span data-stu-id="6cc39-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="6cc39-120">Si le code externe doit savoir à quel moment l'exception `ApplicationException` survient, le bloc « using » risque de poser un problème, car il masque cette exception.</span><span class="sxs-lookup"><span data-stu-id="6cc39-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="6cc39-121">Enfin, cette exemple illustre comment procéder à un nettoyage adéquat lors de la survenue d'exceptions dans `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="6cc39-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="6cc39-122">Pour ce faire, un bloc essai/interception est utilisé pour signaler les erreurs et appeler la méthode `Abort`.</span><span class="sxs-lookup"><span data-stu-id="6cc39-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="6cc39-123">Pour plus d’informations sur l’interception des exceptions à partir d’appels clients, consultez l’exemple [exceptions attendues](expected-exceptions.md) .</span><span class="sxs-lookup"><span data-stu-id="6cc39-123">See the [Expected Exceptions](expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

```csharp
try
{
    ...
    client.Close();
}
catch (CommunicationException e)
{
    ...
    client.Abort();
}
catch (TimeoutException e)
{
    ...
    client.Abort();
}
catch (Exception e)
{
    ...
    client.Abort();
    throw;
}
```

> [!NOTE]
> <span data-ttu-id="6cc39-124">Instruction « using » et ServiceHost : de nombreuses applications d'auto-hébergement ne se contentent pas seulement d'héberger des services et l'appel de la méthode ServiceHost.Close lève rarement une exception. Par conséquent, ces applications peuvent utiliser l'instruction « using » avec ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="6cc39-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="6cc39-125">Toutefois, n'oubliez pas que l'appel de la méthode ServiceHost.Close peut lever une exception `CommunicationException`. Par conséquent, si votre application continue à s'exécuter après la fermeture de ServiceHost, vous devez éviter d'utiliser l'instruction « using » et vous conformer au modèle mentionné précédemment.</span><span class="sxs-lookup"><span data-stu-id="6cc39-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="6cc39-126">Lorsque vous exécutez l'exemple, les exceptions et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="6cc39-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="6cc39-127">Le processus du client exécute trois scénarios qui essaient tous d'appeler `Divide`.</span><span class="sxs-lookup"><span data-stu-id="6cc39-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="6cc39-128">Le premier scénario contient le code ignoré à cause de l'exception levée par la méthode `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="6cc39-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="6cc39-129">Le deuxième scénario contient une exception importante masquée à cause de l'exception levée par la méthode `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="6cc39-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="6cc39-130">Le troisième scénario illustre le processus de nettoyage adéquat.</span><span class="sxs-lookup"><span data-stu-id="6cc39-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="6cc39-131">Le processus client est censé donner le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="6cc39-131">The expected output from the client process is:</span></span>

```console
=
= Demonstrating problem:  closing brace of using statement can throw.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating cleanup with Exceptions.
=
Calling client.Add(0.0, 0.0);
        client.Add(0.0, 0.0); returned 0
Calling client.Divide(0.0, 0.0);
Got System.ServiceModel.CommunicationException from Divide.

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6cc39-132">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6cc39-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6cc39-133">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6cc39-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6cc39-134">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6cc39-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="6cc39-135">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6cc39-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cc39-136">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6cc39-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6cc39-137">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6cc39-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6cc39-138">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6cc39-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6cc39-139">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6cc39-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
