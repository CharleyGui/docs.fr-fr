---
title: Implémenter de nouvelles tentatives avec interruption exponentielle
description: Découvrez comment implémenter de nouvelles tentatives avec interruption exponentielle.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674536"
---
# <a name="implement-retries-with-exponential-backoff"></a>Implémenter de nouvelles tentatives avec interruption exponentielle

Les [*nouvelles tentatives avec interruption exponentielle*](/azure/architecture/patterns/retry) sont un mécanisme qui permet de retenter une opération après un temps d’attente qui augmente de manière exponentielle, jusqu’à ce que le nombre maximal de tentatives configuré ait été atteint (l’[interruption exponentielle](https://en.wikipedia.org/wiki/Exponential_backoff)). Ce mécanisme prend en compte le fait que les ressources du cloud peuvent être indisponibles par intermittence pendant plus de quelques secondes pour une raison quelconque. C’est le cas, par exemple, quand un orchestrateur déplace un conteneur vers un autre nœud dans un cluster pour équilibrer la charge. Durant cette opération, certaines requêtes risquent d’échouer. Cela peut aussi se produire, par exemple, quand une base de données comme SQL Azure est déplacée sur un autre serveur pour équilibrer la charge. La base de données n’est alors plus disponible pendant plusieurs secondes.

Il existe plusieurs approches possibles pour implémenter la logique de nouvelles tentatives avec interruption exponentielle.

>[!div class="step-by-step"]
>[Précédent](partial-failure-strategies.md)
>[Suivant](implement-resilient-entity-framework-core-sql-connections.md)
