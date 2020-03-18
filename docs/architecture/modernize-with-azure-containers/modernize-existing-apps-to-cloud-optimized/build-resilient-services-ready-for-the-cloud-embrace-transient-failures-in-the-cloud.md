---
title: Construisez des services résilients prêts pour le cloud. gérer les échecs passagers dans le cloud
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Construisez des services résilients prêts pour le cloud. gérer les échecs passagers dans le cloud
ms.date: 04/30/2018
ms.openlocfilehash: e516dc675ceb8def25c6d676bced0ea7f253b2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711242"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Créer des services résilients prêts pour le cloud : gérer les défaillances transitoires dans le cloud

La résilience est la capacité à récupérer après des défaillances et à continuer de fonctionner. La résilience n’est pas d’éviter les échecs, mais d’accepter le fait que des échecs se produiront, puis d’y répondre d’une manière qui évite les temps d’arrêt ou la perte de données. La résilience vise à remettre l’application dans un état entièrement fonctionnel après une défaillance.

Votre application est prête pour le cloud lorsqu’elle implémente au minimum un modèle de résilience basé sur un logiciel, plutôt qu’un modèle basé sur le matériel. Votre application cloud doit embrasser les défaillances partielles qui se produiront certainement. Concevez ou refacturez partiellement votre application pour obtenir une résilience avec les défaillances partielles attendues. Il doit être conçu pour faire face à des défaillances partielles, comme les pannes de réseau transitoires et les nœuds, ou les VM s’écraser dans le nuage. Même les conteneurs déplacés vers un nœud différent au sein d’un groupe d’orchestrateurs peuvent causer des défaillances courtes intermittentes dans l’application.

## <a name="handling-partial-failure"></a>Gestion d’une défaillance partielle

Dans une application basée sur le cloud, il existe un risque toujours présent de défaillance partielle. Par exemple, une seule instance de site Web ou un conteneur peut échouer, ou il peut être indisponible ou insensible pendant une courte période. Ou, un seul VM ou serveur peut planter.

Étant donné que les clients et les services sont des processus distincts, un service pourrait ne pas être en mesure de répondre en temps opportun à la demande d’un client. Le service peut être surchargé et répondre lentement aux demandes, ou il pourrait ne pas être accessible pendant une courte période en raison de problèmes de réseau.

Par exemple, envisagez une application monolithique .NET qui accède à une base de données dans la base de données Azure SQL. Si la base de données Azure SQL ou tout autre service tiers ne répond pas pendant une brève période (une base de données Azure SQL peut être déplacée vers un nœud ou un serveur différent, et ne pas être réactif pendant quelques secondes), lorsque l’utilisateur tente de faire une action, l’application peut s’écraser et faire exception au même moment.

Un scénario similaire peut se produire dans une application qui consomme des services HTTP. Le réseau ou le service lui-même peut ne pas être disponible dans le cloud lors d’une défaillance courte et transitoire.

Une application résiliente comme celle indiquée dans la figure 4-9 devrait mettre en œuvre des techniques comme « retries with exponential backoff » pour donner à l’application la possibilité de gérer les défaillances transitoires des ressources. Vous devez également utiliser des « disjoncteurs » dans vos applications. Un disjoncteur empêche une application d’essayer d’accéder à une ressource lorsqu’il s’agit en fait d’une défaillance à long terme. En utilisant un disjoncteur, l’application évite de provoquer un déni de service à elle-même.

![Diagramme des échecs partiels manipulés par des retries avec backoff exponentiel.](./media/retry-partial-failures.png)

**Figure 4-9.** Échecs partiels gérés par des retries avec backoff exponentiel

Vous pouvez utiliser ces techniques à la fois dans les ressources HTTP et dans les ressources de base de données. Dans la figure 4-9, l’application est basée sur une architecture à 3 niveaux, vous avez donc besoin de ces techniques au niveau des services (HTTP) et au niveau de niveau de données (TCP). Dans une application monolithique qui n’utilise qu’un seul niveau d’application en plus de la base de données (pas de services ou de microservices supplémentaires), la manipulation des défaillances transitoires au niveau de connexion de base de données peut suffire. Dans ce scénario, il suffit d’une configuration particulière de la connexion de base de données.

Lors de la mise en œuvre de communications résilientes qui accèdent à la base de données, en fonction de la version de .NET que vous utilisez, il peut être simple (par exemple, [avec Entity Framework 6 ou plus tard](/ef/ef6/fundamentals/connection-resiliency/retry-logic). Il s’agit simplement de configurer la connexion de base de données). Ou, vous pourriez avoir besoin d’utiliser d’autres bibliothèques comme le [bloc d’application de traitement des défauts transitoires](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (pour les versions antérieures de .NET), ou même implémenter votre propre bibliothèque.

Lors de la mise en œuvre des retries HTTP et des disjoncteurs, la recommandation de .NET est d’utiliser la bibliothèque [Polly,](https://github.com/App-vNext/Polly) qui cible .NET Framework 4.0, .NET Framework 4.5, et .NET Standard 1.1, qui comprend .NET Core support.

Pour apprendre à mettre en œuvre des stratégies de gestion des défaillances partielles dans le cloud, consultez les références suivantes.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Mise en œuvre d’une communication résiliente pour gérer l’échec partiel**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **La résilience et la logique de la réalitance de connexion du Cadre d’entité (version 6 et plus tard)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Bloc applicatif de gestion des erreurs temporaires**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Bibliothèque Polly pour la communication résiliente HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Suivant précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[Next](modernize-your-apps-with-monitoring-and-telemetry.md)
