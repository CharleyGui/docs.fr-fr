---
title: Bibliothèque d'activités
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142899"
---
# <a name="activity-library"></a><span data-ttu-id="2035d-102">Bibliothèque d'activités</span><span class="sxs-lookup"><span data-stu-id="2035d-102">Activity Library</span></span>
<span data-ttu-id="2035d-103">Cette section contient des échantillons qui démontrent des activités personnalisées avancées dans Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="2035d-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2035d-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2035d-104">In This Section</span></span>

 [<span data-ttu-id="2035d-105">Activité personnalisée SendMail</span><span class="sxs-lookup"><span data-stu-id="2035d-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="2035d-106">Montre comment créer une activité personnalisée dérivée de <xref:System.Activities.AsyncCodeActivity> pour envoyer du courrier à l'aide de SMTP afin de l'utiliser dans une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="2035d-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="2035d-107">ParallelForEach limité</span><span class="sxs-lookup"><span data-stu-id="2035d-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="2035d-108">Montre comment l’activité `ThrottleParallelForEach` est semblable à l’activité <xref:System.Activities.Statements.ParallelForEach%601> hormis le seul fait qu’elle permet la définition d’un facteur de concurrence pour restreindre le nombre de branches simultanées à exécuter.</span><span class="sxs-lookup"><span data-stu-id="2035d-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="2035d-109">Activités d’accès aux bases de données</span><span class="sxs-lookup"><span data-stu-id="2035d-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="2035d-110">Démontre comment créer des activités qui permettent aux bases de données d’accéder à des bases de données de récupérer ou de modifier des informations et [d’utiliser ADO.NET](../../data/adonet/index.md) pour accéder à la base de données.</span><span class="sxs-lookup"><span data-stu-id="2035d-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="2035d-111">Activité de stratégie externalisée dans .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="2035d-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="2035d-112">Démontre comment l’activité ExternalizedPolicy4 permet d’exécuter la Fondation Windows Workflow existante dans .NET <xref:System.Workflow.Activities.Rules.RuleSet> Framework 3.5 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 3.5) objets dans Windows Workflow Foundation en (WF 4.5) directement en utilisant le moteur de règles qui est expédié dans WF 3.5.</span><span class="sxs-lookup"><span data-stu-id="2035d-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="2035d-113">ForEach non générique</span><span class="sxs-lookup"><span data-stu-id="2035d-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="2035d-114">Montre comment créer une version non générique de l'activité <xref:System.Activities.Statements.ForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="2035d-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="2035d-115">ParallelForEach non générique</span><span class="sxs-lookup"><span data-stu-id="2035d-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="2035d-116">Montre comment créer une version non générique de l'activité <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="2035d-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="2035d-117">Obtenir WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2035d-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="2035d-118">Montre comment utiliser l'activité personnalisée `GetWorkflowInstanceId` pour retourner l'ID d'instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="2035d-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
