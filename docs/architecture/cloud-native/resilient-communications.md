---
title: Communication résiliente
description: Architecture des applications .NET natives Cloud pour Azure | Communication résiliente
ms.date: 06/30/2019
ms.openlocfilehash: 324f5426af1c892db73aa6fc2336a19b7a8e499e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315802"
---
# <a name="resilient-communications"></a>Communications résilientes

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Tout au long de ce document, nous avons regroupé les mérites d’aller au-delà de la conception d’applications monolithiques traditionnelles et d’adopter une architecture basée sur des microservices où un ensemble de services distribués et autonomes s’exécutent de manière indépendante et communiquent avec chacun autre utilisation de protocoles de communication standard tels que HTTP et HTTPs. Bien qu’une telle architecture achète de nombreux avantages importants, elle présente également de nombreux défis. Prenez par exemple en compte les problèmes suivants :

- *Communication réseau hors processus.* Chaque service communique sur un protocole réseau qui introduit une congestion du réseau, une latence et des erreurs temporaires.
- *Détection du service.* Chaque service s’exécutant sur un cluster de machines avec sa propre adresse IP et son propre port, comment les services découvrent et communiquent les uns avec les autres ?
- *Résilience.* Comment gérer les défaillances de courte durée de vie et assurer la stabilité du système ?
- *Équilibrage de charge.* Comment le trafic entrant est-il distribué entre plusieurs instances d’un service ?
- *Sécurité* : Comment les problèmes de sécurité tels que le chiffrement au niveau du transport et la gestion des certificats sont-ils appliqués ?
- *Analyse distribuée.* -Comment mettre en corrélation et capturer la traçabilité et la surveillance d’une seule requête sur plusieurs services de consommation ?

Bien que ces problèmes puissent être résolus avec différentes bibliothèques et frameworks, leur mise en œuvre dans votre base de code peut s’avérer coûteuse, complexe et fastidieuse. En outre, vous vous retrouvez avec une solution dans laquelle les problèmes d’infrastructure sont associés à la logique métier.

## <a name="service-mesh"></a>Maille de service

Une meilleure approche consiste à prendre en compte une technologie nouvelle et évoluant rapidement, intitulée *service Mesh*. Une [maille de service](https://www.nginx.com/blog/what-is-a-service-mesh/) est une couche d’infrastructure configurable avec des fonctionnalités intégrées permettant de gérer la communication de service et de nombreuses difficultés mentionnées ci-dessus. Il dissocie ces problèmes de votre code d’entreprise et les déplace dans un proxy de service, une instance de qui accompagne chacun de vos services. Souvent appelé [modèle de side-car](https://docs.microsoft.com/azure/architecture/patterns/sidecar), le proxy de maille de service est déployé dans un processus distinct pour assurer l’isolation et l’encapsulation à partir de votre code d’entreprise. Toutefois, le proxy est étroitement lié au service en cours de création, ainsi qu’au partage de son cycle de vie. La figure 6-9 illustre ce scénario.

![Maille de service avec une voiture latérale](./media/service-mesh-with-side-car.png)

**Figure 6-9.** Maille de service avec une voiture latérale

Dans la figure précédente, Notez comment le proxy intercepte et gère la communication entre les microservices et le cluster.

Un maillage de service est logiquement divisé en deux composants disparates : un [plan de données](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) et un [plan de contrôle](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). La figure 6-10 montre ces composants et leurs responsabilités.

![Contrôle de maillage de service et plan de données](./media/istio-control-and-data-plane.png)

**Figure 6-10.** Contrôle de maillage de service et plan de données

Une fois configuré, un maillage de service est très fonctionnel. Il peut récupérer un pool d’instances correspondant à partir d’un point de terminaison de découverte de service. Il peut ensuite envoyer une requête à une instance spécifique, en enregistrant la latence et le type de réponse du résultat. Une maille peut choisir l’instance la plus susceptible de retourner une réponse rapide en fonction de nombreux facteurs, y compris la latence observée pour les demandes récentes.

Si une instance ne répond pas ou échoue, la maille peut retenter la demande sur une autre instance. Si un pool retourne des erreurs de manière cohérente, un maillage peut le supprimer du pool d’équilibrage de charge pour qu’il soit retenté régulièrement après sa réparation. Si une demande expire, une maille peut échouer, puis retenter la demande. Une maille capture le comportement sous forme de métriques et de traçage distribué, qui peut ensuite être émis vers un système de mesures centralisé.

## <a name="istio-and-envoy"></a>Istio et Envoy

Bien qu’il existe actuellement quelques options de maillage de service, [Istio](https://istio.io/docs/concepts/what-is-istio/) est le plus populaire au moment de la rédaction de cet article. Une entreprise conjointe d’IBM, Google et LYFT, il s’agit d’une offre Open source qui peut être intégrée dans une application distribuée nouvelle ou existante. Il fournit une solution cohérente et complète pour sécuriser, connecter et surveiller les microservices. Ses fonctionnalités sont les suivantes :

- Sécuriser les communications de service à service dans un cluster avec une authentification et une autorisation puissantes basées sur l’identité.
- Équilibrage de charge automatique pour le trafic HTTP, [gRPC](https://grpc.io/), WebSocket et TCP.
- Contrôle affiné du comportement du trafic avec des règles de routage riches, des nouvelles tentatives, des basculements et une injection d’erreurs.
- Une couche de stratégie enfichable et une API de configuration prennent en charge les contrôles d’accès, les limites de taux et les quotas.
- Mesures automatiques, journaux et traces pour tout le trafic au sein d’un cluster, y compris l’entrée et la sortie du cluster.

Un composant clé pour une implémentation de Istio est un service proxy ayant le [proxy Envoy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy). En provenance de LYFT et par la suite contribué à la [Fondation Cloud Native Computing](https://www.cncf.io/) (décrite dans le chapitre 1), le proxy Envoy s’exécute à côté de chaque service et fournit une base de plateforme agnostique pour les fonctionnalités suivantes :

- Découverte de service dynamique.
- Équilibrage de charge.
- Arrêt TLS.
- Proxys HTTP et gRPC.
- Résilience de disjoncteur.
- Contrôles d’intégrité.
- Mises à jour propagées avec des déploiements de [Canaries](https://martinfowler.com/bliki/CanaryRelease.html) .

Comme indiqué précédemment, Envoy est déployé en tant que side-car pour chaque microservice du cluster.

## <a name="integration-with-azure-kubernetes-services"></a>Intégration avec les services Azure Kubernetes

Le Cloud Azure prend en charge Istio et fournit un support direct pour celui-ci dans les services Azure Kubernetes. Les liens suivants peuvent vous aider à vous lancer :

- [Installation de Istio dans AKS](https://docs.microsoft.com/azure/aks/istio-install)
- [Utilisation de AKS et Istio](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

>[!div class="step-by-step"]
>[Précédent](infrastructure-resiliency-azure.md)
>[Suivant](monitoring-health.md)
