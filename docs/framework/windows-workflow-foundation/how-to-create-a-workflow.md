---
title: 'Procédure : créer un workflow'
description: Suivez l’une des trois options de cette section pour créer un flux de travail dans le cadre de ce didacticiel de Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 7e4575436405e74b7575e55bea37a1a99d879a3e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419562"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="7b6fa-103">Procédure : créer un workflow</span><span class="sxs-lookup"><span data-stu-id="7b6fa-103">How to: Create a Workflow</span></span>
<span data-ttu-id="7b6fa-104">Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7b6fa-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="7b6fa-105">Les rubriques de cette section vous guident dans la création d’un workflow qui utilise à la fois des activités intégrées telles que l' <xref:System.Activities.Statements.Flowchart> activité et les activités personnalisées de la rubrique précédente [Comment : créer une activité](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="7b6fa-105">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="7b6fa-106">Le workflow modélise un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="7b6fa-106">The workflow models a number guessing game.</span></span> <span data-ttu-id="7b6fa-107">Une seule des rubriques de cette section est nécessaire pour terminer le didacticiel ; vous devez choisir le style qui vous intéresse et suivre cette étape.</span><span class="sxs-lookup"><span data-stu-id="7b6fa-107">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="7b6fa-108">Toutefois, vous pouvez terminer toutes les rubriques si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="7b6fa-108">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b6fa-109">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="7b6fa-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="7b6fa-110">Pour effectuer cette rubrique, vous devez d’abord terminer [la procédure : créer une activité](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="7b6fa-110">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b6fa-111">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="7b6fa-111">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b6fa-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7b6fa-112">In This Section</span></span>  
 [<span data-ttu-id="7b6fa-113">Procédure : créer un workflow séquentiel</span><span class="sxs-lookup"><span data-stu-id="7b6fa-113">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="7b6fa-114">Décrit comment créer un workflow séquentiel à l'aide de l'activité <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="7b6fa-114">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="7b6fa-115"> d’organigramme</span><span class="sxs-lookup"><span data-stu-id="7b6fa-115">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="7b6fa-116">Décrit comment créer un workflow d'organigramme à l'aide de l'activité <xref:System.Activities.Statements.Flowchart>.</span><span class="sxs-lookup"><span data-stu-id="7b6fa-116">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="7b6fa-117">Guide pratique pour créer un workflow de machine à états</span><span class="sxs-lookup"><span data-stu-id="7b6fa-117">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="7b6fa-118">Décrit comment créer un workflow de machine à états à l'aide de l'activité <xref:System.Activities.Statements.StateMachine>.</span><span class="sxs-lookup"><span data-stu-id="7b6fa-118">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b6fa-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b6fa-119">See also</span></span>

- [<span data-ttu-id="7b6fa-120">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="7b6fa-120">Windows Workflow Foundation Programming</span></span>](programming.md)
