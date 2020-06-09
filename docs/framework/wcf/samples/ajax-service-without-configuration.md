---
title: AJAX Service Without Configuration
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: ab3731ab6aeb80e0e46228b8bf702b0fe5c6e6e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575899"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="9b414-102">AJAX Service Without Configuration</span><span class="sxs-lookup"><span data-stu-id="9b414-102">AJAX Service Without Configuration</span></span>

<span data-ttu-id="9b414-103">Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service AJAX (Basic JavaScript and XML) asynchrone ASP.NET (un service auquel vous pouvez accéder à l’aide de code JavaScript à partir d’un client de navigateur Web) sans utiliser de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="9b414-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="9b414-104">Le service utilise une syntaxe spéciale dans le fichier .svc pour activer automatiquement un point de terminaison AJAX.</span><span class="sxs-lookup"><span data-stu-id="9b414-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>

<span data-ttu-id="9b414-105">La prise en charge d’AJAX dans WCF est optimisée pour une utilisation avec ASP.NET AJAX par le biais du `ScriptManager` contrôle.</span><span class="sxs-lookup"><span data-stu-id="9b414-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="9b414-106">Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez les [exemples Ajax](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="9b414-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9b414-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="9b414-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="9b414-108">Cet exemple est basé sur le service AJAX Service utilisant HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="9b414-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="9b414-109">Comme décrit dans l’exemple de [service Ajax de base](basic-ajax-service.md) , <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="9b414-109">As described in the [Basic AJAX Service](basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<span data-ttu-id="9b414-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ajoute automatiquement un <xref:System.ServiceModel.Description.WebScriptEndpoint> au service.</span><span class="sxs-lookup"><span data-stu-id="9b414-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="9b414-111">Si aucune modification de configuration ne doit être apportée au point de terminaison, la section `<system.ServiceModel>` peut être supprimée complètement du fichier Web.config pour le service.</span><span class="sxs-lookup"><span data-stu-id="9b414-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="9b414-112">Le fichier Web.config contient des paramètres ASP.NET, qui sont utilisés par ConfigFreeClientPage.aspx.</span><span class="sxs-lookup"><span data-stu-id="9b414-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="9b414-113">Si ce n'était pas le cas, l'intégralité du fichier Web.config pourrait être supprimée.</span><span class="sxs-lookup"><span data-stu-id="9b414-113">If that were not the case, the entire Web.config file could be removed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9b414-114">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9b414-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9b414-115">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="9b414-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9b414-116">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9b414-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9b414-117">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="9b414-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9b414-118">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="9b414-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="9b414-119">Veillez à suivre les instructions d’installation dans [la procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9b414-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="9b414-120">Générez la solution ConfigFreeAjaxService. sln comme décrit dans [génération des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9b414-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="9b414-121">Accédez à `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (n’ouvrez pas ConfigFreeClientPage. aspx dans le navigateur à partir du répertoire du projet).</span><span class="sxs-lookup"><span data-stu-id="9b414-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>

> [!NOTE]
> <span data-ttu-id="9b414-122">Avant d’exécuter cet exemple, assurez-vous que l’authentification anonyme et que l’authentification Windows ne sont pas toutes deux activées dans le dossier ServiceModelSamples des services IIS.</span><span class="sxs-lookup"><span data-stu-id="9b414-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="9b414-123">Si tel est le cas, désactivez l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="9b414-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="9b414-124">Une fois que vous avez exécuté l'exemple, activez l'authentification Windows et réexécutez « iisreset ».</span><span class="sxs-lookup"><span data-stu-id="9b414-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>

## <a name="see-also"></a><span data-ttu-id="9b414-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b414-125">See also</span></span>

- [<span data-ttu-id="9b414-126">Basic AJAX Service</span><span class="sxs-lookup"><span data-stu-id="9b414-126">Basic AJAX Service</span></span>](basic-ajax-service.md)
