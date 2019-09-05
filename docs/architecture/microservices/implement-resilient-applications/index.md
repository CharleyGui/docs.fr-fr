---
title: Implémentation d’applications résilientes
description: En savoir plus sur la résilience, un concept fondamental dans une architecture de microservices. Vous devez savoir comment gérer des défaillances temporaires, qui ne manqueront pas de se produire.
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296059"
---
# <a name="implement-resilient-applications"></a>Implémenter des applications résilientes

*Vos applications basées sur des microservices et sur le cloud devront faire face tôt ou tard à des défaillances partielles qui se produiront à coup sûr. Vous devez concevoir votre application de façon à la rendre résiliente face à ces défaillances partielles.*

La résilience est la capacité à surmonter les défaillances et à continuer de fonctionner. Il ne s’agit pas d’éviter les défaillances, mais d’accepter le fait qu’il s’en produira et qu’il faudra y répondre pour éviter des temps d’arrêt ou des pertes de données. La résilience vise à remettre l’application dans un état entièrement fonctionnel après une défaillance.

Il est déjà assez difficile de concevoir et de déployer une application basée sur des microservices. Mais vous devez aussi veiller à ce votre application continue de s’exécuter dans un environnement qui subira à coup sûr une défaillance quelconque. Par conséquent, votre application doit être résiliente. Elle doit être conçue pour faire face à des défaillances partielles, qu’il s’agisse de pannes réseau ou d’incidents sur des nœuds ou des machines virtuelles dans le cloud. Même les microservices (conteneurs) qui sont déplacés sur un autre nœud de cluster peuvent occasionner de brèves défaillances intermittentes au sein de l’application.

Les divers composants qui constituent votre application doivent aussi intégrer des fonctionnalités de contrôle d’intégrité. En suivant les recommandations fournies dans ce chapitre, vous pouvez créer une application capable de fonctionner correctement en dépit des temps morts temporaires ou des interruptions normales qui se produisent dans les déploiements complexes et dans le cloud.

>[!div class="step-by-step"]
>[Précédent](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Suivant](handle-partial-failure.md)
