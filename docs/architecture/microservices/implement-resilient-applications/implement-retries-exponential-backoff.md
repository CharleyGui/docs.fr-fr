---
title: Implémenter de nouvelles tentatives avec interruption exponentielle
description: Découvrez comment implémenter de nouvelles tentatives avec interruption exponentielle.
ms.date: 10/16/2018
ms.openlocfilehash: 1b948e399495eeb12016006442ac08d2b04f2e69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68674536"
---
# <a name="implement-retries-with-exponential-backoff"></a><span data-ttu-id="3da5c-103">Implémenter de nouvelles tentatives avec interruption exponentielle</span><span class="sxs-lookup"><span data-stu-id="3da5c-103">Implement retries with exponential backoff</span></span>

<span data-ttu-id="3da5c-104">Les [*nouvelles tentatives avec interruption exponentielle*](/azure/architecture/patterns/retry) sont un mécanisme qui permet de retenter une opération après un temps d’attente qui augmente de manière exponentielle, jusqu’à ce que le nombre maximal de tentatives configuré ait été atteint (l’[interruption exponentielle](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="3da5c-104">[*Retries with exponential backoff*](/azure/architecture/patterns/retry) is a technique that retries an operation, with an exponentially increasing wait time, up to a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="3da5c-105">Ce mécanisme prend en compte le fait que les ressources du cloud peuvent être indisponibles par intermittence pendant plus de quelques secondes pour une raison quelconque.</span><span class="sxs-lookup"><span data-stu-id="3da5c-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="3da5c-106">C’est le cas, par exemple, quand un orchestrateur déplace un conteneur vers un autre nœud dans un cluster pour équilibrer la charge.</span><span class="sxs-lookup"><span data-stu-id="3da5c-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="3da5c-107">Durant cette opération, certaines requêtes risquent d’échouer.</span><span class="sxs-lookup"><span data-stu-id="3da5c-107">During that time, some requests might fail.</span></span> <span data-ttu-id="3da5c-108">Cela peut aussi se produire, par exemple, quand une base de données comme SQL Azure est déplacée sur un autre serveur pour équilibrer la charge. La base de données n’est alors plus disponible pendant plusieurs secondes.</span><span class="sxs-lookup"><span data-stu-id="3da5c-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="3da5c-109">Il existe plusieurs approches possibles pour implémenter la logique de nouvelles tentatives avec interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="3da5c-109">There are many approaches to implement retries logic with exponential backoff.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3da5c-110">[Suivant précédent](partial-failure-strategies.md)
>[Next](implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="3da5c-110">[Previous](partial-failure-strategies.md)
[Next](implement-resilient-entity-framework-core-sql-connections.md)</span></span>
