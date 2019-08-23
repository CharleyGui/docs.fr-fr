---
title: Workflows procéduraux
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: d1edd73b2276d0a3918b61c8da2d04769d09e7c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956116"
---
# <a name="procedural-workflows"></a><span data-ttu-id="b6e5d-102">Workflows procéduraux</span><span class="sxs-lookup"><span data-stu-id="b6e5d-102">Procedural Workflows</span></span>
<span data-ttu-id="b6e5d-103">Les workflows procéduraux utilisent des méthodes de contrôle de flux semblables à ceux recherchés dans les langages de procédures.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-103">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="b6e5d-104">Ces constructions comprennent notamment `While` et `If`.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-104">These constructs include `While` and `If`.</span></span> <span data-ttu-id="b6e5d-105">Ces workflows peuvent être composés librement à l'aide d'autres activités de contrôle de flux telles que <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-105">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="b6e5d-106">Contrôle du flux d'exécution</span><span class="sxs-lookup"><span data-stu-id="b6e5d-106">Controlling Execution Flow</span></span>  
 <span data-ttu-id="b6e5d-107">La bibliothèque d'activité de workflow a des activités pour modéliser la plupart des méthodes de contrôle de flux utilisé dans les langages de procédures.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-107">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="b6e5d-108">Elles incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="b6e5d-108">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="b6e5d-109">Pour utiliser des activités de contrôle de Flow, faites-les glisser de la boîte à outils d' **activité** vers une activité composite à l’intérieur de la fenêtre du concepteur.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-109">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6e5d-110">Si vous utilisez les fonctionnalités d’hébergement de Windows Server AppFabric pour héberger des flux de travail sur une batterie de serveurs Web, AppFabric déplace les instances entre les différents serveurs AppFabric.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-110">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="b6e5d-111">Cela nécessite que les ressources puissent être partagées entre tous les nœuds.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-111">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="b6e5d-112">Aucune des activités de workflow .NET 4 par défaut ne contient des opérations qui ont accès à des ressources locales.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-112">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="b6e5d-113">Comme AppFabric n'offre aucun mécanisme pour marquer un workflow comme étant immuable, un développeur ne doit pas créer d'activités personnalisées qui échouent lorsqu'un workflow est déplacé.</span><span class="sxs-lookup"><span data-stu-id="b6e5d-113">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e5d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6e5d-114">See also</span></span>

- [<span data-ttu-id="b6e5d-115">Workflows d’organigramme</span><span class="sxs-lookup"><span data-stu-id="b6e5d-115">Flowchart Workflows</span></span>](flowchart-workflows.md)
