---
title: Créez des services résilients prêts pour le Cloud. gérer les échecs passagers dans le cloud
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Créez des services résilients prêts pour le Cloud. gérer les échecs passagers dans le cloud
ms.date: 04/30/2018
ms.openlocfilehash: e6fae8140b55cb0308dca9f4b77e961501b41f8f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739396"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Créez des services résilients prêts pour le Cloud : adoptez des échecs temporaires dans le Cloud

La résilience est la capacité à surmonter les défaillances et à continuer de fonctionner. La résilience ne permet pas d’éviter les défaillances, mais accepte le fait que des échecs se produisent, puis répond à celles-ci de manière à éviter les temps d’arrêt ou la perte de données. La résilience vise à remettre l’application dans un état entièrement fonctionnel après une défaillance.

Votre application est prête pour le Cloud quand, au minimum, elle implémente un modèle de résilience basé sur des logiciels plutôt qu’un modèle basé sur le matériel. Votre application Cloud doit accepter les défaillances partielles qui se produiront certainement. Concevez ou refactorisez partiellement votre application pour obtenir une résilience avec des échecs partiels attendus. Elle doit être conçue pour faire face aux défaillances partielles, telles que les pannes réseau temporaires et les nœuds, ou les pannes de machines virtuelles dans le Cloud. Même les conteneurs qui sont déplacés vers un nœud différent au sein d’un cluster Orchestrator peuvent entraîner des défaillances courtes intermittentes au sein de l’application.

## <a name="handling-partial-failure"></a>Gestion d’une défaillance partielle

Dans une application basée sur le Cloud, il y a un risque de défaillance partielle. Par exemple, une instance de site Web unique ou un conteneur peut échouer, ou elle peut ne pas être disponible ou ne pas répondre pendant une brève période. Ou une seule machine virtuelle ou un seul serveur peut se bloquer.

Étant donné que les clients et les services sont des processus distincts, un service peut ne pas être en mesure de répondre en temps opportun à la demande d’un client. Le service peut être surchargé et répondre lentement aux demandes, ou il peut ne pas être accessible pendant une brève période en raison de problèmes réseau.

Par exemple, considérez une application .NET monolithique qui accède à une base de données dans Azure SQL Database. Si la base de données SQL Azure ou tout autre service tiers ne répond pas pendant une courte période (une base de données SQL Azure peut être déplacée vers un autre nœud ou serveur et ne pas répondre pendant quelques secondes), lorsque l’utilisateur tente d’effectuer une action, l’application peut se bloquer et l’être w une exception au même moment.

Un scénario similaire peut se produire dans une application qui consomme des services HTTP. Le réseau ou le service lui-même peut ne pas être disponible dans le Cloud en cas de défaillance temporaire.

Une application résiliente telle que celle illustrée dans la figure 4-9 doit implémenter des techniques telles que « nouvelles tentatives avec interruption exponentielle » pour permettre à l’application de gérer les défaillances temporaires dans les ressources. Vous devez également utiliser des « disjoncteurs » dans vos applications. Un disjoncteur empêche une application d’essayer d’accéder à une ressource lorsqu’il s’agit d’une défaillance à long terme. À l’aide d’un disjoncteur, l’application évite de provoquer un déni de service à lui-même.

![Diagramme des échecs partiels gérés par les nouvelles tentatives avec interruption exponentielle.](./media/build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud/retry-partial-failures.png)

**Figure 4-9.** Échecs partiels gérés par les nouvelles tentatives avec interruption exponentielle

Vous pouvez utiliser ces techniques à la fois dans les ressources HTTP et dans les ressources de base de données. Dans la figure 4-9, l’application est basée sur une architecture à trois niveaux. vous avez donc besoin de ces techniques au niveau des services (HTTP) et au niveau de la couche données (TCP). Dans une application monolithique qui n’utilise qu’un seul niveau d’application en plus de la base de données (pas de services ou de microservices supplémentaires), la gestion des échecs temporaires au niveau de la connexion de base de données peut suffire. Dans ce scénario, une seule configuration particulière de la connexion de base de données est requise.

Lors de l’implémentation de communications résilientes qui accèdent à la base de données, en fonction de la version de .NET que vous utilisez, elle peut être simple (par exemple, [avec Entity Framework 6 ou version ultérieure](/ef/ef6/fundamentals/connection-resiliency/retry-logic)). Il suffit de configurer la connexion à la base de données. Ou bien, vous devrez peut-être utiliser des bibliothèques supplémentaires telles que le [bloc applicatif de gestion des erreurs temporaires](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)) (pour les versions antérieures de .net) ou même implémenter votre propre bibliothèque.

Lors de l’implémentation de nouvelles tentatives HTTP et de disjoncteurs, la recommandation pour .NET consiste à utiliser la bibliothèque [Polly](https://github.com/App-vNext/Polly) , qui cible .NET Framework 4,0, .NET Framework 4,5 et .NET standard 1,1, qui comprend la prise en charge de .net core.

Pour savoir comment implémenter des stratégies de gestion des défaillances partielles dans le Cloud, consultez les références suivantes.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Implémentation d’une communication résiliente pour gérer les défaillances partielles**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Résilience des connexions Entity Framework et logique de nouvelle tentative (version 6 et ultérieures)**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **Bloc applicatif de gestion des erreurs temporaires**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Bibliothèque Polly pour la communication HTTP résiliente**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[Suivant](modernize-your-apps-with-monitoring-and-telemetry.md)
