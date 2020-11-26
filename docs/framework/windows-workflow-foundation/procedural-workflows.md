---
title: Workflows procéduraux
description: Dans Workflow Foundation, les flux de travail de procédure utilisent des méthodes de contrôle de flux similaires à celles trouvées dans les langages de procédure.
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 13d1b5e55b84687e2a78db1a94317b8b1e33328c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246028"
---
# <a name="procedural-workflows"></a>Workflows procéduraux

Les workflows procéduraux utilisent des méthodes de contrôle de flux semblables à ceux recherchés dans les langages de procédures. Ces constructions comprennent notamment `While` et `If`. Ces workflows peuvent être composés librement à l'aide d'autres activités de contrôle de flux telles que <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Contrôle du flux d'exécution  

 La bibliothèque d'activité de workflow a des activités pour modéliser la plupart des méthodes de contrôle de flux utilisé dans les langages de procédures. notamment :  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 Pour utiliser des activités de contrôle de Flow, faites-les glisser de la boîte à outils d' **activité** vers une activité composite à l’intérieur de la fenêtre du concepteur.  
  
> [!NOTE]
> Si vous utilisez les fonctionnalités d’hébergement de Windows Server AppFabric pour héberger des flux de travail sur une batterie de serveurs Web, AppFabric déplace les instances entre les différents serveurs AppFabric. Cela nécessite que les ressources puissent être partagées entre tous les nœuds.  Aucune des activités de workflow .NET 4 par défaut ne contient des opérations qui ont accès à des ressources locales. Comme AppFabric n'offre aucun mécanisme pour marquer un workflow comme étant immuable, un développeur ne doit pas créer d'activités personnalisées qui échouent lorsqu'un workflow est déplacé.  
  
## <a name="see-also"></a>Voir aussi

- [Workflows d'organigramme](flowchart-workflows.md)
