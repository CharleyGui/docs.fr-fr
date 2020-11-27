---
title: Options d'hébergement de workflow
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 8ddb83f068eab8480bacc8b80bc5d44b7755fa59
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293778"
---
# <a name="workflow-hosting-options"></a>Options d'hébergement de workflow

La plupart des exemples de Windows Workflow Foundation (WF) utilisent des workflows hébergés dans une application console, mais ce scénario n’est pas réaliste pour les flux de travail réels. Les flux de travail des applications métier réelles sont hébergés dans des processus persistants, soit un service Windows créé par le développeur, soit une application serveur telle qu’IIS 7,0 ou AppFabric. Les différences entre ces approches sont les suivantes.

## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hébergement de workflows dans IIS avec Windows AppFabric

IIS avec AppFabric est l'hôte par défaut pour les workflows. L'application hôte de workflows utilisant AppFabric est WAS (Windows Activation Services), qui supprime la dépendance de HTTP sur IIS uniquement.

## <a name="hosting-workflows-in-iis-alone"></a>Hébergement de workflows dans IIS uniquement

L’utilisation de IIS 7,0 seul n’est pas recommandée, car il existe des outils de gestion et de surveillance disponibles avec AppFabric qui facilitent la maintenance des applications en cours d’exécution. Les workflows doivent uniquement être hébergés dans IIS 7,0 uniquement si des problèmes d’infrastructure se posent lors du passage à AppFabric.

> [!WARNING]
> IIS 7,0 recycle périodiquement les pools d’applications pour diverses raisons. Lorsqu'un pool d'applications est recyclé, IIS cesse de recevoir des messages de l'ancien pool, et instancie un pool d'applications pour recevoir de nouvelles demandes. Si un workflow continue de fonctionner après l’envoi d’une réponse, IIS 7,0 ne tient pas compte du travail effectué et peut recycler le pool d’applications d’hébergement. Dans ce cas, le flux de travail est abandonné et les services de suivi enregistrent un message [1004-WorkflowInstanceAborted](1004-workflowinstanceaborted.md) avec un champ raison vide.
>
> Si la persistance est utilisée, l'hôte doit explicitement redémarrer les instances interrompues à partir du dernier point de persistance.
>
> Si AppFabric est utilisé, le service de gestion de workflow reprend en fin de compte le workflow à partir du dernier point correct de persistance si la persistance est utilisée. Si aucune persistance n’est utilisée, et le workflow exécute des opérations en dehors d’un modèle de requête/réponse, des données seront perdues lors de l’interruption du workflow.

## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hébergement d'un workflow dans un service Windows personnalisé

Créer un service de workflow personnalisé pour héberger le workflow nécessite que le développeur duplique nombre des fonctionnalités prêtes à l'emploi fournies par AppFabric, mais offre plus de souplesse avec des fonctionnalités personnalisées. Cette option ne doit être prise en compte que si AppFabric s'avère ne pas être une option.
