---
title: Stratégies pour la gestion d’une défaillance partielle
description: Découvrez plusieurs stratégies pour gérer normalement les défaillances partielles.
ms.date: 10/16/2018
ms.openlocfilehash: e96fe99ab44b924460e01abaad30aa3e2432117a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68674506"
---
# <a name="strategies-to-handle-partial-failure"></a>Stratégies pour gérer une défaillance partielle

Les stratégies pour la gestion des défaillances partielles sont les suivantes.

**Utilisez la communication asynchrone (par exemple, la communication basée sur les messages) sur les microservices internes**. Nous vous conseillons vivement de ne pas créer de longues chaînes d’appels HTTP synchrones entre les microservices internes, car cette conception incorrecte peut devenir la cause principale de graves pannes. Au contraire, à l’exception des communications front-end entre les applications clientes et le premier niveau des microservices ou les passerelles d’API affinées, nous vous recommandons d’utiliser une communication asynchrone (basée sur les messages) uniquement après le premier cycle de requête/réponse, entre les microservices internes. La cohérence à terme et les architectures basées sur les événements permettent de réduire les effets en chaîne. Ces approches appliquent un plus haut niveau d’autonomie des microservices, c’est pourquoi elles préviennent le problème indiqué ici.

**Utilisez les nouvelles tentatives avec interruption exponentielle**. Cette technique permet d’éviter les défaillances brèves et intermittentes en effectuant de nouvelles tentatives d’appel un certain nombre de fois, dans le cas où le service ne serait pas disponible pendant seulement une courte période. Cela peut se produire lors de problèmes réseau intermittents ou quand un microservice/conteneur est déplacé vers un autre nœud d’un cluster. Toutefois, si ces nouvelles tentatives ne sont pas correctement conçues avec des disjoncteurs, les effets en chaîne peuvent s’aggraver, entraînant même, à terme, un [déni de service](https://en.wikipedia.org/wiki/Denial-of-service_attack).

**Contournez les délais d’attente réseau**. En général, les clients doivent être conçus pour ne pas se bloquer indéfiniment et pour toujours utiliser des délais d’expiration lors de l’attente d’une réponse. L’utilisation de délais d’expiration garantit que les ressources ne sont jamais bloquées indéfiniment.

**Utilisez le modèle Disjoncteur**. Dans cette approche, le processus client suit le nombre de requêtes ayant échoué. Si le taux d’erreurs dépasse une limite configurée, un « disjoncteur » est déclenché de sorte que les autres tentatives échouent immédiatement. (Si un grand nombre de demandes échouent, cela suggère que le service n’est pas disponible et que l’envoi de demandes est inutile.) Après une période de temps mort, le client devrait essayer à nouveau et, si les nouvelles demandes sont acceptées, fermer le disjoncteur.

**Fournissez des solutions de secours**. Dans cette approche, le processus client exécute la logique de secours en cas d’échec d’une requête, comme le retour de données mises en cache ou d’une valeur par défaut. Il s’agit d’une approche appropriée pour les requêtes, mais qui est plus complexe pour les mises à jour ou les commandes.

**Limitez le nombre de requêtes placées en file d’attente**. Les clients doivent également imposer une limite plus grande du nombre de requêtes en attente qu’un microservice client peut envoyer à un service particulier. Si la limite est atteinte, il est probablement inutile d’effectuer d’autres requêtes, et ces tentatives devraient échouer immédiatement. En termes d’implémentation, la stratégie d’[isolation par cloisonnement](https://github.com/App-vNext/Polly/wiki/Bulkhead) de Polly peut être utilisée pour satisfaire cette exigence. Cette approche est essentiellement une limitation de parallélisation avec <xref:System.Threading.SemaphoreSlim> comme implémentation. Elle autorise également une « file d’attente » à l’extérieur du cloisonnement. Vous pouvez vous protéger de manière proactive contre une charge excessive , même avant l’exécution (par exemple, parce que la capacité maximale est considérée comme atteinte). Ainsi, sa réponse à certains scénarios de défaillance est plus rapide que celle d’un disjoncteur, puisque le disjoncteur attend la défaillance. Dans [Polly](http://www.thepollyproject.org/), l’objet BulkheadPolicy expose le niveau de remplissage du cloisonnement et de la file d’attente. De plus, en cas de dépassement, il propose des événements qui peuvent également être utilisés pour gérer la mise à l’échelle horizontale automatisée.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Modèles de résilience**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **Ajout de résilience et optimisation des performances**\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **Cloison.** Dépôt GitHub. Implémentation de la stratégie de Polly.
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **Concevoir des applications résilientes pour Azure**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **Manipulation transitoire des défauts**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[Suivant précédent](handle-partial-failure.md)
>[Next](implement-retries-exponential-backoff.md)
