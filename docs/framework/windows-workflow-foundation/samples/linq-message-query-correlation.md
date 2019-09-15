---
title: Corrélation de requête de message LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 202d65914d32245952f308d3115ec93231f95f15
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989336"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="41251-102">Corrélation de requête de message LINQ</span><span class="sxs-lookup"><span data-stu-id="41251-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="41251-103">Cet exemple montre comment effectuer une corrélation basée sur le contenu à l’aide d’une implémentation <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisée par opposition au <xref:System.ServiceModel.XPathMessageQuery> fourni par le système.</span><span class="sxs-lookup"><span data-stu-id="41251-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="41251-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="41251-104">Demonstrates</span></span>  
 <span data-ttu-id="41251-105"><xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisé, corrélation basée sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="41251-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="41251-106">Discussion</span><span class="sxs-lookup"><span data-stu-id="41251-106">Discussion</span></span>  
 <span data-ttu-id="41251-107">Cet exemple montre le mode d'extension à partir de la classe de base <xref:System.ServiceModel.Dispatcher.MessageQuery> pour les besoins de la corrélation.</span><span class="sxs-lookup"><span data-stu-id="41251-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="41251-108">L'implémentation personnalisée, `LinqMessageQuery`, permet aux utilisateurs de fournir un XName à rechercher dans le message à l'aide de XLinq.</span><span class="sxs-lookup"><span data-stu-id="41251-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="41251-109">Les données récupérées par la requête sont utilisées pour former la clé de corrélation afin de distribuer des messages à l'instance de workflow appropriée.</span><span class="sxs-lookup"><span data-stu-id="41251-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="41251-110">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="41251-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="41251-111">Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP.</span><span class="sxs-lookup"><span data-stu-id="41251-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="41251-112">Pour exécuter cet exemple, des listes de contrôle d’accès d’URL appropriées doivent être ajoutées (pour plus d’informations, consultez [configuration de http et HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) ), soit en exécutant Visual Studio en tant qu’administrateur, soit en exécutant la commande suivante à une invite de commandes avec élévation de privilèges pour ajouter les listes de contrôle d’accès appropriées.</span><span class="sxs-lookup"><span data-stu-id="41251-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="41251-113">Vérifiez que vos domaine et nom d'utilisateur sont substitués.</span><span class="sxs-lookup"><span data-stu-id="41251-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="41251-114">Une fois les listes de contrôle d'accès (ACL) d'URL ajoutées, effectuez les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="41251-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="41251-115">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="41251-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="41251-116">Pour définir plusieurs projets de démarrage, cliquez avec le bouton droit sur la solution et sélectionnez **définir les projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="41251-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="41251-117">Ajoutez le **service** et le **client** (dans cet ordre) en tant que plusieurs projets de démarrage.</span><span class="sxs-lookup"><span data-stu-id="41251-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="41251-118">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="41251-118">Run the application.</span></span> <span data-ttu-id="41251-119">La console cliente affiche un workflow qui envoie une commande et reçoit l'ID de bon de commande, puis confirme par la suite la commande.</span><span class="sxs-lookup"><span data-stu-id="41251-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="41251-120">La fenêtre Service affichera les demandes en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="41251-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="41251-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="41251-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="41251-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="41251-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="41251-123">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="41251-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41251-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="41251-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
