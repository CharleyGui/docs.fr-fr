---
title: Options d'hébergement de workflow
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: b0cd9748c28cd6206e1fedffc5772b2849462dba
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487368"
---
# <a name="workflow-hosting-options"></a>Options d'hébergement de workflow
La plupart des exemples Windows Workflow Foundation (WF) utilisent des workflows hébergés dans une application console, mais ce n’est pas un scénario réaliste pour les workflows réels. Flux de travail dans les applications d’entreprise réelles sera hébergée dans un service Windows créé persistant processus-par le développeur ou une application de serveur telles que IIS 7.0 ou AppFabric. Les différences entre ces approches sont les suivantes.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hébergement de workflows dans IIS avec Windows AppFabric  
 IIS avec AppFabric est l'hôte par défaut pour les workflows. L'application hôte de workflows utilisant AppFabric est WAS (Windows Activation Services), qui supprime la dépendance de HTTP sur IIS uniquement.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Hébergement de workflows dans IIS uniquement  
 À l’aide d’IIS 7.0 uniquement n’est pas recommandé, il existe des outils d’analyse disponibles avec AppFabric qui facilitent la maintenance des applications en cours d’exécution et de gestion. Flux de travail doit être hébergés dans IIS 7.0 uniquement si vous rencontrez des problèmes d’infrastructure avec la migration vers AppFabric.  
  
> [!WARNING]
>  IIS 7.0 recycle périodiquement les pools d’applications pour diverses raisons. Lorsqu'un pool d'applications est recyclé, IIS cesse de recevoir des messages de l'ancien pool, et instancie un pool d'applications pour recevoir de nouvelles demandes. Si un workflow continue de fonctionner après l’envoi d’une réponse, IIS 7.0 ne sera pas connaissance des travaux en cours et peut recycler le pool d’application d’hébergement. Si cela se produit, le workflow s’interrompra, et des services de suivi enregistreront un [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md) message avec un champ de raison vide.  
>   
>  Si la persistance est utilisée, l'hôte doit explicitement redémarrer les instances interrompues à partir du dernier point de persistance.  
>   
>  Si AppFabric est utilisé, le service de gestion de workflow reprend en fin de compte le workflow à partir du dernier point correct de persistance si la persistance est utilisée. Si aucune persistance n’est utilisée, et le workflow exécute des opérations en dehors d’un modèle de requête/réponse, des données seront perdues lors de l’interruption du workflow.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hébergement d'un workflow dans un service Windows personnalisé  
 Créer un service de workflow personnalisé pour héberger le workflow nécessite que le développeur duplique nombre des fonctionnalités prêtes à l'emploi fournies par AppFabric, mais offre plus de souplesse avec des fonctionnalités personnalisées. Cette option ne doit être prise en compte que si AppFabric s'avère ne pas être une option.
