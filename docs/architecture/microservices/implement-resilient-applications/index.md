---
title: Implémenter des applications résilientes
description: En savoir plus sur la résilience, un concept fondamental dans une architecture de microservices. Vous devez savoir comment gérer les défaillances temporaires normalement lorsqu’elles se produisent.
ms.date: 01/30/2020
ms.openlocfilehash: ccdb2470c727ad4bd89c4e0634da8564b8010e63
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502652"
---
# <a name="implement-resilient-applications"></a>Implémenter des applications résilientes

*Vos applications basées sur le microservice et le Cloud doivent prendre en compte les défaillances partielles qui seront certainement finalement effectuées. Vous devez concevoir votre application pour qu’elle soit résiliente à ces défaillances partielles.*

La résilience est la capacité à récupérer après des défaillances et à continuer de fonctionner. Il ne s’agit pas d’éviter les défaillances, mais d’accepter le fait qu’il s’en produira et qu’il faudra y répondre pour éviter des temps d’arrêt ou des pertes de données. La résilience vise à remettre l’application dans un état entièrement fonctionnel après une défaillance.

Il est déjà assez difficile de concevoir et de déployer une application basée sur des microservices. Mais vous devez aussi veiller à ce votre application continue de s’exécuter dans un environnement qui subira à coup sûr une défaillance quelconque. Par conséquent, votre application doit être résiliente. Elle doit être conçue pour faire face à des défaillances partielles, qu’il s’agisse de pannes réseau ou d’incidents sur des nœuds ou des machines virtuelles dans le cloud. Même les microservices (conteneurs) qui sont déplacés sur un autre nœud de cluster peuvent occasionner de brèves défaillances intermittentes au sein de l’application.

Les divers composants qui constituent votre application doivent aussi intégrer des fonctionnalités de contrôle d’intégrité. En suivant les recommandations fournies dans ce chapitre, vous pouvez créer une application capable de fonctionner correctement en dépit des temps morts temporaires ou des interruptions normales qui se produisent dans les déploiements complexes et dans le cloud.

>[!IMPORTANT]
> eShopOnContainer utilisait la [bibliothèque Polly](http://www.thepollyproject.org/) pour implémenter la résilience à l’aide de [clients typés](./use-httpclientfactory-to-implement-resilient-http-requests.md) jusqu’au 3.0.0 de la version.
>
> À partir de la version 3.0.0, la résilience des appels HTTP est implémentée à l’aide d’une [maille Linkerd](https://linkerd.io/), qui gère les nouvelles tentatives de manière transparente et configurable, au sein d’un cluster Kubernetes, sans avoir à gérer ces problèmes dans le code.
>
> La bibliothèque Polly est toujours utilisée pour ajouter la résilience aux connexions de base de données, particulièrement lors du démarrage des services.

>[!WARNING]
> Tous les exemples de code de cette section étaient valides avant l’utilisation de Linkerd et ne sont pas mis à jour pour refléter le code réel actuel. Ils ont donc un sens dans le contexte de cette section.

>[!div class="step-by-step"]
>[Précédent](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Suivant](handle-partial-failure.md)
