---
title: Prise en main Tutorial2
description: Cet article commence une série de didacticiels qui vous présentent la programmation d’applications Windows Workflow Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 148ba77231067bf5f8ff1d8b444b83d951ce8761
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419848"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="1a4ad-103">Didacticiel de mise en route</span><span class="sxs-lookup"><span data-stu-id="1a4ad-103">Getting Started Tutorial</span></span>
<span data-ttu-id="1a4ad-104">Cette section contient un ensemble de rubriques de procédure pas à pas qui vous initient à la programmation d’applications Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="1a4ad-104">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="1a4ad-105">En suivant les procédures dans ces rubriques, vous générerez une application qui est un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-105">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="1a4ad-106">La première rubrique du didacticiel vous guide tout au long des étapes de création des activités personnalisées obligatoires pour le workflow.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-106">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="1a4ad-107">Dans la deuxième rubrique, ces activités sont assemblées avec les activités de workflow intégrées dans un workflow d'organigramme.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-107">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="1a4ad-108">Dans la troisième rubrique, l'application hôte est configurée pour exécuter le workflow et la persistance est introduite dans la dernière rubrique.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-108">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="1a4ad-109">Chaque étape de ce processus dépendant des étapes précédentes, nous vous recommandons de les exécuter dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-109">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a4ad-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1a4ad-110">In This Section</span></span>  
 [<span data-ttu-id="1a4ad-111">Guide pratique pour créer une activité</span><span class="sxs-lookup"><span data-stu-id="1a4ad-111">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="1a4ad-112">Décrit comment créer une activité personnalisée qui dérive de <xref:System.Activities.NativeActivity%601> et comment composer cette activité avec une activité intégrée dans une activité composite à l'aide du concepteur d'activités.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-112">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="1a4ad-113">Guide pratique pour créer un workflow</span><span class="sxs-lookup"><span data-stu-id="1a4ad-113">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="1a4ad-114">Décrit comment créer des workflows d'organigramme, séquentiels et de machine à états à l'aide des activités prédéfinies et des activités personnalisées du didacticiel précédent.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-114">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="1a4ad-115">Guide pratique pour exécuter un workflow</span><span class="sxs-lookup"><span data-stu-id="1a4ad-115">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="1a4ad-116">Décrit comment appeler un workflow à partir d'un environnement hôte, passer des données à l'intérieur et à l'extérieur d'un workflow, et reprendre des signets.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-116">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="1a4ad-117">Procédure : créer et exécuter un workflow de longue durée</span><span class="sxs-lookup"><span data-stu-id="1a4ad-117">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="1a4ad-118">Décrit comment ajouter la persistance à une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-118">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="1a4ad-119">Guide pratique pour créer un participant de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="1a4ad-119">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="1a4ad-120">Décrit comment créer un participant de suivi personnalisé et un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-120">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="1a4ad-121">Procédure : héberger plusieurs versions d'un workflow côte à côte</span><span class="sxs-lookup"><span data-stu-id="1a4ad-121">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="1a4ad-122">Décrit comment utiliser `WorkflowIdentity` pour héberger plusieurs versions d'un workflow côte à côte.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-122">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="1a4ad-123">Guide pratique pour mettre à jour la définition d’une instance de workflow en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="1a4ad-123">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="1a4ad-124">Décrit comment utiliser la mise à jour dynamique pour modifier des instances en cours de exécution de workflow.</span><span class="sxs-lookup"><span data-stu-id="1a4ad-124">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4ad-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a4ad-125">See also</span></span>

- [<span data-ttu-id="1a4ad-126">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="1a4ad-126">Windows Workflow Foundation Programming</span></span>](programming.md)
