---
title: Mettre en œuvre des applications résilientes
description: En savoir plus sur la résilience, un concept fondamental dans une architecture de microservices. Vous devez savoir comment gérer les échecs transitoires gracieusement quand ils se produisent.
ms.date: 01/30/2020
ms.openlocfilehash: 46276a6b9b36a494bfae657275692ca9d5554d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78847230"
---
# <a name="implement-resilient-applications"></a>Mettre en œuvre des applications résilientes

*Vos applications de microservice et de cloud doivent englober les défaillances partielles qui se produiront certainement éventuellement. Vous devez concevoir votre application pour être résiliente à ces défaillances partielles.*

La résilience est la capacité à récupérer après des défaillances et à continuer de fonctionner. Il ne s’agit pas d’éviter les défaillances, mais d’accepter le fait qu’il s’en produira et qu’il faudra y répondre pour éviter des temps d’arrêt ou des pertes de données. La résilience vise à remettre l’application dans un état entièrement fonctionnel après une défaillance.

Il est déjà assez difficile de concevoir et de déployer une application basée sur des microservices. Mais vous devez aussi veiller à ce votre application continue de s’exécuter dans un environnement qui subira à coup sûr une défaillance quelconque. Par conséquent, votre application doit être résiliente. Elle doit être conçue pour faire face à des défaillances partielles, qu’il s’agisse de pannes réseau ou d’incidents sur des nœuds ou des machines virtuelles dans le cloud. Même les microservices (conteneurs) qui sont déplacés sur un autre nœud de cluster peuvent occasionner de brèves défaillances intermittentes au sein de l’application.

Les divers composants qui constituent votre application doivent aussi intégrer des fonctionnalités de contrôle d’intégrité. En suivant les recommandations fournies dans ce chapitre, vous pouvez créer une application capable de fonctionner correctement en dépit des temps morts temporaires ou des interruptions normales qui se produisent dans les déploiements complexes et dans le cloud.

>[!IMPORTANT]
> eShopOnContainer avait utilisé la [bibliothèque Polly](http://www.thepollyproject.org/) pour implémenter la résilience à [l’aide de clients typés](./use-httpclientfactory-to-implement-resilient-http-requests.md) jusqu’à la sortie 3.0.0.
>
> En commençant par la version 3.0.0, la résilience des appels HTTP est implémentée à l’aide [d’un maillage Linkerd](https://linkerd.io/), qui gère les retries d’une manière transparente et configurable, au sein d’un cluster Kubernetes, sans avoir à gérer ces préoccupations dans le code.
>
> La bibliothèque Polly est toujours utilisée pour ajouter de la résilience aux connexions de base de données, spécialement lors du démarrage des services.

>[!WARNING]
> Tous les échantillons de code de cette section étaient valides avant d’utiliser Linkerd et ne sont pas mis à jour pour refléter le code actuel. Ils ont donc du sens dans le contexte de cette section.

>[!div class="step-by-step"]
>[Suivant précédent](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Next](handle-partial-failure.md)
