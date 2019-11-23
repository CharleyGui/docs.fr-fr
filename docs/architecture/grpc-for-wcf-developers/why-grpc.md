---
title: Pourquoi gRPC est recommandé pour les développeurs WCF-gRPC pour les développeurs WCF
description: Une discussion sur la raison pour laquelle gRPC est adapté aux développeurs WCF qui cherchent à migrer vers des architectures et des plateformes modernes.
ms.date: 09/02/2019
ms.openlocfilehash: da712e1ceee92f0a1a2661252dcda602f5dde9a0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966943"
---
# <a name="why-grpc-is-recommended-for-wcf-developers"></a>Pourquoi gRPC est recommandé pour les développeurs WCF

Avant de plonger dans le langage et les techniques de gRPC, il est intéressant de savoir pourquoi gRPC est la solution adaptée aux développeurs WCF qui veulent migrer vers .NET Core, étant donné que des solutions alternatives sont disponibles.

## <a name="similarity-to-wcf"></a>Similarité avec WCF

Bien que son implémentation et son approche soient différentes, l’expérience réelle du développement et de la consommation de services avec gRPC doit être très intuitive pour les développeurs WCF. L’objectif sous-jacent de rendre possible le code comme si le client et le serveur étaient sur la même plate-forme, sans avoir à se soucier de la mise en réseau, est identique. Les deux plateformes partagent le principe de déclaration et d’implémentation d’une interface, même si le processus de déclaration de cette interface est différent. Comme vous le verrez au chapitre 5, les différents types d’appels RPC pris en charge par gRPC sont très bien adaptés aux différentes liaisons disponibles pour les services WCF.

## <a name="benefits-of-grpc"></a>Avantages de gRPC

Les autres raisons pour lesquelles gRPC se trouve au-dessus d’autres solutions sont les suivantes :

### <a name="performance"></a>Performances

Comme indiqué précédemment, l’utilisation de HTTP/2 au lieu de HTTP/1.1 supprime la nécessité de disposer de messages explicites et utilise plutôt le protocole binaire plus petit plus rapide. Cela est plus efficace pour l’analyse des ordinateurs. HTTP/2 prend également en charge le multiplexage des requêtes sur une seule connexion, ce qui permet d’envoyer des réponses dès qu’elles sont prêtes, sans qu’il soit nécessaire d’attendre dans une file d’attente (problème dans HTTP/1.1 appelé « blocage de la tête de ligne (HOL) »). Moins de ressources sont nécessaires lors de l’utilisation de gRPC, ce qui en fait une bonne solution à utiliser pour les appareils mobiles et sur les réseaux plus lents.

### <a name="interoperability"></a>Interopérabilité

Il existe des outils et des bibliothèques gRPC pour tous les principaux langages de programmation et plateformes, notamment .NET, C++Java, Python, Go,, node. js, SWIFT, DART, Ruby et php. Grâce au format de câble binaire de tampon de protocole et à la génération de code efficace pour chaque plateforme, les développeurs peuvent créer des applications performantes tout en bénéficiant d’une prise en charge multiplateforme complète.

### <a name="usability-and-productivity"></a>Convivialité et productivité

gRPC est une solution RPC complète. Il fonctionne de manière cohérente sur plusieurs langages et plateformes, et fournit un excellent outil, avec une grande partie du code réutilisable généré automatiquement, de sorte que davantage de temps pour les développeurs est libéré pour se concentrer sur la logique métier.

### <a name="streaming"></a>Diffusion

gRPC dispose d’une diffusion en continu bidirectionnelle complète qui offre des fonctionnalités très similaires aux services duplex complets de WCF. la diffusion en continu gRPC peut fonctionner sur des connexions Internet régulières, des équilibrages de charge et des maillages de service.

### <a name="deadlinetimeouts-and-cancellation"></a>Échéance/délais d’attente et annulation

gRPC permet aux clients de spécifier la durée maximale d’exécution d’un RPC. Si l’échéance spécifiée est dépassée, le serveur peut annuler l’opération indépendamment du client. Les échéances et les annulations peuvent être propagées à travers d’autres appels gRPC pour permettre d’appliquer les limites d’utilisation des ressources. Les clients peuvent également abandonner les opérations lorsqu’une échéance est dépassée, ou une version antérieure si nécessaire (par exemple, en raison d’une interaction avec l’utilisateur).

### <a name="security"></a>Sécurité

gRPC est implicitement sécurisé lors de l’utilisation de HTTP/2 sur une connexion chiffrée de bout en bout TLS. La prise en charge de l’authentification par certificat client (voir le chapitre 6) augmente davantage la sécurité et la confiance entre le client et le serveur.

>[!div class="step-by-step"]
>[Précédent](network-protocols.md)
>[Suivant](protocol-buffers.md)
