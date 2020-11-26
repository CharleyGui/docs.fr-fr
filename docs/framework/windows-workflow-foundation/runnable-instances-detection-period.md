---
title: Période de détection des instances activables
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: aefde2726bb2ccc15f9e68009e5e141602b13b10
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245768"
---
# <a name="runnable-instances-detection-period"></a>Période de détection des instances activables

Le magasin d’instances de workflow SQL exécute une tâche interne qui se réveille régulièrement et détecte les instances exécutables ou activables dans la base de données de persistance. La propriété **période de détection des instances exécutables** du magasin d’instances de workflow SQL spécifie la période après laquelle le magasin d’instances de workflow SQL exécute une tâche de détection pour détecter toutes les instances de workflow exécutables ou activables dans la base de données de persistance après le cycle de détection précédent.  
  
 La définition d'un intervalle plus court pour cette propriété réduit le délai entre l'expiration d'un minuteur associé à une instance de workflow et la signalisation de l'événement, ainsi que le chargement subséquent de l'instance. Toutefois, cela augmente également la charge de traitement sur un hôte et peut ne pas être souhaitable dans les scénarios où les minuteurs durables et/ou les échecs d'hôte sont rares. La propriété possède le type TimeSpan et sa valeur suit le format : hh:mm:ss. La valeur minimale de cette propriété est 00:00:01 et sa valeur par défaut 00:00:05.  
  
 Pour plus d’informations sur la détection et l’activation des instances de workflow exécutables et activables, consultez [activation d’instance](instance-activation.md).
