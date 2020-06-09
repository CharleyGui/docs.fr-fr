---
title: instanciation
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 1cfaa0db5b81858b733343f17cae71e5815ef60b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596615"
---
# <a name="instancing"></a><span data-ttu-id="3c1c6-102">instanciation</span><span class="sxs-lookup"><span data-stu-id="3c1c6-102">Instancing</span></span>
<span data-ttu-id="3c1c6-103">Cet exemple illustre l'utilisation du comportement d'instanciation qui contrôle la manière dont les instances d'une classe de service sont créées en réponse aux demandes du client.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-103">The Instancing sample demonstrates the instancing behavior setting, which controls how instances of a service class are created in response to client requests.</span></span> <span data-ttu-id="3c1c6-104">L’exemple est basé sur le [prise en main](getting-started-sample.md), qui implémente le `ICalculator` contrat de service.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="3c1c6-105">Cet exemple définit un nouveau contrat, `ICalculatorInstance`, lequel hérite d'`ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-105">This sample defines a new contract, `ICalculatorInstance`, which inherits from `ICalculator`.</span></span> <span data-ttu-id="3c1c6-106">Le contrat spécifié par `ICalculatorInstance` fournit trois opérations supplémentaires pour l'inspection de l'état de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-106">The contract specified by `ICalculatorInstance` provides three additional operations for inspecting the state of the service instance.</span></span> <span data-ttu-id="3c1c6-107">Lorsque vous modifiez le paramètre d'instanciation, vous pouvez observer les changements au niveau du comportement en exécutant le client.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-107">By altering the instancing setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="3c1c6-108">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="3c1c6-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c1c6-109">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3c1c6-110">Les modes d'instanciation disponibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="3c1c6-110">The following instancing modes are available:</span></span>  
  
- <span data-ttu-id="3c1c6-111"><xref:System.ServiceModel.InstanceContextMode.PerCall> : une nouvelle instance de service est créée à chaque demande du client.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-111"><xref:System.ServiceModel.InstanceContextMode.PerCall>: A new service instance is created for each client request.</span></span>  
  
- <span data-ttu-id="3c1c6-112"><xref:System.ServiceModel.InstanceContextMode.PerSession> : une nouvelle instance est créée à chaque nouvelle session de client et est conservée aussi longtemps que dure cette dernière (une liaison prenant en charge les sessions est requise).</span><span class="sxs-lookup"><span data-stu-id="3c1c6-112"><xref:System.ServiceModel.InstanceContextMode.PerSession>: A new instance is created for each new client session, and maintained for the lifetime of that session (requires a binding that supports session).</span></span>  
  
- <span data-ttu-id="3c1c6-113"><xref:System.ServiceModel.InstanceContextMode.Single> : une instance unique de la classe de service gère toutes les demandes émanant du client aussi longtemps que dure l'application.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-113"><xref:System.ServiceModel.InstanceContextMode.Single>: A single instance of the service class handles all client requests for the lifetime of the application.</span></span>  
  
 <span data-ttu-id="3c1c6-114">La classe de service spécifie le comportement d'instanciation à l'aide de l'attribut `[ServiceBehavior(InstanceContextMode=<setting>)]`, tel qu'illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-114">The service class specifies instancing behavior with the `[ServiceBehavior(InstanceContextMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="3c1c6-115">Pour observer le comportement de chacun des modes d'instance, modifiez les lignes commentées.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-115">By changing which lines are commented out, you can observe the behavior of each of the instance modes.</span></span> <span data-ttu-id="3c1c6-116">N'oubliez pas de régénérer le service après avoir modifié le mode d'instanciation.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-116">Remember to rebuild the service after changing the instancing mode.</span></span> <span data-ttu-id="3c1c6-117">Vous n'avez pas à spécifier de paramètres d'instanciation sur le client.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-117">There are no instancing-related settings to specify on the client.</span></span>  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="3c1c6-118">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3c1c6-119">Le mode d'instance en fonction duquel le service s'exécute s'affiche.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-119">The instance mode the service is running under is displayed.</span></span> <span data-ttu-id="3c1c6-120">Au terme de chaque opération, l'ID de l'instance et le compteur d'opération s'affichent afin de rendre compte du comportement du mode d'instanciation.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-120">After each operation, the instance ID and operation count are displayed to reflect the behavior of the instancing mode.</span></span> <span data-ttu-id="3c1c6-121">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-121">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3c1c6-122">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3c1c6-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3c1c6-123">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c1c6-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3c1c6-124">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c1c6-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3c1c6-125">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c1c6-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3c1c6-126">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3c1c6-127">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3c1c6-128">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3c1c6-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c1c6-129">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3c1c6-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
