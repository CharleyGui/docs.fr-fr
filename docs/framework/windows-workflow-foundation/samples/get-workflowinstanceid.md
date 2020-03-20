---
title: Obtenir WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 8cb83fcf15b814b0ca6f7f95f1a9b8eec70185cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142730"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="d8093-102">Obtenir WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="d8093-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="d8093-103">Cet exemple montre comment utiliser l'activité personnalisée `GetWorkflowInstanceId` pour retourner l'ID d'instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="d8093-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d8093-104">Illustre le</span><span class="sxs-lookup"><span data-stu-id="d8093-104">Demonstrates</span></span>  
 <span data-ttu-id="d8093-105">Développement de l'activité personnalisée, comment accéder à l'instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="d8093-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d8093-106">Discussions</span><span class="sxs-lookup"><span data-stu-id="d8093-106">Discussion</span></span>  
 <span data-ttu-id="d8093-107">L'obtention de l'ID d'instance d'un workflow en cours d'exécution requiert l'écriture de code.</span><span class="sxs-lookup"><span data-stu-id="d8093-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="d8093-108">Si vous souhaitez écrire un workflow complètement déclaratif, vous avez besoin d'une activité qui puisse retourner l'ID d'instance de workflow afin que l'activité puisse être référencée dans le workflow pour fournir une expérience de création de workflow complètement déclaratif.</span><span class="sxs-lookup"><span data-stu-id="d8093-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="d8093-109">De nombreux scénarios requièrent l'accès à l'ID d'instance, par exemple à des fins d'enregistrement ou d'audit, ou pour exécuter une corrélation au niveau de l'application en retournant l'ID d'instance à un client pour une future association (par exemple, en utilisant cette activité à l'intérieur d'une activité SendReply).</span><span class="sxs-lookup"><span data-stu-id="d8093-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="d8093-110">`GetWorkflowInstanceId` est implémenté comme un <xref:System.Activities.CodeActivity%601> parce qu'il doit retourner une valeur de type <xref:System.Guid>, et il doit avoir accès au <xref:System.Activities.CodeActivityContext> pour l'obtention de l'ID d'instance du workflow.</span><span class="sxs-lookup"><span data-stu-id="d8093-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="d8093-111">Son implémentation est assez basique.</span><span class="sxs-lookup"><span data-stu-id="d8093-111">Its implementation is fairly basic.</span></span>  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> <span data-ttu-id="d8093-112">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d8093-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d8093-113">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d8093-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d8093-114">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="d8093-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8093-115">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d8093-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
