---
title: Activités de l'ordinateur d'état dans WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: dd0bfae1f24ecd9f98c0a2f04265581f880202a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261720"
---
# <a name="state-machine-activities-in-wf"></a>Activités de l'ordinateur d'état dans WF

.NET Framework 4,5 fournit plusieurs activités et concepteurs d’activités fournis par le système pour la création de workflows d’ordinateur d’État.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Exécute des activités contenues à l'aide du modèle de machine à états familier.|  
|<xref:System.Activities.Statements.State>|Représente un état dans un ordinateur d'état.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Représente un état d'arrêt au sein d'une machine à états. <xref:System.Activities.Core.Presentation.FinalState> est un concepteur d'activités qui en cas d'utilisation crée un <xref:System.Activities.Statements.State> préconfiguré comme état d'arrêt. Pour plus d’informations, consultez [Concepteur d’activités FinalState](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|Représente la transition entre deux états. Il n’y a aucun élément de **boîte à outils** pour <xref:System.Activities.Statements.Transition> ; les transitions sont créées sur le concepteur de workflow en faisant glisser et en déposant une ligne entre deux États, ou en déposant un État sur les triangles qui apparaissent lorsqu’un État est pointé sur un autre. Pour plus d’informations, consultez [Concepteur d’activités de transition](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Voir aussi

- [Didacticiel de mise en route](getting-started-tutorial.md)
