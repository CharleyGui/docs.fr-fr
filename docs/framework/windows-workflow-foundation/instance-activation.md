---
title: Activation d'instance
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: 1fd30d9d440c06c03e726ed1f1ddbebb0d5f7e8c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279933"
---
# <a name="instance-activation"></a>Activation d'instance

Le magasin d’instances de workflow SQL exécute une tâche interne qui se réveille régulièrement et détecte les instances de workflow exécutables ou activables dans la base de données de persistance. En cas de détection d'une instance de workflow exécutable, il avertit l'hôte de workflow capable d'activer l'instance. En cas de détection d'une instance de workflow activable, il avertit un hôte générique qui active un hôte de workflow qui, à son tour, exécute l'instance de workflow. Les sections suivantes de cette rubrique décrivent en détail le processus d'activation d'instance.  
  
## <a name="detecting-and-activating-runnable-workflow-instances"></a><a name="RunnableSection"></a> Détection et activation d’instances de workflow exécutables  

 Le magasin d’instances de workflow SQL prend en compte une instance de workflow *exécutable* si l’instance n’est pas dans l’état suspendu ou l’état terminé et satisfait les conditions suivantes :  
  
- L'instance est déverrouillée et a un minuteur en attente qui a expiré.  
  
- L'instance a un verrou périmé.  
  
- L’instance est déverrouillée et son état est en **cours d’exécution**.  
  
 Lorsqu'il détecte une instance exécutable, le magasin d'instances de workflow SQL déclenche l'objet <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>. Ensuite, le SqlWorkflowInstanceStore cesse de surveiller jusqu'à ce que l'objet <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> soit appelé une fois sur le magasin.  
  
 Un hôte de workflow qui s'est abonné à l'objet <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> et capable de charger l'instance exécute l'objet <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> par rapport au magasin d'instances pour charger l'instance en mémoire. Un hôte de flux de travail est considéré comme apte à charger une instance de flux de travail si l’hôte et l’instance ont la propriété de métadonnées **WorkflowServiceType** définie sur la même valeur.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Détection et activation d'instances de workflow activables  

 Une instance de workflow est *considérée comme* pouvant être activée si l’instance est exécutable et qu’il n’existe aucun hôte de flux de travail capable de charger l’instance s’exécute sur l’ordinateur. Consultez « Détection et activation d'instances de workflow exécutables », ci-dessus, pour obtenir la définition d'une instance de workflow exécutable.  
  
 Lorsque le magasin d'instances de workflow SQL détecte une instance de workflow activable dans la base de données, il déclenche l'objet <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent>. Ensuite, le SqlWorkflowInstanceStore cesse de surveiller jusqu'à ce que l'objet <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> soit appelé une fois sur le magasin.  
  
 Lorsqu'un hôte générique qui s'est abonné à l'objet <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> reçoit l'événement, il exécute l'objet <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> par rapport au magasin d'instances pour obtenir des paramètres d'activation nécessaires à la création d'un hôte de workflow. L'hôte générique utilise ces paramètres d'activation pour créer un hôte de workflow qui, à son tour, charge et exécute l'instance de service exécutable.  
  
## <a name="generic-hosts"></a>Hôtes génériques  

 Un hôte générique est un hôte dont la valeur de la propriété de métadonnées **WorkflowServiceType** pour les hôtes génériques est définie sur **WorkflowServiceType. any** pour indiquer qu’il peut gérer n’importe quel type de Workflow. Un hôte générique a un paramètre XName nommé **ActivationType**.  
  
 Actuellement, le magasin d’instances de workflow SQL prend en charge les hôtes génériques avec la valeur du paramètre ActivationType définie sur **was**. Si le paramètre ActivationType n'est pas défini sur WAS, le magasin d'instances de workflow SQL lève un objet <xref:System.Runtime.DurableInstancing.InstancePersistenceException>. Le service de gestion de flux de travail fourni avec les fonctionnalités d’hébergement de Windows Server AppFabric est un hôte générique dont le type d’activation est défini sur **was**.  
  
 Pour l'activation WAS, un hôte générique requiert un jeu de paramètres d'activation pour dériver l'adresse de point de terminaison à laquelle les nouveaux hôtes peuvent être activés. Les paramètres d’activation pour l’activation WAS sont : nom du site, chemin d’accès vers l’application relatif au site et chemin d’accès vers le service relatif à l’application. Lors de l'exécution de l'objet <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>, le magasin d'instances de workflow SQL stocke ces paramètres d'activation.  
  
## <a name="runnable-instances-detection-period"></a>Période de détection des instances activables  

 La propriété **période de détection des instances exécutables** du magasin d’instances de workflow SQL spécifie la période après laquelle le magasin d’instances de workflow SQL exécute une tâche de détection pour détecter toutes les instances de workflow exécutables ou activables dans la base de données de persistance après le cycle de détection précédent. Pour plus d’informations sur cette propriété, consultez [période de détection des instances exécutables](runnable-instances-detection-period.md) .
