---
title: Équilibrage de charge gRPC-gRPC pour les développeurs WCF
description: Choix d’un équilibreur de charge pour fonctionner avec les services gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 070fc7fda73988302d15c8cec12b1ac359641317
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967451"
---
# <a name="load-balancing-grpc"></a>Équilibrage de charge gRPC

Un déploiement classique d’une application gRPC comprend un certain nombre d’instances identiques du service, offrant ainsi une résilience et une évolutivité horizontale. Équilibrage de charge des demandes entrantes distribuées sur ces instances pour fournir une utilisation complète de toutes les ressources disponibles. Pour rendre cet équilibrage de charge invisible au client, il est courant d’utiliser un serveur d’équilibrage de charge de proxy pour gérer les demandes des clients et les acheminer vers les instances de serveur principal.

Les équilibrages de charge sont classés en fonction de la *couche* sur laquelle ils opèrent. Les équilibreurs de charge de couche 4 fonctionnent au niveau du *transport* , par exemple avec les sockets TCP, les connexions et les paquets. Les équilibreurs de charge de couche 7 fonctionnent au niveau de l' *application* , en gérant spécifiquement les demandes http/2 pour les applications gRPC.

## <a name="l4-load-balancers"></a>Équilibreurs de charge L4

Un équilibreur de charge L4 accepte une demande de connexion TCP à partir d’un client, ouvre une autre connexion à l’une des instances de serveur principal, et copie les données entre les deux connexions sans traitement réel. L4 offre d’excellentes performances et une faible latence, mais très peu de contrôle ou d’intelligence. Tant que le client maintient la connexion ouverte, toutes les demandes sont dirigées vers la même instance de serveur principal.

Le [Azure load balancer](https://azure.microsoft.com/services/load-balancer/)est un exemple d’équilibrage de charge n4.

## <a name="l7-load-balancers"></a>Équilibreurs de charge L7

Un équilibreur de charge L7 analyse les demandes HTTP/2 entrantes et les transmet aux instances du serveur principal à la demande, quelle que soit la durée pendant laquelle la connexion est maintenue par le client.

Voici quelques exemples d’équilibrage de charge L7 :

- [Nginx](https://www.nginx.com/)
- [HAproxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

En règle générale, les équilibreurs de charge L7 sont le meilleur choix pour gRPC et d’autres applications HTTP/2 (et, en fait, pour les applications HTTP). Les équilibreurs de charge L4 *fonctionnent* avec les applications gRPC, mais sont principalement utiles lorsque la faible latence et la faible surcharge sont primordiales.

> [!IMPORTANT]
> Au moment de la rédaction de cet article, tous les équilibrages de charge L7 ne prennent pas en charge toutes les parties de la spécification HTTP/2 requises par les services gRPC, tels que les en-têtes de fin.

Lorsque vous utilisez le chiffrement TLS, les équilibrages de charge peuvent mettre fin à la connexion TLS et transmettre des demandes non chiffrées à l’application principale, ou transmettre la requête chiffrée. Dans les deux cas, l’équilibreur de charge doit être configuré avec la clé publique et la clé privée du serveur, afin qu’il puisse déchiffrer les demandes de traitement.

Reportez-vous à la documentation de votre équilibreur de charge préféré pour savoir comment le configurer pour gérer les demandes HTTP/2 avec vos services principaux.

## <a name="load-balancing-within-kubernetes"></a>Équilibrage de charge dans Kubernetes

Consultez [la section sur les maillages de service](service-mesh.md) pour une discussion sur l’équilibrage de charge entre les services internes sur Kubernetes.

>[!div class="step-by-step"]
>[Précédent](service-mesh.md)
>[Suivant](application-performance-management.md)
