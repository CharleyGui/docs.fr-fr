---
title: Protocoles réseau-gRPC pour les développeurs WCF
description: Vue d’ensemble des protocoles réseau gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: cf99b2608d576765856c992679b93b6f21e796cf
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846395"
---
# <a name="network-protocols"></a>Protocoles réseau

Contrairement à WCF, gRPC utilise HTTP/2 comme base pour sa mise en réseau. Cela offre des avantages significatifs par rapport à WCF et SOAP, qui fonctionnent uniquement sur HTTP/1.1. Pour les développeurs souhaitant utiliser gRPC, étant donné qu’il n’y a pas d’alternative à HTTP/2, il semblerait être le moment idéal pour explorer HTTP/2 plus en détail et pour identifier les avantages supplémentaires de l’utilisation de gRPC.

HTTP/2, publié par l’IETF (Internet Engineering Task Force) dans 2015, était dérivé du protocole expérimental SPDY, qui était déjà utilisé par Google. Il a été spécialement conçu pour être plus efficace, plus rapide et plus sûr que HTTP/1.1.

## <a name="key-features-of-http2"></a>Fonctionnalités clés du protocole HTTP/2

La liste suivante présente quelques-unes des fonctionnalités clés et des avantages du protocole HTTP/2 :

### <a name="binary-protocol"></a>Protocole binaire

Les cycles de demande/réponse n’ont plus besoin de commandes de texte. Cela simplifie et accélère l’implémentation des commandes. Plus précisément, l’analyse des données est plus rapide et utilise moins de mémoire, la latence du réseau est réduite avec des améliorations significatives en termes de vitesse et une meilleure utilisation globale des ressources réseau.

### <a name="streams"></a>Flux

Les flux permettent de créer des connexions à long terme entre l’expéditeur et le récepteur, sur lesquels plusieurs messages ou frames peuvent être envoyés de manière asynchrone. Plusieurs flux peuvent fonctionner indépendamment sur une seule connexion HTTP/2.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Demander le multiplexage sur une seule connexion TCP

Cette fonctionnalité est l’une des innovations les plus importantes de HTTP/2. En autorisant plusieurs demandes parallèles de données, il est désormais possible de télécharger des fichiers Web simultanément à partir d’un seul serveur. Les sites Web se chargent plus rapidement et le besoin d’optimisation est réduit. Blocage de la tête de ligne (HOL), où les réponses qui sont prêtes doivent attendre d’être envoyées jusqu’à ce qu’une requête antérieure soit terminée, est également atténuée (bien que le blocage de HOL puisse encore se produire au niveau du transport TCP).

### <a name="nettcp-like-performance-cross-platform"></a>Performances NetTCP, multiplateforme

Fondamentalement, la combinaison de gRPC et HTTP/2 offre aux développeurs au moins la vitesse et l’efficacité équivalentes des liaisons NetTCP pour WCF, et dans certains cas encore plus rapides et plus efficaces. Toutefois, contrairement à NetTCP, gRPC sur HTTP/2 n’est pas restreinte aux applications .NET.

>[!div class="step-by-step"]
>[Précédent](interface-definition-language.md)
>[Suivant](why-grpc.md)
