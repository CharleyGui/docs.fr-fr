---
title: Bibliothèque d'activités
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: ce65bf8e7adad6acefd7aac6d69c3f836b94be29
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094694"
---
# <a name="activity-library"></a>Bibliothèque d'activités
Cette section contient des exemples qui illustrent des activités personnalisées avancées dans Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>Dans cette section

 [Activité personnalisée SendMail](sendmail-custom-activity.md)  
 Montre comment créer une activité personnalisée dérivée de <xref:System.Activities.AsyncCodeActivity> pour envoyer du courrier à l'aide de SMTP afin de l'utiliser dans une application de workflow.  
  
 [ParallelForEach limité](throttled-parallel-foreach.md)  
 Montre comment l’activité `ThrottleParallelForEach` est semblable à l’activité <xref:System.Activities.Statements.ParallelForEach%601> hormis le seul fait qu’elle permet la définition d’un facteur de concurrence pour restreindre le nombre de branches simultanées à exécuter.
  
 [Activités d’accès aux bases de données](database-access-activities.md)  
 Montre comment créer des activités qui permettent d’accéder aux bases de données afin de récupérer ou de modifier des informations et d’utiliser [ADO.net](../../data/adonet/index.md) pour accéder à la base de données.  
  
 [Activité de stratégie externalisée dans .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)  
 Montre comment l’activité ExternalizedPolicy4 permet d’exécuter des Windows Workflow Foundation existants dans .NET Framework 3,5 (WF 3,5) <xref:System.Workflow.Activities.Rules.RuleSet> objets dans Windows Workflow Foundation dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4,5) directement à l’aide du moteur de règles fourni dans WF 3,5. 
  
 [ForEach non générique](non-generic-foreach.md)  
 Montre comment créer une version non générique de l'activité <xref:System.Activities.Statements.ForEach%601>.  
  
 [ParallelForEach non générique](non-generic-parallelforeach.md)  
 Montre comment créer une version non générique de l'activité <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 [Obtenir WorkflowInstanceId](get-workflowinstanceid.md)  
 Montre comment utiliser l'activité personnalisée `GetWorkflowInstanceId` pour retourner l'ID d'instance de workflow.
