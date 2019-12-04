---
title: Réhébergement du Workflow Designer
ms.date: 03/30/2017
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
ms.openlocfilehash: 4b89c84d6761fa1e16bc17794885f64086a920f8
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716727"
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="a2bb6-102">Réhébergement du Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="a2bb6-102">Rehosting the Workflow Designer</span></span>
<span data-ttu-id="a2bb6-103">Les Concepteur de flux de travail Windows peuvent être réhébergés dans des environnements en dehors de Visual Studio 2012 afin de créer, de modifier et de surveiller des flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a2bb6-103">The Windows Workflow Designer can be rehosted in environments outside of Visual Studio 2012 for the purposes of creating, modifying, and monitoring workflows.</span></span>

 <span data-ttu-id="a2bb6-104">Le type <xref:System.Activities.Presentation.WorkflowDesigner> est un wrapper de la zone de dessin, de la grille des propriétés et d'autres éléments, et expose un modèle de programmation de base conçu pour gérer la majorité des scénarios de réhébergement du concepteur.</span><span class="sxs-lookup"><span data-stu-id="a2bb6-104">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="a2bb6-105">L’hébergement du <xref:System.Activities.Presentation.WorkflowDesigner> à l’intérieur d’une application Windows Presentation Foundation (WPF) est un scénario de réhébergement courant pour Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a2bb6-105">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a Windows Presentation Foundation (WPF) application is a common rehosting scenario for Workflow Designer.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a2bb6-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a2bb6-106">In This Section</span></span>
 [<span data-ttu-id="a2bb6-107">Tâche 1 : Créer une nouvelle application Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a2bb6-107">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)

 [<span data-ttu-id="a2bb6-108">Tâche 2 : Héberger le concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="a2bb6-108">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)

 [<span data-ttu-id="a2bb6-109">Tâche 3 : Créer les volets Toolbox et PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="a2bb6-109">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)

 [<span data-ttu-id="a2bb6-110">Prise en charge des nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de flux de travail réhébergé</span><span class="sxs-lookup"><span data-stu-id="a2bb6-110">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](wf-features-in-the-rehosted-workflow-designer.md)

## <a name="see-also"></a><span data-ttu-id="a2bb6-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2bb6-111">See also</span></span>

- [<span data-ttu-id="a2bb6-112">Personnalisation de l’expérience de conception de workflow</span><span class="sxs-lookup"><span data-stu-id="a2bb6-112">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
