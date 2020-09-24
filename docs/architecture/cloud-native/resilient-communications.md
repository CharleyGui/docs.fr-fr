---
title: Communication résiliente
description: Architecture des applications .NET natives Cloud pour Azure | Communication résiliente
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 18b26223634efc5c05f680d0cbb7c8cbc2490a59
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166038"
---
# <a name="resilient-communications"></a>Communications résilientes

Tout au long de ce document, nous avons adopté une approche architecturale basée sur des microservices. Bien qu’une telle architecture offre des avantages importants, elle présente de nombreux défis :

- *Communication réseau hors processus.* Chaque microservice communique via un protocole réseau qui introduit une congestion du réseau, une latence et des erreurs temporaires.

- *Découverte des services.* Comment les microservices découvrent et communiquent les uns avec les autres lorsqu’ils s’exécutent sur un cluster de machines avec leurs propres ports et adresses IP ?

- *Résilience.* Comment gérer les défaillances de courte durée de vie et assurer la stabilité du système ?

- *Équilibrage de la charge.* Comment le trafic entrant est-il distribué entre plusieurs instances d’un microservice ?

- *Sécurité.* Comment les problèmes de sécurité tels que le chiffrement au niveau du transport et la gestion des certificats sont-ils appliqués ?

- *Analyse distribuée.* -Comment mettre en corrélation et capturer la traçabilité et la surveillance d’une seule requête sur plusieurs microservices consommés ?

Vous pouvez résoudre ces problèmes avec des bibliothèques et des infrastructures différentes, mais l’implémentation peut être coûteuse, complexe et fastidieuse. Vous obtenez également des problèmes d’infrastructure associés à la logique métier.

## <a name="service-mesh"></a>Maille de service

Une meilleure approche est une technologie en constante évolution intitulée *Mesh service*. Une [maille de service](https://www.nginx.com/blog/what-is-a-service-mesh/) est une couche d’infrastructure configurable avec des fonctionnalités intégrées pour gérer la communication de service et les autres difficultés mentionnées ci-dessus. Il dissocie ces préoccupations en les déplaçant dans un proxy de service. Le proxy est déployé dans un processus séparé (appelé [side-car](/azure/architecture/patterns/sidecar)) pour assurer l’isolation à partir du code d’entreprise. Toutefois, le side-car est lié au service, il est créé avec lui et partage son cycle de vie. La figure 6-7 illustre ce scénario.

![Maille de service avec une voiture latérale](./media/service-mesh-with-side-car.png)

**Figure 6-7.** Maille de service avec une voiture latérale

Dans la figure précédente, Notez comment le proxy intercepte et gère la communication entre les microservices et le cluster.

Un maillage de service est logiquement divisé en deux composants disparates : un [plan de données](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) et un [plan de contrôle](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). La figure 6-8 montre ces composants et leurs responsabilités.

![Contrôle de maillage de service et plan de données](./media/istio-control-and-data-plane.png)

**Figure 6-8.** Contrôle de maillage de service et plan de données

Une fois configuré, un maillage de service est très fonctionnel. Il peut récupérer un pool d’instances correspondant à partir d’un point de terminaison de découverte de service. La maille peut ensuite envoyer une demande à une instance spécifique, en enregistrant la latence et le type de réponse du résultat. Une maille peut choisir l’instance la plus susceptible de retourner une réponse rapide en fonction de nombreux facteurs, y compris la latence observée pour les demandes récentes.

Si une instance ne répond pas ou échoue, le maillage réessaie la demande sur une autre instance. Si elle retourne des erreurs, une maille supprime l’instance du pool d’équilibrage de charge et la renomme après sa réparation. Si une demande expire, une maille peut échouer, puis retenter la demande. Une maille capture et émet des métriques et le traçage distribué vers un système de mesures centralisé.

## <a name="istio-and-envoy"></a>Istio et Envoy

Bien qu’il existe actuellement quelques options de maillage de service, [Istio](https://istio.io/docs/concepts/what-is-istio/) est le plus populaire au moment de la rédaction de cet article. Istio est une entreprise conjointe d’IBM, Google et LYFT. Il s’agit d’une offre Open source qui peut être intégrée dans une application distribuée nouvelle ou existante. La technologie offre une solution cohérente et complète pour sécuriser, connecter et surveiller les microservices. Ses fonctionnalités sont les suivantes :

- Sécuriser les communications de service à service dans un cluster avec une authentification et une autorisation puissantes basées sur l’identité.
- Équilibrage de charge automatique pour le trafic HTTP, [gRPC](https://grpc.io/), WebSocket et TCP.
- Contrôle affiné du comportement du trafic avec des règles de routage riches, des nouvelles tentatives, des basculements et une injection d’erreurs.
- Une couche de stratégie enfichable et une API de configuration prennent en charge les contrôles d’accès, les limites de taux et les quotas.
- Mesures automatiques, journaux et traces pour tout le trafic au sein d’un cluster, y compris l’entrée et la sortie du cluster.

Un composant clé pour une implémentation de Istio est un service proxy ayant le [proxy Envoy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy). Il s’exécute à côté de chaque service et fournit une base de plateforme agnostique pour les fonctionnalités suivantes :

- Découverte de service dynamique.
- Équilibrage de charge :
- Arrêt TLS.
- Proxys HTTP et gRPC.
- Résilience de disjoncteur.
- Contrôles d’intégrité.
- Mises à jour propagées avec des déploiements de [Canaries](https://martinfowler.com/bliki/CanaryRelease.html) .

Comme indiqué précédemment, Envoy est déployé en tant que side-car pour chaque microservice du cluster.

## <a name="integration-with-azure-kubernetes-services"></a>Intégration avec les services Azure Kubernetes

Le Cloud Azure prend en charge Istio et fournit un support direct pour celui-ci dans les services Azure Kubernetes. Les liens suivants peuvent vous aider à vous lancer :

- [Installation de Istio dans AKS](/azure/aks/istio-install)
- [Utilisation de AKS et Istio](/azure/aks/istio-scenario-routing)

### <a name="references"></a>Références

- [Polly](http://www.thepollyproject.org/)

- [Modèle de nouvelle tentative](/azure/architecture/patterns/retry)

- [Modèle Disjoncteur](/azure/architecture/patterns/circuit-breaker)

- [Livre blanc sur la résilience dans Azure](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [latence du réseau](https://www.techopedia.com/definition/8553/network-latency)

- [Redondance](/azure/architecture/guide/design-principles/redundancy)

- [géo-réplication](/azure/sql-database/sql-database-active-geo-replication)

- [Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview)

- [Guide de mise à l’échelle automatique](/azure/architecture/best-practices/auto-scaling)

- [Istio](https://istio.io/docs/concepts/what-is-istio/)

- [Proxy d’envoi](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
>[Précédent](infrastructure-resiliency-azure.md) 
> [Suivant](monitoring-health.md)
