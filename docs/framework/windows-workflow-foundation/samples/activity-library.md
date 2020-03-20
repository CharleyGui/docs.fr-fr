---
title: Bibliothèque d'activités
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142899"
---
# <a name="activity-library"></a>Bibliothèque d'activités
Cette section contient des échantillons qui démontrent des activités personnalisées avancées dans Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>Dans cette section

 [Activité personnalisée SendMail](sendmail-custom-activity.md)  
 Montre comment créer une activité personnalisée dérivée de <xref:System.Activities.AsyncCodeActivity> pour envoyer du courrier à l'aide de SMTP afin de l'utiliser dans une application de workflow.  
  
 [ParallelForEach limité](throttled-parallel-foreach.md)  
 Montre comment l’activité `ThrottleParallelForEach` est semblable à l’activité <xref:System.Activities.Statements.ParallelForEach%601> hormis le seul fait qu’elle permet la définition d’un facteur de concurrence pour restreindre le nombre de branches simultanées à exécuter.
  
 [Activités d’accès aux bases de données](database-access-activities.md)  
 Démontre comment créer des activités qui permettent aux bases de données d’accéder à des bases de données de récupérer ou de modifier des informations et [d’utiliser ADO.NET](../../data/adonet/index.md) pour accéder à la base de données.  
  
 [Activité de stratégie externalisée dans .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)  
 Démontre comment l’activité ExternalizedPolicy4 permet d’exécuter la Fondation Windows Workflow existante dans .NET <xref:System.Workflow.Activities.Rules.RuleSet> Framework 3.5 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 3.5) objets dans Windows Workflow Foundation en (WF 4.5) directement en utilisant le moteur de règles qui est expédié dans WF 3.5.
  
 [ForEach non générique](non-generic-foreach.md)  
 Montre comment créer une version non générique de l'activité <xref:System.Activities.Statements.ForEach%601>.  
  
 [ParallelForEach non générique](non-generic-parallelforeach.md)  
 Montre comment créer une version non générique de l'activité <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 [Obtenir WorkflowInstanceId](get-workflowinstanceid.md)  
 Montre comment utiliser l'activité personnalisée `GetWorkflowInstanceId` pour retourner l'ID d'instance de workflow.
