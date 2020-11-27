---
title: Options pour la création d'activités dans WF
ms.date: 03/30/2017
ms.assetid: b9061f5f-12c3-47f0-adbe-1330e2714c94
ms.openlocfilehash: e80750b3865a21d072f45b0245ae114660012e66
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289202"
---
# <a name="activity-authoring-options-in-wf"></a>Options pour la création d'activités dans WF

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] fournit plusieurs options pour créer des activités personnalisées. Le choix de la méthode à utiliser pour créer une activité donnée dépend de quelles fonctionnalités d’exécution sont nécessaires.  
  
## <a name="deciding-which-base-activity-class-to-use-for-authoring-custom-activities"></a>Choix de la classe d'activité de base à utiliser pour créer des activités personnalisées  

 Le tableau suivant répertorie les fonctionnalités disponibles dans les classes de base d'activités personnalisées.  
  
|Classe d'activité de base|Fonctionnalités disponibles|  
|-------------------------|------------------------|  
|<xref:System.Activities.Activity>|Compose des groupes d'activités fournies par le système et personnalisées dans une activité composite.|  
|<xref:System.Activities.CodeActivity>|Implémente les fonctionnalités impératives en fournissant une méthode <xref:System.Activities.CodeActivity%601.Execute%2A> qui peut être remplacée. Donne également accès au suivi, aux variables et aux arguments.|  
|<xref:System.Activities.NativeActivity>|Fournit toutes les fonctionnalités de <xref:System.Activities.CodeActivity>, plus celles nécessaires pour abandonner l'exécution d'une activité, annuler l'exécution d'une activité enfant, utiliser des signets, ainsi que planifier des activités, des actions d'activité et des fonctions.|  
|<xref:System.Activities.DynamicActivity>|Fournit une approche DOM pour créer des activités qui servent d'interface avec le concepteur WF et les fonctionnalités d'exécution via <xref:System.ComponentModel.ICustomTypeDescriptor>, ce qui permet de créer d'autres activités sans définir de nouveaux types.|  
  
## <a name="authoring-activities-using-activity"></a>Création d'activités à l'aide d'Activity  

 Les activités qui dérivent de <xref:System.Activities.Activity> composent les fonctionnalités en assemblant d'autres activités existantes. Ces activités peuvent être des activités personnalisées existantes et des activités de la bibliothèque d'activités [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]. Assembler ces activités est la méthode la plus simple pour créer des fonctionnalités personnalisées. Cette approche est généralement utilisée pour la création de workflows dans un environnement de conception visuelle.  
  
## <a name="authoring-activities-using-codeactivity-or-asynccodeactivity"></a>Activités de création à l'aide de CodeActivity ou AsyncCodeActivity  

 Les activités qui dérivent de <xref:System.Activities.CodeActivity> ou <xref:System.Activities.AsyncCodeActivity> peuvent implémenter les fonctionnalités impératives en remplaçant la méthode <xref:System.Activities.CodeActivity%601.Execute%2A> par un code impératif personnalisé. Le code personnalisé est exécuté lorsque l'activité est exécutée par le runtime. Les activités créées de cette façon ont accès aux fonctionnalités personnalisées, mais elles n’ont pas accès à toutes les fonctionnalités d’exécution, notamment celles offrant un accès total à l’environnement d’exécution, la capacité de planifier des activités enfants, la création de signets ou la prise en charge des méthodes Cancel ou Abort. Lorsqu'un <xref:System.Activities.CodeActivity> est exécuté, il a accès à une version réduite de l'environnement d'exécution (via la classe <xref:System.Activities.CodeActivityContext> ou <xref:System.Activities.AsyncCodeActivityContext>). Les activités créées à l'aide de <xref:System.Activities.CodeActivity> ont accès à la résolution des arguments et des variables, aux extensions et au suivi. La planification d'activités asynchrones peut être réalisée à l'aide de <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="authoring-activities-using-nativeactivity"></a>Création d'activités à l'aide de NativeActivity  

 Les activités qui dérivent de <xref:System.Activities.NativeActivity>, comme celles qui dérivent de <xref:System.Activities.CodeActivity>, créent des fonctionnalités impératives en remplaçant la méthode <xref:System.Activities.NativeActivity.Execute%2A>, mais elles ont également accès à toutes les fonctionnalités d'exécution de workflow via le contexte <xref:System.Activities.NativeActivityContext> passé dans la méthode <xref:System.Activities.NativeActivity.Execute%2A>. Ce contexte prend en charge la planification et l'annulation des activités enfants, l'exécution des objets <xref:System.Activities.ActivityAction> et objets <xref:System.Activities.ActivityFunc%601>, la circulation des transactions dans un workflow, l'appel de processus asynchrones, l'annulation et l'abandon de l'exécution, l'accès aux propriétés d'exécution et aux extensions, ainsi que l'utilisation des signets (descripteurs pour reprendre les workflows mis en pause).  
  
## <a name="authoring-activities-using-dynamicactivity"></a>Création d'activités à l'aide de DynamicActivity  

 Contrairement aux trois autres types d'activité, les nouvelles fonctionnalités ne sont pas créées en dérivant de nouveaux types de <xref:System.Activities.DynamicActivity> (la classe est scellée), mais plutôt en assemblant les fonctionnalités dans les propriétés <xref:System.Activities.DynamicActivity.Properties%2A> et <xref:System.Activities.DynamicActivity.Implementation%2A> à l'aide d'un modèle DOM (Document Object Model) de l'activité.  
  
## <a name="authoring-activities-that-return-a-result"></a>Création d'activités qui retournent un résultat  

 De nombreuses activités doivent retourner un résultat après leur exécution. Pour ce faire, il est possible de toujours définir un <xref:System.Activities.OutArgument%601> personnalisé sur une activité ; il est néanmoins recommandé d'utiliser à la place <xref:System.Activities.Activity%601>, ou de dériver de <xref:System.Activities.CodeActivity%601> ou <xref:System.Activities.NativeActivity%601>. Chacune de ces classes de base a un <xref:System.Activities.OutArgument%601> nommé Result (Résultat) que votre activité peut utiliser comme valeur de retour. Les activités qui retournent un résultat ne doivent être utilisées que si un seul résultat doit être retourné à partir d'une activité ; si plusieurs résultats doivent être retournés, des membres <xref:System.Activities.OutArgument%601> distincts doivent être utilisés à la place.
