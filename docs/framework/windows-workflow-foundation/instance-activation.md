---
title: Activation d'instance
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: 5e0d5a91a0f0ccc02d13ef96c3470da1942cc520
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348244"
---
# <a name="instance-activation"></a>Activation d'instance
Le magasin d’instances de workflow SQL exécute une tâche interne qui se réveille régulièrement et détecte les instances de workflow exécutables ou activables dans la base de données de persistance. En cas de détection d'une instance de workflow exécutable, il avertit l'hôte de workflow capable d'activer l'instance. En cas de détection d'une instance de workflow activable, il avertit un hôte générique qui active un hôte de workflow qui, à son tour, exécute l'instance de workflow. Les sections suivantes de cette rubrique décrivent en détail le processus d'activation d'instance.  
  
## <a name="RunnableSection"></a> Détection et activation d’Instances de Workflow exécutables  
 Le Store d’Instance de Workflow SQL considère comme une instance de workflow *exécutable* si l’instance n’est pas dans l’état suspendu ou l’état terminé et satisfait les conditions suivantes :  
  
- L'instance est déverrouillée et a un minuteur en attente qui a expiré.  
  
- L'instance a un verrou périmé.  
  
- L’instance est déverrouillée et son état est **lors de l’exécution**.  
  
 Lorsqu'il détecte une instance exécutable, le magasin d'instances de workflow SQL déclenche l'objet <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>. Ensuite, le SqlWorkflowInstanceStore cesse de surveiller jusqu'à ce que l'objet <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> soit appelé une fois sur le magasin.  
  
 Un hôte de workflow qui s'est abonné à l'objet <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> et capable de charger l'instance exécute l'objet <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> par rapport au magasin d'instances pour charger l'instance en mémoire. Un hôte de workflow est considéré comme capable de charger une instance de workflow si l’hôte et l’instance ont les propriétés de métadonnées **WorkflowServiceType** défini sur la même valeur.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Détection et activation d'instances de workflow activables  
 Une instance de workflow est considérée comme *activable* si l’instance est exécutable et qu’aucun hôte de flux de travail qui est capable de charger l’instance n’est en cours d’exécution sur l’ordinateur. Consultez « Détection et activation d'instances de workflow exécutables », ci-dessus, pour obtenir la définition d'une instance de workflow exécutable.  
  
 Lorsque le magasin d'instances de workflow SQL détecte une instance de workflow activable dans la base de données, il déclenche l'objet <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent>. Ensuite, le SqlWorkflowInstanceStore cesse de surveiller jusqu'à ce que l'objet <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> soit appelé une fois sur le magasin.  
  
 Lorsqu'un hôte générique qui s'est abonné à l'objet <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> reçoit l'événement, il exécute l'objet <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> par rapport au magasin d'instances pour obtenir des paramètres d'activation nécessaires à la création d'un hôte de workflow. L'hôte générique utilise ces paramètres d'activation pour créer un hôte de workflow qui, à son tour, charge et exécute l'instance de service exécutable.  
  
## <a name="generic-hosts"></a>Hôtes génériques  
 Un hôte générique est un ordinateur hôte avec la valeur de la propriété de métadonnées **WorkflowServiceType** pour les hôtes génériques est définie sur **WorkflowServiceType.Any** pour indiquer qu’il peut gérer n’importe quel type de flux de travail. Un hôte générique a un paramètre XName nommé **ActivationType**.  
  
 Actuellement, le Store d’Instance de Workflow SQL prend en charge les hôtes génériques ayant la valeur du paramètre ActivationType définie sur **WAS**. Si le paramètre ActivationType n'est pas défini sur WAS, le magasin d'instances de workflow SQL lève un objet <xref:System.Runtime.DurableInstancing.InstancePersistenceException>. Le Service de gestion de flux de travail qui est fourni avec les fonctionnalités d’hébergement de Windows Server AppFabric est un hôte générique dont le type d’activation **WAS**.  
  
 Pour l'activation WAS, un hôte générique requiert un jeu de paramètres d'activation pour dériver l'adresse de point de terminaison à laquelle les nouveaux hôtes peuvent être activés. Les paramètres d’activation pour l’activation WAS sont : nom du site, chemin d’accès vers l’application relatif au site et chemin d’accès vers le service relatif à l’application. Lors de l'exécution de l'objet <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>, le magasin d'instances de workflow SQL stocke ces paramètres d'activation.  
  
## <a name="runnable-instances-detection-period"></a>Période de détection des instances activables  
 Le **période de détection des Instances exécutables** propriété du Store d’Instance de Workflow SQL spécifie la période de temps après lequel le Store d’Instance de Workflow SQL exécute une tâche de détection pour détecter tout workflow exécutable ou activable instances dans la base de données de persistance issue du cycle de détection précédent. Consultez [période de détection des Instances exécutables](runnable-instances-detection-period.md) pour plus d’informations sur cette propriété.
