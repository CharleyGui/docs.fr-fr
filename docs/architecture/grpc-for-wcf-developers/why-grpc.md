---
title: Pourquoi nous recommandons gRPC pour les développeurs WCF - gRPC pour les développeurs WCF
description: Une discussion sur les raisons pour lesquelles gRPC est un bon ajustement pour les développeurs WCF qui veulent migrer vers les architectures modernes et les plates-formes.
ms.date: 09/02/2019
ms.openlocfilehash: 664781e94c24c1796eafa6a70eb28d453b530d66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147644"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>Pourquoi nous recommandons gRPC pour les développeurs WCF

Avant de plonger profondément dans la langue et les techniques de gRPC, il vaut la peine de discuter pourquoi gRPC est la bonne solution pour Windows Communication Foundation (WCF) développeurs qui veulent migrer vers .NET Core.

## <a name="similarity-to-wcf"></a>Similitude avec WCF

Bien que la mise en œuvre et l’approche soient différentes pour gRPC, l’expérience du développement et de la consommation de services avec gRPC devrait être intuitive pour les développeurs de WCF. L’objectif sous-jacent est le même : permettre de coder comme si le client et le serveur étaient sur la même plate-forme, sans avoir à se soucier du réseautage.

Les deux plates-formes partagent le principe de déclarer puis de mettre en œuvre une interface, même si le processus de déclaration de cette interface est différent. Et comme vous le verrez dans le chapitre 5, les différents types d’appels RPC que gRPC prend en charge la carte bien aux liaisons disponibles pour les services WCF.

## <a name="benefits-of-grpc"></a>Avantages de gRPC

gRPC se tient au-dessus d’autres solutions pour les raisons suivantes.

### <a name="performance"></a>Performances

L’utilisation de HTTP/2 plutôt que DE HTTP/1.1 supprime l’exigence de messages lisibles par l’homme et utilise plutôt le protocole binaire plus petit et plus rapide. Ceci est plus efficace pour les ordinateurs à analyser. HTTP/2 prend également en charge les demandes de multiplexing sur une seule connexion. Ce support permet d’envoyer des réponses dès qu’elles sont prêtes sans avoir besoin d’attendre dans une file d’attente. (Dans HTTP/1.1, ce numéro est connu sous le nom de « blocage de la tête de gamme (HOL) ». Vous avez besoin de moins de ressources lors de l’utilisation de gRPC, ce qui en fait une bonne solution à utiliser pour les appareils mobiles et sur les réseaux plus lents.

### <a name="interoperability"></a>Interopérabilité

Il existe des outils et des bibliothèques gRPC pour tous les principaux langages et plates-formes de programmation, y compris .NET, Java, Python, Go, C, Node.js, Swift, Dart, Ruby et PHP. Grâce au format de fil binaire Protocol Buffers et à la génération de code efficace pour chaque plate-forme, les développeurs peuvent créer des applications performantes tout en bénéficiant d’un support multiplateforme complet.

### <a name="usability-and-productivity"></a>Convivialité et productivité

gRPC est une solution RPC complète. Il fonctionne de façon cohérente sur plusieurs langues et plates-formes. Il fournit également un excellent outillage, avec une grande partie du code de plaque de chaudière nécessaire automatiquement généré. Ainsi, plus de temps de développeur est libéré pour se concentrer sur la logique d’affaires.

### <a name="streaming"></a>Diffusion en continu

gRPC dispose d’un streaming bidirectionnel complet, qui offre des fonctionnalités similaires aux services complets de duplex de WCF. GRPC streaming peut fonctionner sur des connexions Internet régulières, les équilibristes de charge, et les mailles de service.

### <a name="deadlinetimeouts-and-cancellation"></a>Délais/temps d’arrêt et annulation

gRPC permet aux clients de spécifier un délai maximum pour qu’un CPR finisse. Si la date limite spécifiée est dépassée, le serveur peut annuler l’opération indépendamment du client. Les délais et les annulations peuvent être propagés par d’autres appels gRPC pour aider à faire respecter les limites d’utilisation des ressources. Les clients peuvent également arrêter les opérations lorsqu’une date limite est dépassée, ou plus tôt si nécessaire (par exemple, en raison d’une interaction utilisateur).

### <a name="security"></a>Sécurité

gRPC est implicitement sécurisé lorsqu’il utilise HTTP/2 sur une connexion cryptée de bout en bout TLS. La prise en charge de l’authentification des certificats clients (voir [le chapitre 6)](security.md)augmente encore la sécurité et la confiance entre le client et le serveur.

>[!div class="step-by-step"]
>[Suivant précédent](network-protocols.md)
>[Next](protocol-buffers.md)
