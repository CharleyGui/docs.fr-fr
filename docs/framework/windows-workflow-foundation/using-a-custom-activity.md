---
title: Utilisation d'une activité personnalisée
ms.date: 03/30/2017
ms.assetid: 8f356419-681a-4175-ae93-878eee970249
ms.openlocfilehash: 6ca67ef7a8c4330d0182e960fc3fdcce656976a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962221"
---
# <a name="using-a-custom-activity"></a>Utilisation d'une activité personnalisée
Les activités qui dérivent de la classe <xref:System.Activities.Activity> ou de ses sous-classes peuvent être composées de plus grands workflows, ou créées directement dans le code. Cette rubrique explique comment utiliser des activités personnalisées dans les workflows créés dans le code ou dans le concepteur.  
  
> [!NOTE]
> Les activités personnalisées peuvent être utilisées dans le même projet que celui dans lequel elles sont définies, à condition que l’activité personnalisée et l’activité qui l’utilise soient compilées (par exemple, chargées par un type d’instanciation généré par le processus de génération) si l’activité de référence est chargée. dynamiquement (par exemple, à l’aide de ActivityXAMLServices), l’assembly référencé doit être placé dans un autre projet ou le code XAML généré par le concepteur doit être modifié manuellement pour permettre cela.  
  
#### <a name="using-a-custom-activity-to-a-workflow-project"></a>Utilisation d'une activité personnalisée dans un projet de workflow  
  
1. Ajoutez une référence du projet hôte au projet de bibliothèque d'activités qui contient l'activité personnalisée.  
  
2. Générez la solution.  
  
3. Pour utiliser l'activité personnalisée dans le concepteur, recherchez l'activité personnalisée dans la boîte à outils, puis faites glisser l'activité sur l'aire du concepteur.  
  
4. Pour utiliser l'activité personnalisée dans le code, ajoutez une instruction Using qui fait référence au projet d'activité personnalisée, puis passez une nouvelle instance de l'activité à <xref:System.Activities.WorkflowInvoker.Invoke%2A>.
