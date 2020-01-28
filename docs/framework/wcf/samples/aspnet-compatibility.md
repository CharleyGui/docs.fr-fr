---
title: ASP.NET Compatibility
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 1f1690cdd1a880c852abc04ea8e4958bae2c5432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728022"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="939f0-102">ASP.NET Compatibility</span><span class="sxs-lookup"><span data-stu-id="939f0-102">ASP.NET Compatibility</span></span>

<span data-ttu-id="939f0-103">Cet exemple montre comment activer le mode de compatibilité ASP.NET dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="939f0-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="939f0-104">Les services qui s’exécutent en mode de compatibilité ASP.NET participent pleinement au pipeline d’application ASP.NET et peuvent utiliser des fonctionnalités ASP.NET telles que l’autorisation de fichier/d’URL, l’état de session et la classe <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="939f0-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="939f0-105">La classe <xref:System.Web.HttpContext> permet d’accéder aux cookies, aux sessions et à d’autres fonctionnalités ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="939f0-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="939f0-106">Dans ce mode, les liaisons doivent utiliser le transport HTTP et le service lui-même doit être hébergé dans les services IIS.</span><span class="sxs-lookup"><span data-stu-id="939f0-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>

<span data-ttu-id="939f0-107">Dans cet exemple, le client est une application console (fichier exécutable) et le service est hébergé dans les services IIS</span><span class="sxs-lookup"><span data-stu-id="939f0-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="939f0-108">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="939f0-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="939f0-109">Cet exemple nécessite un pool d’applications .NET Framework 4 pour pouvoir s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="939f0-109">This sample requires a .NET Framework 4 application pool in order to run.</span></span> <span data-ttu-id="939f0-110">Pour créer un pool d'applications ou modifier le pool d'applications par défaut, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="939f0-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>

1. <span data-ttu-id="939f0-111">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="939f0-111">Open **Control Panel**.</span></span>  <span data-ttu-id="939f0-112">Ouvrez l’applet **Outils d’administration** sous le titre **système et sécurité** .</span><span class="sxs-lookup"><span data-stu-id="939f0-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="939f0-113">Ouvrez l’applet du **Gestionnaire de Internet Information Services (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="939f0-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>

2. <span data-ttu-id="939f0-114">Développez l’arborescence dans le volet **connexions** .</span><span class="sxs-lookup"><span data-stu-id="939f0-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="939f0-115">Sélectionnez le nœud **pools d’applications** .</span><span class="sxs-lookup"><span data-stu-id="939f0-115">Select the **Application Pools** node.</span></span>

