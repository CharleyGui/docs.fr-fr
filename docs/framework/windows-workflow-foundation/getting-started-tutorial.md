---
title: Prise en main Tutorial2
description: Cet article commence une série de didacticiels qui vous présentent la programmation d’applications Windows Workflow Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: e9856320faa82becf12dda04d02f6f1c08081feb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293596"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="70def-103">Didacticiel de mise en route</span><span class="sxs-lookup"><span data-stu-id="70def-103">Getting Started Tutorial</span></span>

<span data-ttu-id="70def-104">Cette section contient un ensemble de rubriques de procédure pas à pas qui vous initient à la programmation d’applications Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="70def-104">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="70def-105">En suivant les procédures dans ces rubriques, vous générerez une application qui est un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="70def-105">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="70def-106">La première rubrique du didacticiel vous guide tout au long des étapes de création des activités personnalisées obligatoires pour le workflow.</span><span class="sxs-lookup"><span data-stu-id="70def-106">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="70def-107">Dans la deuxième rubrique, ces activités sont assemblées avec les activités de workflow intégrées dans un workflow d'organigramme.</span><span class="sxs-lookup"><span data-stu-id="70def-107">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="70def-108">Dans la troisième rubrique, l'application hôte est configurée pour exécuter le workflow et la persistance est introduite dans la dernière rubrique.</span><span class="sxs-lookup"><span data-stu-id="70def-108">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="70def-109">Chaque étape de ce processus dépendant des étapes précédentes, nous vous recommandons de les exécuter dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="70def-109">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70def-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="70def-110">In This Section</span></span>  

 [<span data-ttu-id="70def-111">Procédure : créer une activité</span><span class="sxs-lookup"><span data-stu-id="70def-111">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="70def-112">Décrit comment créer une activité personnalisée qui dérive de <xref:System.Activities.NativeActivity%601> et comment composer cette activité avec une activité intégrée dans une activité composite à l'aide du concepteur d'activités.</span><span class="sxs-lookup"><span data-stu-id="70def-112">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="70def-113">Procédure : créer un workflow</span><span class="sxs-lookup"><span data-stu-id="70def-113">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="70def-114">Décrit comment créer des workflows d'organigramme, séquentiels et de machine à états à l'aide des activités prédéfinies et des activités personnalisées du didacticiel précédent.</span><span class="sxs-lookup"><span data-stu-id="70def-114">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="70def-115">Procédure : exécuter un workflow</span><span class="sxs-lookup"><span data-stu-id="70def-115">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="70def-116">Décrit comment appeler un workflow à partir d'un environnement hôte, passer des données à l'intérieur et à l'extérieur d'un workflow, et reprendre des signets.</span><span class="sxs-lookup"><span data-stu-id="70def-116">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="70def-117">Procédure : créer et exécuter un workflow durable</span><span class="sxs-lookup"><span data-stu-id="70def-117">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="70def-118">Décrit comment ajouter la persistance à une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="70def-118">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="70def-119">Procédure : créer un participant de suivi de personnalisé</span><span class="sxs-lookup"><span data-stu-id="70def-119">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="70def-120">Décrit comment créer un participant de suivi personnalisé et un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="70def-120">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="70def-121">Procédure : héberger plusieurs versions d’un workflow côte à côte</span><span class="sxs-lookup"><span data-stu-id="70def-121">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="70def-122">Décrit comment utiliser `WorkflowIdentity` pour héberger plusieurs versions d'un workflow côte à côte.</span><span class="sxs-lookup"><span data-stu-id="70def-122">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="70def-123">Procédure : mettre à jour la définition d’une instance de workflow en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="70def-123">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="70def-124">Décrit comment utiliser la mise à jour dynamique pour modifier des instances en cours de exécution de workflow.</span><span class="sxs-lookup"><span data-stu-id="70def-124">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70def-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70def-125">See also</span></span>

- [<span data-ttu-id="70def-126">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="70def-126">Windows Workflow Foundation Programming</span></span>](programming.md)
