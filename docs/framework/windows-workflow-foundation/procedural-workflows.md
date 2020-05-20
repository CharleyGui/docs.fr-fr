---
title: Workflows procéduraux
description: Dans Workflow Foundation, les flux de travail de procédure utilisent des méthodes de contrôle de flux similaires à celles trouvées dans les langages de procédure.
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 97664c1352928e7d05c2ed15fc118dd21474cfc3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421434"
---
# <a name="procedural-workflows"></a><span data-ttu-id="e80e3-103">Workflows procéduraux</span><span class="sxs-lookup"><span data-stu-id="e80e3-103">Procedural Workflows</span></span>
<span data-ttu-id="e80e3-104">Les workflows procéduraux utilisent des méthodes de contrôle de flux semblables à ceux recherchés dans les langages de procédures.</span><span class="sxs-lookup"><span data-stu-id="e80e3-104">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="e80e3-105">Ces constructions comprennent notamment `While` et `If`.</span><span class="sxs-lookup"><span data-stu-id="e80e3-105">These constructs include `While` and `If`.</span></span> <span data-ttu-id="e80e3-106">Ces workflows peuvent être composés librement à l'aide d'autres activités de contrôle de flux telles que <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="e80e3-106">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="e80e3-107">Contrôle du flux d'exécution</span><span class="sxs-lookup"><span data-stu-id="e80e3-107">Controlling Execution Flow</span></span>  
 <span data-ttu-id="e80e3-108">La bibliothèque d'activité de workflow a des activités pour modéliser la plupart des méthodes de contrôle de flux utilisé dans les langages de procédures.</span><span class="sxs-lookup"><span data-stu-id="e80e3-108">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="e80e3-109">Il s’agit des tables suivantes :</span><span class="sxs-lookup"><span data-stu-id="e80e3-109">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="e80e3-110">Pour utiliser des activités de contrôle de Flow, faites-les glisser de la boîte à outils d' **activité** vers une activité composite à l’intérieur de la fenêtre du concepteur.</span><span class="sxs-lookup"><span data-stu-id="e80e3-110">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e80e3-111">Si vous utilisez les fonctionnalités d’hébergement de Windows Server AppFabric pour héberger des flux de travail sur une batterie de serveurs Web, AppFabric déplace les instances entre les différents serveurs AppFabric.</span><span class="sxs-lookup"><span data-stu-id="e80e3-111">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="e80e3-112">Cela nécessite que les ressources puissent être partagées entre tous les nœuds.</span><span class="sxs-lookup"><span data-stu-id="e80e3-112">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="e80e3-113">Aucune des activités de workflow .NET 4 par défaut ne contient des opérations qui ont accès à des ressources locales.</span><span class="sxs-lookup"><span data-stu-id="e80e3-113">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="e80e3-114">Comme AppFabric n'offre aucun mécanisme pour marquer un workflow comme étant immuable, un développeur ne doit pas créer d'activités personnalisées qui échouent lorsqu'un workflow est déplacé.</span><span class="sxs-lookup"><span data-stu-id="e80e3-114">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80e3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e80e3-115">See also</span></span>

- [<span data-ttu-id="e80e3-116">Workflows d’organigramme</span><span class="sxs-lookup"><span data-stu-id="e80e3-116">Flowchart Workflows</span></span>](flowchart-workflows.md)
