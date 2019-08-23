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
# <a name="procedural-workflows"></a>Workflows procéduraux
Les workflows procéduraux utilisent des méthodes de contrôle de flux semblables à ceux recherchés dans les langages de procédures. Ces constructions comprennent notamment `While` et `If`. Ces workflows peuvent être composés librement à l'aide d'autres activités de contrôle de flux telles que <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Contrôle du flux d'exécution  
 La bibliothèque d'activité de workflow a des activités pour modéliser la plupart des méthodes de contrôle de flux utilisé dans les langages de procédures. Elles incluent notamment :  
  
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

- [Workflows d’organigramme](flowchart-workflows.md)
