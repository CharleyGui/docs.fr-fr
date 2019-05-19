---
title: Vue d'ensemble de Windows Workflow
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: 285ab75f7f67bbb9ffa18367eff126c04227f193
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876142"
---
# <a name="windows-workflow-overview"></a>Vue d'ensemble de Windows Workflow
Un flux de travail est un ensemble d’unités élémentaires appelé *activités* qui sont stockés sous la forme d’un modèle qui décrit un processus réel. Les workflows offrent un moyen de décrire l'ordre d'exécution et les relations de dépendance entre des éléments de travail de courte ou longue durée. Ce travail s'effectue à travers le modèle de démarrage à l'arrêt et les activités peuvent être exécutées par des utilisateurs ou par les fonctions système.  
  
## <a name="workflow-run-time-engine"></a>Moteur d'exécution de workflow  
 Chaque instance de workflow en cours d'exécution est créée et gérée par un moteur d'exécution in-process avec lequel le processus hôte interagit par le biais de l'un des éléments suivants :  
  
- Un <xref:System.Activities.WorkflowInvoker>, qui appelle le workflow comme une méthode.  
  
- Un <xref:System.Activities.WorkflowApplication> pour contrôler explicitement l'exécution d'une instance de workflow unique.  
  
- Un <xref:System.ServiceModel.WorkflowServiceHost> pour les interactions basées sur des messages dans les scénarios à plusieurs instances.  
  
 Chacune de ces classes encapsule le runtime de l'activité principale représenté en tant que <xref:System.Activities.ActivityInstance> responsable de l'exécution de l'activité. Un domaine d'application peut comporter plusieurs objets <xref:System.Activities.ActivityInstance> fonctionnant simultanément.  
  
 Chacun des trois objets d’interaction hôtes précédents est créé à partir d’une arborescence d’activités appelée programme de workflow. À l’aide de ces types ou un hôte personnalisé qui encapsule <xref:System.Activities.ActivityInstance>, flux de travail peut être exécutée à l’intérieur de n’importe quel processus Windows, y compris les applications de console basée sur les formulaires des applications, les Services Windows, des sites Web ASP.NET et Windows Communication Foundation (WCF) Services.  
  
 ![Composants de flux de travail dans le processus hôte](./media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Composants de workflow dans le processus hôte  
  
## <a name="interaction-between-workflow-components"></a>Interaction entre composants de workflow  
 Le diagramme suivant montre comment les composants de workflow interagissent les uns avec les autres.  
  
 ![Diagramme illustrant l’interaction des composants de flux de travail.](./media/overview/workflow-component-interatction.gif)  
  
 Dans le diagramme précédent, la méthode <xref:System.Activities.WorkflowInvoker.Invoke%2A> de classe <xref:System.Activities.WorkflowInvoker> est utilisée pour appeler plusieurs instances de workflow. <xref:System.Activities.WorkflowInvoker> est utilisé pour les workflows légers ne nécessitant pas de gestion à partir de l'hôte ; les workflows qui nécessitent d'être gérés à partir de l'hôte (tel qu'une reprise <xref:System.Activities.Bookmark>) doivent être exécutés avec <xref:System.Activities.WorkflowApplication.Run%2A> à la place. Il n'est pas nécessaire d'attendre qu'une instance de workflow soit terminée avant d'en appeler une autre ; le moteur de runtime prend en charge plusieurs instances de workflow simultanément.  Les workflows appelés sont les suivants :  
  
- Une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> enfant. <xref:System.Activities.Variable> de l'activité parente est lié à un <xref:System.Activities.InArgument> de l'activité enfant. Pour plus d’informations sur les variables, arguments et la liaison, consultez [Variables et Arguments](variables-and-arguments.md).  
  
- Une activité personnalisée appelée `ReadLine`. Un <xref:System.Activities.OutArgument> de l'activité `ReadLine` est retourné à la méthode  <xref:System.Activities.WorkflowInvoker.Invoke%2A> appelante.  
  
- Une activité personnalisée qui dérive de la classe abstraite <xref:System.Activities.CodeActivity>. Le <xref:System.Activities.CodeActivity> peut accéder aux fonctionnalités d’exécution (telles que le suivi et les propriétés) à l’aide du <xref:System.Activities.CodeActivityContext> qui est disponible en tant que paramètre de la méthode <xref:System.Activities.CodeActivity.Execute%2A>. Pour plus d’informations sur ces fonctionnalités d’exécution, consultez [suivi et traçage de Workflow](workflow-tracking-and-tracing.md) et [propriétés d’exécution de flux de travail](workflow-execution-properties.md).  
  
## <a name="see-also"></a>Voir aussi

- [BizTalk Server 2006 ou WF ? Choix de l’outil de Workflow approprié pour votre projet](https://go.microsoft.com/fwlink/?LinkId=154901)
