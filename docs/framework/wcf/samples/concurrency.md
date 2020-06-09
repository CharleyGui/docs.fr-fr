---
title: Accès concurrentiel
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 393c8a79cb60a33203b41a0778176a4d78a9b6ee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585309"
---
# <a name="concurrency"></a><span data-ttu-id="3aef1-102">Accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="3aef1-102">Concurrency</span></span>
<span data-ttu-id="3aef1-103">Cet exemple montre l'utilisation du <xref:System.ServiceModel.ServiceBehaviorAttribute> avec l'énumération <xref:System.ServiceModel.ConcurrencyMode> qui contrôle si une instance de service traite des messages l'un après l'autre ou simultanément.</span><span class="sxs-lookup"><span data-stu-id="3aef1-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="3aef1-104">L’exemple est basé sur le [prise en main](getting-started-sample.md), qui implémente le `ICalculator` contrat de service.</span><span class="sxs-lookup"><span data-stu-id="3aef1-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="3aef1-105">Cet exemple définit un nouveau contrat, `ICalculatorConcurrency`, qui hérite d' `ICalculator`, fournissant deux opérations supplémentaires pour l'inspection de l'état d'accès concurrentiel du service.</span><span class="sxs-lookup"><span data-stu-id="3aef1-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="3aef1-106">En modifiant le paramètre d'accès concurrentiel, vous pouvez observer le changement de comportement en exécutant le client.</span><span class="sxs-lookup"><span data-stu-id="3aef1-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="3aef1-107">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="3aef1-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3aef1-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="3aef1-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3aef1-109">Trois modes d'accès concurrentiel sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="3aef1-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="3aef1-110">`Single` : chaque instance de service traite un message à la fois.</span><span class="sxs-lookup"><span data-stu-id="3aef1-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="3aef1-111">Il s'agit du mode d'accès concurrentiel par défaut.</span><span class="sxs-lookup"><span data-stu-id="3aef1-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="3aef1-112">`Multiple` : chaque instance de service traite plusieurs messages simultanément.</span><span class="sxs-lookup"><span data-stu-id="3aef1-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="3aef1-113">Pour utiliser ce mode, l'implémentation de service doit être « thread-safe ».</span><span class="sxs-lookup"><span data-stu-id="3aef1-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="3aef1-114">`Reentrant` : chaque instance de service traite un message à la fois, mais accepte des appels réentrants.</span><span class="sxs-lookup"><span data-stu-id="3aef1-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="3aef1-115">Le service accepte uniquement ces appels lorsqu’il appelle. Reentrant est illustré dans l’exemple [ConcurrencyMode. Reentrant](concurrencymode-reentrant.md) .</span><span class="sxs-lookup"><span data-stu-id="3aef1-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="3aef1-116">L'utilisation de l'accès concurrentiel est associée au mode d'instanciation.</span><span class="sxs-lookup"><span data-stu-id="3aef1-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="3aef1-117">Dans l'instanciation <xref:System.ServiceModel.InstanceContextMode.PerCall>, l'accès concurrentiel n'est pas pertinent, parce que chaque message est traité par une nouvelle instance de service.</span><span class="sxs-lookup"><span data-stu-id="3aef1-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="3aef1-118">Dans l'instanciation <xref:System.ServiceModel.InstanceContextMode.Single>, l'accès concurrentiel <xref:System.ServiceModel.ConcurrencyMode.Single> ou <xref:System.ServiceModel.ConcurrencyMode.Multiple> est pertinent, selon que la même instance traite des messages l'un après l'autre ou simultanément.</span><span class="sxs-lookup"><span data-stu-id="3aef1-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="3aef1-119">Dans l'instanciation <xref:System.ServiceModel.InstanceContextMode.PerSession>, chacun des modes d'accès concurrentiel peut être pertinent.</span><span class="sxs-lookup"><span data-stu-id="3aef1-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="3aef1-120">La classe de service spécifie le comportement d'accès concurrentiel avec l'attribut `[ServiceBehavior(ConcurrencyMode=<setting>)]` comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="3aef1-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="3aef1-121">En modifiant les lignes commentées, vous pouvez tester les modes d'accès concurrentiel `Single` et `Multiple`.</span><span class="sxs-lookup"><span data-stu-id="3aef1-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="3aef1-122">Veillez à régénérer le service après avoir modifié le mode d'accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="3aef1-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="3aef1-123">L'exemple utilise par défaut l'accès concurrentiel <xref:System.ServiceModel.ConcurrencyMode.Multiple> avec l'instanciation <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="3aef1-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="3aef1-124">Le code client a été modifié pour utiliser un proxy asynchrone.</span><span class="sxs-lookup"><span data-stu-id="3aef1-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="3aef1-125">Le client peut ainsi effectuer plusieurs appels au service sans attendre de réponse entre chaque appel.</span><span class="sxs-lookup"><span data-stu-id="3aef1-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="3aef1-126">Vous pouvez observer la différence dans le comportement du mode d'accès concurrentiel de service.</span><span class="sxs-lookup"><span data-stu-id="3aef1-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="3aef1-127">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="3aef1-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3aef1-128">Le mode d'accès concurrentiel sous lequel le service s'exécute s'affiche, chaque opération est appelée, puis, le nombre d'opérations est affiché.</span><span class="sxs-lookup"><span data-stu-id="3aef1-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="3aef1-129">Notez que lorsque le mode d'accès concurrentiel est `Multiple`, les résultats sont retournés dans un ordre différent de l'ordre d'appel parce que le service traite plusieurs messages simultanément.</span><span class="sxs-lookup"><span data-stu-id="3aef1-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="3aef1-130">En modifiant le mode d'accès concurrentiel en `Single`, les résultats sont retournés dans l'ordre d'appel parce que le service traite chaque message individuellement.</span><span class="sxs-lookup"><span data-stu-id="3aef1-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="3aef1-131">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="3aef1-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3aef1-132">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3aef1-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3aef1-133">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3aef1-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3aef1-134">Si vous utilisez Svcutil. exe pour générer le client proxy, assurez-vous d’inclure l' `/async` option.</span><span class="sxs-lookup"><span data-stu-id="3aef1-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="3aef1-135">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3aef1-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3aef1-136">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3aef1-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3aef1-137">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3aef1-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3aef1-138">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3aef1-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3aef1-139">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3aef1-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3aef1-140">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3aef1-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
