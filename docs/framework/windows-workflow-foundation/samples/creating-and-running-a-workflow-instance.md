---
title: Création et exécution d'une instance de workflow
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016049"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="9174c-102">Création et exécution d'une instance de workflow</span><span class="sxs-lookup"><span data-stu-id="9174c-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="9174c-103">Cet exemple montre comment exécuter une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="9174c-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="9174c-104">Il indique comment l’exécuter de façon synchrone et de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9174c-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9174c-105">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="9174c-105">Demonstrates</span></span>

<span data-ttu-id="9174c-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="9174c-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="9174c-107">Discussion</span><span class="sxs-lookup"><span data-stu-id="9174c-107">Discussion</span></span>

<span data-ttu-id="9174c-108">La première partie de l'exemple utilise <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="9174c-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="9174c-109">Il s'agit de la façon la plus simple d'exécuter un workflow.</span><span class="sxs-lookup"><span data-stu-id="9174c-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="9174c-110">Les workflows exécutés avec <xref:System.Activities.WorkflowInvoker.Invoke%2A> s’exécutent de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="9174c-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="9174c-111">La deuxième partie de l'exemple utilise la classe <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="9174c-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="9174c-112"><xref:System.Activities.WorkflowApplication> vous permet d'avoir plus de contrôle sur chaque instance, notamment la possibilité d'interagir avec le workflow en cours d'exécution et d'exécuter le workflow de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9174c-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9174c-113">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9174c-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9174c-114">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="9174c-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9174c-115">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="9174c-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9174c-116">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="9174c-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="9174c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9174c-117">See also</span></span>

- [<span data-ttu-id="9174c-118">Utilisation de WorkflowInvoker et WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="9174c-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