3. <span data-ttu-id="939f0-116">Pour définir le pool d’applications par défaut de sorte qu’il utilise .NET Framework 4 (ce qui peut entraîner des problèmes d’incompatibilité avec les sites existants), cliquez avec le bouton droit sur l’élément de liste **DefaultAppPool** et sélectionnez **paramètres de base...** .</span><span class="sxs-lookup"><span data-stu-id="939f0-116">To set the default application pool to use .NET Framework 4 (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="939f0-117">Définissez la liste déroulante **version du .NET Framework** sur **.NET Framework v 4.0.30128** (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="939f0-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>

4. <span data-ttu-id="939f0-118">Pour créer un nouveau pool d’applications qui utilise .NET Framework 4 (pour préserver la compatibilité pour d’autres applications), cliquez avec le bouton droit sur le nœud **pools d’applications** , puis sélectionnez **Ajouter un pool d’applications...** .</span><span class="sxs-lookup"><span data-stu-id="939f0-118">To create a new application pool that uses .NET Framework 4 (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="939f0-119">Nommez le nouveau pool d’applications, puis définissez la liste déroulante **version du .NET Framework** sur **.NET Framework v 4.0.30128** (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="939f0-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="939f0-120">Après avoir exécuté les étapes de configuration ci-dessous, cliquez avec le bouton droit sur l’application **servicemodelsamples** , puis sélectionnez **gérer l’application**, **Paramètres avancés...** .</span><span class="sxs-lookup"><span data-stu-id="939f0-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="939f0-121">Définissez le **pool d’applications** sur le nouveau pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="939f0-121">Set the **Application Pool** to the new application pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="939f0-122">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="939f0-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="939f0-123">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="939f0-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="939f0-124">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="939f0-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="939f0-125">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="939f0-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`

<span data-ttu-id="939f0-126">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="939f0-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="939f0-127">Les contrats `ICalculator` et `ICalculatorSession` ont été modifiés pour permettre à un ensemble d'opérations d'être effectuées tout en conservant un résultat d'exécution.</span><span class="sxs-lookup"><span data-stu-id="939f0-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculatorSession
{
    [OperationContract]
    void Clear();
    [OperationContract]
    void AddTo(double n);
    [OperationContract]
    void SubtractFrom(double n);
    [OperationContract]
    void MultiplyBy(double n);
    [OperationContract]
    void DivideBy(double n);
    [OperationContract]
    double Result();
}
```

<span data-ttu-id="939f0-128">Le service conserve l’état de chaque client (à l’aide de la fonctionnalité correspondante) tandis que plusieurs opérations de service sont appelées pour effectuer un calcul.</span><span class="sxs-lookup"><span data-stu-id="939f0-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="939f0-129">Le client peut récupérer le résultat actuel en appelant `Result` et remettre le résultat à zéro en appelant `Clear`.</span><span class="sxs-lookup"><span data-stu-id="939f0-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>

<span data-ttu-id="939f0-130">Le service utilise la session ASP.NET pour stocker le résultat de chaque session cliente.</span><span class="sxs-lookup"><span data-stu-id="939f0-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="939f0-131">Cela lui permet de conserver le résultat d'exécution de chaque client tandis qu'il reçoit plusieurs appels.</span><span class="sxs-lookup"><span data-stu-id="939f0-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>

> [!NOTE]
> <span data-ttu-id="939f0-132">L’état de session ASP.NET et les sessions WCF sont très différents.</span><span class="sxs-lookup"><span data-stu-id="939f0-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="939f0-133">Pour plus d’informations sur les sessions WCF, consultez [session](../../../../docs/framework/wcf/samples/session.md) .</span><span class="sxs-lookup"><span data-stu-id="939f0-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>

<span data-ttu-id="939f0-134">Le service a une dépendance intime sur l’état de session ASP.NET et nécessite le mode de compatibilité ASP.NET pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="939f0-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="939f0-135">Ces exigences sont définies de manière déclarative en appliquant l’attribut `AspNetCompatibilityRequirements`.</span><span class="sxs-lookup"><span data-stu-id="939f0-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>

```csharp
[AspNetCompatibilityRequirements(RequirementsMode =
                       AspNetCompatibilityRequirementsMode.Required)]
public class CalculatorService : ICalculatorSession
{
    double Result
    {  // store result in AspNet Session
       get {
          if (HttpContext.Current.Session["Result"] != null)
             return (double)HttpContext.Current.Session["Result"];
          return 0.0D;
       }
       set
       {
          HttpContext.Current.Session["Result"] = value;
       }
    }
    public void Clear()
    {
        Result = 0.0D;
    }
    public void AddTo(double n)
    {
        Result += n;
    }
    public void SubtractFrom(double n)
    {
        Result -= n;
    }
    public void MultiplyBy(double n)
    {
        Result *= n;
    }
    public void DivideBy(double n)
    {
        Result /= n;
    }
    public double Result()
    {
        return Result;
    }
}
```

<span data-ttu-id="939f0-136">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="939f0-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="939f0-137">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="939f0-137">Press ENTER in the client window to shut down the client.</span></span>

```console
0, + 100, - 50, * 17.65, / 2 = 441.25
Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="939f0-138">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="939f0-138">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="939f0-139">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="939f0-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="939f0-140">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="939f0-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="939f0-141">Une fois la solution générée, exécutez Setup. bat pour configurer l’application ServiceModelSamples dans IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="939f0-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="939f0-142">Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu’application IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="939f0-142">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="939f0-143">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="939f0-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="939f0-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="939f0-144">See also</span></span>

- <span data-ttu-id="939f0-145">[Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="939f0-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
