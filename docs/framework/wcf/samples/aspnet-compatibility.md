---
title: ASP.NET Compatibility
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: 01329769b74c8a5841b5a2024d3ed674c108be1c
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487670"
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="3ece2-102">ASP.NET Compatibility</span><span class="sxs-lookup"><span data-stu-id="3ece2-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="3ece2-103">Cet exemple montre comment activer le mode de compatibilité ASP.NET dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ece2-103">This sample demonstrates how to enable ASP.NET Compatibility mode in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3ece2-104">Utilisent des services qui s’exécutent dans la compatibilité ASP.NET participent pleinement le pipeline d’application ASP.NET de mode et peut rendre des fonctionnalités ASP.NET telles que l’autorisation de fichier/URL, l’état de session et le <xref:System.Web.HttpContext> classe.</span><span class="sxs-lookup"><span data-stu-id="3ece2-104">Services running in ASP.NET Compatibility mode participate fully in the ASP.NET application pipeline and can make use of ASP.NET features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="3ece2-105">Le <xref:System.Web.HttpContext> classe permet d’accéder aux cookies, les sessions et les autres fonctionnalités ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3ece2-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other ASP.NET features.</span></span> <span data-ttu-id="3ece2-106">Dans ce mode, les liaisons doivent utiliser le transport HTTP et le service lui-même doit être hébergé dans les services IIS.</span><span class="sxs-lookup"><span data-stu-id="3ece2-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="3ece2-107">Dans cet exemple, le client est une application console (fichier exécutable) et le service est hébergé dans les services IIS</span><span class="sxs-lookup"><span data-stu-id="3ece2-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ece2-108">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="3ece2-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="3ece2-109">Cet exemple requiert pour fonctionner un pool d'applications [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ece2-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="3ece2-110">Pour créer un pool d'applications ou modifier le pool d'applications par défaut, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="3ece2-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  

1. <span data-ttu-id="3ece2-111">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="3ece2-111">Open **Control Panel**.</span></span>  <span data-ttu-id="3ece2-112">Ouvrez le **outils d’administration** applet sous le **système et sécurité** titre.</span><span class="sxs-lookup"><span data-stu-id="3ece2-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="3ece2-113">Ouvrez le **Internet Information Services (IIS) Manager** applet.</span><span class="sxs-lookup"><span data-stu-id="3ece2-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  

2. <span data-ttu-id="3ece2-114">Développez l’arborescence dans le **connexions** volet.</span><span class="sxs-lookup"><span data-stu-id="3ece2-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="3ece2-115">Sélectionnez le **Pools d’applications** nœud.</span><span class="sxs-lookup"><span data-stu-id="3ece2-115">Select the **Application Pools** node.</span></span>  

3. <span data-ttu-id="3ece2-116">Pour définir le pool d’applications par défaut à utiliser [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (ce qui peut provoquer des problèmes d’incompatibilité avec des sites existants), avec le bouton droit le **DefaultAppPool** élément de liste et sélectionnez **paramètres de base...** .</span><span class="sxs-lookup"><span data-stu-id="3ece2-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="3ece2-117">Définir le **.Net Framework Version** déroulant **.Net Framework v4.0.30128** (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="3ece2-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  

4. <span data-ttu-id="3ece2-118">Pour créer un nouveau pool d’applications qui utilise [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (pour préserver la compatibilité avec d’autres applications), avec le bouton droit le **Pools d’applications** nœud et sélectionnez **ajouter un Pool d’applications...** .</span><span class="sxs-lookup"><span data-stu-id="3ece2-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="3ece2-119">Nommez le nouveau pool d’applications et définissez le **.Net Framework Version** déroulant **.Net Framework v4.0.30128** (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="3ece2-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="3ece2-120">Une fois que le programme d’installation en cours d’exécution les étapes ci-dessous, cliquez sur le **ServiceModelSamples** application et sélectionnez **gérer l’Application**, **paramètres avancés...** .</span><span class="sxs-lookup"><span data-stu-id="3ece2-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="3ece2-121">Définir le **Pool d’applications** au nouveau pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="3ece2-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ece2-122">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3ece2-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3ece2-123">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3ece2-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3ece2-124">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="3ece2-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3ece2-125">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3ece2-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="3ece2-126">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="3ece2-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="3ece2-127">Les contrats `ICalculator` et `ICalculatorSession` ont été modifiés pour permettre à un ensemble d'opérations d'être effectuées tout en conservant un résultat d'exécution.</span><span class="sxs-lookup"><span data-stu-id="3ece2-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
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
  
 <span data-ttu-id="3ece2-128">Le service conserve l’état de chaque client (à l’aide de la fonctionnalité correspondante) tandis que plusieurs opérations de service sont appelées pour effectuer un calcul.</span><span class="sxs-lookup"><span data-stu-id="3ece2-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="3ece2-129">Le client peut récupérer le résultat actuel en appelant `Result` et remettre le résultat à zéro en appelant `Clear`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="3ece2-130">Le service utilise la session ASP.NET pour stocker le résultat pour chaque session client.</span><span class="sxs-lookup"><span data-stu-id="3ece2-130">The service uses the ASP.NET session to store the result for each client session.</span></span> <span data-ttu-id="3ece2-131">Cela lui permet de conserver le résultat d'exécution de chaque client tandis qu'il reçoit plusieurs appels.</span><span class="sxs-lookup"><span data-stu-id="3ece2-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ece2-132">État de session ASP.NET et des sessions WCF sont des aspects très différents.</span><span class="sxs-lookup"><span data-stu-id="3ece2-132">ASP.NET session state and WCF sessions are very different things.</span></span> <span data-ttu-id="3ece2-133">Consultez [Session](../../../../docs/framework/wcf/samples/session.md) pour plus d’informations sur les sessions de WCF.</span><span class="sxs-lookup"><span data-stu-id="3ece2-133">See [Session](../../../../docs/framework/wcf/samples/session.md) for details on WCF sessions.</span></span>
  
 <span data-ttu-id="3ece2-134">Le service a une dépendance approfondie sur l’état de session ASP.NET et nécessite le mode de compatibilité ASP.NET pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="3ece2-134">The service has an intimate dependency on ASP.NET session state and requires ASP.NET compatibility mode to function correctly.</span></span> <span data-ttu-id="3ece2-135">Ces exigences sont définies de manière déclarative en appliquant l’attribut `AspNetCompatibilityRequirements`.</span><span class="sxs-lookup"><span data-stu-id="3ece2-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
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
  
 <span data-ttu-id="3ece2-136">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="3ece2-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3ece2-137">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="3ece2-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3ece2-138">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3ece2-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3ece2-139">Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ece2-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3ece2-140">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ece2-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3ece2-141">Une fois la solution a été créée, exécutez Setup.bat pour installer l’Application ServiceModelSamples dans IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="3ece2-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="3ece2-142">Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu’Application IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="3ece2-142">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>  
  
4. <span data-ttu-id="3ece2-143">Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ece2-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ece2-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ece2-144">See also</span></span>

- [<span data-ttu-id="3ece2-145">Hébergement AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="3ece2-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
