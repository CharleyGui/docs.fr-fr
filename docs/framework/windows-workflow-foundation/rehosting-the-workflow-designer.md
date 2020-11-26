---
title: Réhébergement du Workflow Designer
description: Le Concepteur de flux de travail Windows peut être réhébergé dans des environnements en dehors de Visual Studio pour la création, la modification et la surveillance des flux de travail.
ms.date: 03/30/2017
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
ms.openlocfilehash: 8c3a67d0beecdfcf4f99580bb6ec25fea6473718
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245898"
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="93fab-103">Réhébergement du Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="93fab-103">Rehosting the Workflow Designer</span></span>

<span data-ttu-id="93fab-104">Les Concepteur de flux de travail Windows peuvent être réhébergés dans des environnements en dehors de Visual Studio 2012 afin de créer, de modifier et de surveiller des flux de travail.</span><span class="sxs-lookup"><span data-stu-id="93fab-104">The Windows Workflow Designer can be rehosted in environments outside of Visual Studio 2012 for the purposes of creating, modifying, and monitoring workflows.</span></span>

 <span data-ttu-id="93fab-105">Le type <xref:System.Activities.Presentation.WorkflowDesigner> est un wrapper de la zone de dessin, de la grille des propriétés et d'autres éléments, et expose un modèle de programmation de base conçu pour gérer la majorité des scénarios de réhébergement du concepteur.</span><span class="sxs-lookup"><span data-stu-id="93fab-105">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="93fab-106">L’hébergement du <xref:System.Activities.Presentation.WorkflowDesigner> à l’intérieur d’une application Windows Presentation Foundation (WPF) est un scénario de réhébergement courant pour les concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="93fab-106">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a Windows Presentation Foundation (WPF) application is a common rehosting scenario for Workflow Designer.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="93fab-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="93fab-107">In This Section</span></span>

 [<span data-ttu-id="93fab-108">Tâche 1 : créer une application Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="93fab-108">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)

 [<span data-ttu-id="93fab-109">Tâche 2 : héberger le concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="93fab-109">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)

 [<span data-ttu-id="93fab-110">Tâche 3 : créer les volets Toolbox et PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="93fab-110">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)

 [<span data-ttu-id="93fab-111">Prise en charge de nouvelles fonctionnalités Workflow Foundation 4.5 dans le concepteur de workflow réhébergé</span><span class="sxs-lookup"><span data-stu-id="93fab-111">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](wf-features-in-the-rehosted-workflow-designer.md)

## <a name="see-also"></a><span data-ttu-id="93fab-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93fab-112">See also</span></span>

- [<span data-ttu-id="93fab-113">Personnalisation de l'expérience de conception de workflow</span><span class="sxs-lookup"><span data-stu-id="93fab-113">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
