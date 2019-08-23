---
title: Programme de résolution de signets pour WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 017c5f959ed109ffe9b5e5c4bf2b9de9d04fdcdb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964940"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="21bb8-102">Programme de résolution de signets pour WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="21bb8-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="21bb8-103">Cet exemple montre comment <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> peut être utilisé avec <xref:System.ServiceModel.Activities.WorkflowServiceHost> pour créer des instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="21bb8-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="21bb8-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="21bb8-104">Demonstrates</span></span>  
 <span data-ttu-id="21bb8-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="21bb8-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="21bb8-106">Discussion</span><span class="sxs-lookup"><span data-stu-id="21bb8-106">Discussion</span></span>  
 <span data-ttu-id="21bb8-107">Cet exemple utilise <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pour créer des instances de workflow hébergées à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="21bb8-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="21bb8-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> est un point d'extensibilité pour <xref:System.ServiceModel.Activities.WorkflowServiceHost> qui peut être utilisé dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="21bb8-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="21bb8-109">Création d'instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="21bb8-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="21bb8-110">Reprise de signets sur une instance de workflow hébergée dans un <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="21bb8-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="21bb8-111">L'exemple de point de terminaison inclus expose un contrat qui fournit des opérations pour créer un workflow et retourne l'ID d'instance ou crée une instance avec un ID spécifique.</span><span class="sxs-lookup"><span data-stu-id="21bb8-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="21bb8-112">L'exemple d'application console crée une instance <xref:System.ServiceModel.Activities.WorkflowServiceHost> avec une définition de workflow et ajoute un `CreationEndpoint` à l'hôte.</span><span class="sxs-lookup"><span data-stu-id="21bb8-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="21bb8-113">Il fait alors appel à l'opération `Create` sur le point de terminaison pour créer une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="21bb8-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21bb8-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="21bb8-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="21bb8-115">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="21bb8-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="21bb8-116">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="21bb8-116">Run the application.</span></span> <span data-ttu-id="21bb8-117">La console `CreationEndpoint` affiche un message qui inclut l'ID d'instance lorsque l'instance de workflow est créée.</span><span class="sxs-lookup"><span data-stu-id="21bb8-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="21bb8-118">Le message «Hello World!»</span><span class="sxs-lookup"><span data-stu-id="21bb8-118">The message "Hello World!"</span></span> <span data-ttu-id="21bb8-119">est imprimé par l’instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="21bb8-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="21bb8-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21bb8-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="21bb8-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="21bb8-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="21bb8-122">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="21bb8-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21bb8-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="21bb8-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
