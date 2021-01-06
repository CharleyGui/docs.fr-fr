---
title: Pourquoi nous recommandons gRPC pour les développeurs WCF-gRPC pour les développeurs WCF
description: Une discussion sur la raison pour laquelle gRPC est adapté aux développeurs WCF qui souhaitent migrer vers des architectures et des plateformes modernes.
ms.date: 12/15/2020
ms.openlocfilehash: 058f85297610116e96c8580fcefb10ee6dfcf935
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937972"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>Pourquoi nous recommandons gRPC pour les développeurs WCF

Avant de plonger dans le langage et les techniques de gRPC, il est intéressant de savoir pourquoi gRPC est la solution adaptée aux développeurs Windows Communication Foundation (WCF) qui souhaitent migrer vers .NET.

## <a name="similarity-to-wcf"></a>Similarité avec WCF

Bien que l’implémentation et l’approche soient différentes pour gRPC, l’expérience du développement et de l’utilisation des services avec gRPC doit être intuitive pour les développeurs WCF. L’objectif sous-jacent est le même : il est possible de coder comme si le client et le serveur se trouvent sur la même plate-forme, sans avoir à se soucier de la mise en réseau.

Les deux plateformes partagent le principe de déclaration et d’implémentation d’une interface, même si le processus de déclaration de cette interface est différent. Comme vous le verrez au chapitre 5, les différents types d’appels RPC que gRPC prend en charge mappent bien aux liaisons disponibles pour les services WCF.

## <a name="benefits-of-grpc"></a>Avantages de gRPC

gRPC est au-dessus d’autres solutions pour les raisons suivantes.

### <a name="performance"></a>Performances

L’utilisation de HTTP/2 plutôt que HTTP/1.1 supprime la nécessité de disposer de messages explicites et utilise à la place le protocole binaire plus petit et plus rapide. Cela est plus efficace pour l’analyse des ordinateurs. HTTP/2 prend également en charge le multiplexage des requêtes sur une seule connexion. Cette prise en charge permet d’envoyer des réponses dès qu’elles sont prêtes, sans qu’il soit nécessaire d’attendre dans une file d’attente. (Dans HTTP/1.1, ce problème est connu sous le nom de « blocage en tête de ligne (HOL) ».) Vous avez besoin de moins de ressources lors de l’utilisation de gRPC, ce qui en fait une bonne solution à utiliser pour les appareils mobiles et sur les réseaux plus lents.

### <a name="interoperability"></a>Interopérabilité

Il existe des outils et des bibliothèques gRPC pour tous les principaux langages de programmation et plateformes, notamment .NET, Java, Python, Go, C++, Node.js, SWIFT, DART, Ruby et PHP. Grâce au format de câble binaire de tampon de protocole et à la génération de code efficace pour chaque plateforme, les développeurs peuvent créer des applications performantes tout en bénéficiant d’une prise en charge multiplateforme complète.

### <a name="usability-and-productivity"></a>Convivialité et productivité

gRPC est une solution RPC complète. Il fonctionne de manière cohérente sur plusieurs langages et plateformes. Il fournit également d’excellents outils, avec une grande partie du code réutilisable généré automatiquement. Ainsi, davantage de temps pour les développeurs est libéré pour se concentrer sur la logique métier.

### <a name="streaming"></a>Diffusion en continu

gRPC dispose d’une diffusion en continu bidirectionnelle complète qui offre des fonctionnalités similaires à celles des services duplex intégral de WCF. la diffusion en continu gRPC peut fonctionner sur des connexions Internet régulières, des équilibrages de charge et des maillages de service.

### <a name="deadlinetimeouts-and-cancellation"></a>Échéance/délais d’attente et annulation

gRPC permet aux clients de spécifier la durée maximale pendant laquelle un RPC se termine. Si l’échéance spécifiée est dépassée, le serveur peut annuler l’opération indépendamment du client. Les échéances et les annulations peuvent être propagées à travers d’autres appels gRPC pour permettre d’appliquer les limites d’utilisation des ressources. Les clients peuvent également arrêter des opérations lorsqu’une échéance est dépassée, ou une version antérieure si nécessaire (par exemple, en raison d’une interaction avec l’utilisateur).

### <a name="security"></a>Sécurité

gRPC est implicitement sécurisé lorsqu’il utilise HTTP/2 sur une connexion chiffrée de bout en bout TLS. La prise en charge de l’authentification par certificat client (voir le [chapitre 6](security.md)) augmente davantage la sécurité et la confiance entre le client et le serveur.

>[!div class="step-by-step"]
>[Précédent](network-protocols.md) 
> [Suivant](protocol-buffers.md)
