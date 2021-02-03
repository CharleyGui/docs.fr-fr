---
title: Modèles de résilience d’application
description: Architecture des applications .NET natives Cloud pour Azure | Modèles de résilience d’application
author: robvet
ms.date: 01/19/2021
ms.openlocfilehash: 9a59a7d93b61b0dea11680f6caf0bd3b68a0f853
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505919"
---
# <a name="application-resiliency-patterns"></a>Modèles de résilience d’application

La première ligne de défense est la résilience des applications.

Bien que vous puissiez consacrer beaucoup de temps à écrire votre propre infrastructure de résilience, de tels produits existent déjà. [Polly](http://www.thepollyproject.org/) est une bibliothèque complète de résilience .net et de gestion des erreurs temporaires qui permet aux développeurs d’exprimer les stratégies de résilience de façon Fluent et thread-safe. Polly cible les applications générées avec le .NET Framework ou le .NET 5. Le tableau suivant décrit les fonctionnalités de résilience, appelées `policies` , disponibles dans la bibliothèque Polly. Elles peuvent être appliquées individuellement ou regroupées.

| Policy | Expérience |
| :-------- | :-------- |
| Recommencer | Configure les opérations de nouvelle tentative sur les opérations désignées. |
| Disjoncteur | Bloque les opérations demandées pour une période prédéfinie lorsque les erreurs dépassent un seuil configuré |
| Délai d'expiration | Limite la durée pendant laquelle un appelant peut attendre une réponse. |
| Cloisonnement | Limite les actions à un pool de ressources de taille fixe pour empêcher les appels défaillants de inonder une ressource. |
| Cache | Stocke les réponses automatiquement. |
| Secours | Définit le comportement structuré en cas d’échec. |

Notez comment, dans la figure précédente, les stratégies de résilience s’appliquent aux messages de demande, qu’ils proviennent d’un client externe ou d’un service principal. L’objectif est de compenser la demande d’un service qui peut être momentanément indisponible. Ces interruptions courtes se manifestent généralement avec les codes d’état HTTP indiqués dans le tableau suivant.

| Code d’état HTTP| Cause |
| :-------- | :-------- |
| 404 | Introuvable |
| 408 | Délai d’expiration de la demande |
| 429 | Trop de requêtes (vous avez probablement été limité) |
| 502 | Passerelle incorrecte |
| 503 | Service indisponible |
| 504 | Délai d’expiration de la passerelle |

Question : voulez-vous réessayer un code d’état HTTP 403-interdit ? Non. Ici, le système fonctionne correctement, mais informe l’appelant qu’il n’est pas autorisé à effectuer l’opération demandée. Vous devez veiller à ne réessayer que les opérations provoquées par des défaillances.

Comme nous l’avons recommandé dans le chapitre 1, les développeurs Microsoft qui créent des applications Cloud natives doivent cibler la plate-forme .NET. La version 2,1 a introduit la bibliothèque [HTTPClientFactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) pour la création d’instances client http pour l’interaction avec les ressources basées sur une URL. En remplaçant la classe HTTPClient d’origine, la classe Factory prend en charge de nombreuses fonctionnalités améliorées, dont l’une est une [intégration étroite](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) avec la bibliothèque de résilience Polly. Avec elle, vous pouvez facilement définir des stratégies de résilience dans la classe de démarrage de l’application pour gérer les défaillances partielles et les problèmes de connectivité.

Nous allons ensuite développer les modèles de réessai et de disjoncteur.

### <a name="retry-pattern"></a>Modèle Nouvelle tentative

Dans un environnement Cloud natif distribué, les appels aux services et aux ressources de Cloud peuvent échouer en raison d’échecs temporaires (éphémères), qui se corrigent généralement après une courte période de temps. L’implémentation d’une stratégie de nouvelle tentative aide un service Cloud-native à atténuer ces scénarios.

Le [modèle de nouvelle tentative](/azure/architecture/patterns/retry) permet à un service de retenter une opération de demande ayant échoué (configurable) un nombre de fois avec un délai d’attente qui croît de manière exponentielle. La figure 6-2 montre une nouvelle tentative en action.

![Modèle de nouvelle tentative en action](./media/retry-pattern.png)

**Figure 6-2**. Modèle de nouvelle tentative en action

Dans la figure précédente, un modèle de nouvelle tentative a été implémenté pour une opération de demande. Elle est configurée pour autoriser jusqu’à quatre tentatives avant d’échouer avec un intervalle d’attente (temps d’attente) à partir de deux secondes, ce qui double de façon exponentielle pour chaque tentative suivante.

- La première invocation échoue et retourne le code d’état HTTP 500. L’application attend deux secondes et réessaie l’appel.
- Le deuxième appel échoue également et retourne le code d’état HTTP 500. L’application double maintenant l’intervalle d’interruption à quatre secondes et réessaie l’appel.
- Enfin, le troisième appel aboutisse.
- Dans ce scénario, l’opération de nouvelle tentative aurait tenté jusqu’à quatre tentatives tout en doublant la durée de l’interruption avant l’échec de l’appel.
- En cas d’échec de la quatrième tentative de nouvelle tentative, une stratégie de secours serait appelée pour traiter correctement le problème.

Il est important d’augmenter la période d’interruption avant de retenter l’appel pour que le temps de service s’auto-correct. Il est recommandé d’implémenter une interruption exponentiellement plus longue (doublement de la période à chaque nouvelle tentative) pour permettre une correction appropriée.

## <a name="circuit-breaker-pattern"></a>Modèle disjoncteur

Alors que le modèle de nouvelle tentative peut aider à récupérer une requête qui a été intégrée dans une défaillance partielle, il existe des situations où les échecs peuvent être provoqués par des événements imprévus qui nécessitent des périodes plus longues à résoudre. Ces erreurs peuvent aller d’une perte partielle de connectivité à la défaillance complète d’un service. Dans ces situations, il est inutile pour une application de réessayer continuellement une opération qui risque de ne pas aboutir.

Pour compliquer les choses, l’exécution d’opérations de nouvelle tentative continues sur un service non réactif peut vous faire passer dans un scénario de déni de service auto-imposé où vous inondez votre service d’appels continus qui épuisent les ressources telles que la mémoire, les threads et les connexions de base de données.

Dans ces situations, il serait préférable que l’opération échoue immédiatement et tente uniquement d’appeler le service si elle est susceptible de réussir.

Le [modèle disjoncteur](/azure/architecture/patterns/circuit-breaker) peut empêcher une application de tenter d’exécuter à plusieurs reprises une opération qui risque d’échouer. Après un nombre prédéfini d’appels ayant échoué, il bloque tout le trafic vers le service. Périodiquement, il permet à un appel d’essai de déterminer si l’erreur a été résolue. La figure 6-3 illustre le modèle de disjoncteur en action.

![Modèle disjoncteur en action](./media/circuit-breaker-pattern.png)

**Figure 6-3**. Modèle disjoncteur en action

Dans la figure précédente, un modèle de disjoncteur a été ajouté au modèle de nouvelle tentative d’origine. Notez comment après les échecs de demandes de 100, les disjoncteurs s’ouvrent et n’autorisent plus les appels au service. La valeur CheckCircuit, définie à 30 secondes, spécifie la fréquence à laquelle la bibliothèque autorise une requête à passer au service. Si cet appel s’effectue correctement, le circuit se ferme et le service est à nouveau disponible pour le trafic.

Gardez à l’esprit que l’objectif du modèle de disjoncteur est *différent* de celui du modèle de nouvelle tentative. Le modèle de nouvelle tentative permet à une application de retenter une opération dans l’attente qu’elle aboutisse. Le modèle disjoncteur empêche une application d’effectuer une opération qui risque d’échouer. En règle générale, une application *combine* ces deux modèles en utilisant le modèle nouvelle tentative pour appeler une opération par le biais d’un disjoncteur.

## <a name="testing-for-resiliency"></a>Test pour la résilience

Le test de la résilience ne peut pas toujours être effectué de la même façon que vous testez les fonctionnalités de l’application (en exécutant des tests unitaires, des tests d’intégration, etc.). Au lieu de cela, vous devez tester la manière dont la charge de travail de bout en bout s’effectue dans des conditions d’échec, qui se produisent uniquement par intermittence. Par exemple : injecter des échecs en bloquant des processus, des certificats arrivés à expiration, rendre les services dépendants indisponibles, etc. Des infrastructures comme [chaos-singe](https://github.com/Netflix/chaosmonkey) peuvent être utilisées pour des tests de chaos.

La résilience des applications est nécessaire pour gérer les opérations demandées. Mais il ne s’agit que de la moitié de l’histoire. Nous aborderons ensuite les fonctionnalités de résilience disponibles dans le Cloud Azure.

>[!div class="step-by-step"]
>[Précédent](resiliency.md) 
> [Suivant](infrastructure-resiliency-azure.md)
