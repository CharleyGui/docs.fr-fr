---
title: Introduction - gRPC pour les développeurs WCF
description: Introduction
ms.date: 09/02/2019
ms.openlocfilehash: 41f470eb02a77b1b6a26a7d4c2ca347ad07d828d
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988932"
---
# <a name="introduction"></a>Introduction

Aider les machines à communiquer entre elles a été l’une des principales préoccupations de l’ère numérique. En particulier, il y a un effort continu pour déterminer le mécanisme optimal de communication à distance qui conviendra aux exigences d’interopérabilité de l’infrastructure actuelle. Comme vous pouvez l’imaginer, ce mécanisme change au fur et à mesure que les exigences ou l’infrastructure évoluent.

La sortie de .NET Core 3.0 marque un changement dans la façon dont Microsoft fournit des solutions de communication à distance aux développeurs qui veulent fournir des services sur une gamme de plates-formes. .NET Core n’offre pas Windows Communication Foundation (WCF) hors de la boîte, mais, avec la sortie de ASP.NET Core 3.0, il fournit intégré dans la fonctionnalité gRPC.

gRPC est un cadre populaire dans la communauté logicielle au sens large. Il est utilisé par les développeurs à travers de nombreux langages de programmation pour les scénarios RPC modernes. La communauté et l’écosystème sont dynamiques et actifs. Le soutien au protocole gRPC est ajouté aux composants d’infrastructure comme les Kubernetes, les mailles de service, les équilibristes de charge, et plus encore. Ces facteurs, ainsi que ses performances, son efficacité et sa compatibilité multiplateforme, font de gRPC un choix naturel pour les nouvelles applications et les applications WCF qui se déplacent vers .NET Core.

## <a name="history"></a>Historique

Le principe fondamental d’un réseau informatique comme rien de plus qu’un groupe d’ordinateurs échangeant des données les uns avec les autres pour réaliser un ensemble de tâches interdépendantes n’a pas changé depuis sa création. Mais la complexité, l’ampleur et les attentes ont augmenté de façon exponentielle.  

Au cours des années 1990, l’accent a été mis principalement sur l’amélioration des réseaux internes qui utilisaient le même langage et les mêmes plates-formes. TCP/IP est devenu l’étalon-or de ce type de communication.

L’accent s’est rapidement déplacé sur la meilleure façon d’optimiser la communication sur plusieurs plates-formes en promouvant une approche agnostique linguistique. L’architecture axée sur le service (SOA) a fourni une structure pour épelage d’une vaste collection de services qui pourraient être fournis à une application.

Le développement des *services Web* s’est produit lorsque toutes les grandes plates-formes pouvaient accéder à Internet, mais ils ne pouvaient toujours pas interagir les uns avec les autres. Les services Web ont des normes et des protocoles ouverts, notamment :

- XML pour marquer et coder les données.
- Protocole d’accès aux objets simples (SOAP) pour transférer des données.
- Web Services Definition Language (WSDL) pour décrire et connecter les services Web aux applications client.
- Universal Description, Découverte et Intégration (UDDI) pour rendre les services Web détectables par d’autres services.

SOAP définit les règles par lesquelles les éléments distribués d’une application peuvent communiquer entre eux, même si elles sont sur différentes plates-formes. SOAP est basé sur XML, il est donc lisible par l’homme. Le sacrifice pour faire SOAP facilement compris est la taille; Les messages SOAP sont plus grands que les messages dans des protocoles comparables. SOAP a été conçu pour briser les applications monolithiques sous forme multicomposante sans perdre la sécurité ou le contrôle. Ainsi, WCF a été conçu pour travailler avec ce genre de système, contrairement à gRPC, qui a commencé comme un système distribué. WCF a abordé certaines de ces limitations en élaborant et en documentant des protocoles d’extension propriétaires pour la pile SOAP, mais au prix d’un manque de soutien de la part d’autres plates-formes.

Windows Communication Foundation est un cadre pour la construction de services. Il a été conçu au début des années 2000 pour aider les développeurs utilisant soA tôt pour gérer les complexités de travailler avec SOAP. Bien qu’il supprime l’obligation pour les développeurs d’écrire leurs propres protocoles SOAP, WCF utilise toujours SOAP pour activer l’interopérabilité avec d’autres systèmes. WCF a également été conçu pour fournir des solutions sur plusieurs protocoles (HTTP/1.1, Net.TCP, etc.).

## <a name="microservices"></a>Microservices

Dans les architectures de microservices, de grandes applications sont construites comme une collection de services modulaires plus petits. Chaque composant effectue une tâche ou un processus spécifique, et les composants sont conçus pour fonctionner interopératoirement, mais peuvent être isolés au besoin.

Les avantages pour les microservices comprennent :

- Les modifications et les mises à niveau peuvent être traitées de manière indépendante.
- La manipulation des erreurs devient plus efficace parce que les problèmes peuvent être attribués à des services spécifiques qui sont ensuite isolés, reconstruits, testés et redéployés indépendamment des autres services.
- L’évolutivité peut se limiter à des instances ou des services spécifiques plutôt qu’à l’ensemble de l’application.
- Le développement peut se faire au-delà de plusieurs équipes, avec moins de friction que lorsque de nombreuses équipes travaillent sur une base de code unique.

L’évolution vers une virtualisation croissante, l’informatique en nuage, les conteneurs et l’Internet des objets a contribué à l’essor continu des microservices. Mais les microservices ne sont pas sans défis. L’infrastructure fragmentée/décentralisée met davantage l’accent sur le besoin de simplicité et de rapidité lors de la communication entre les services. Cela a attiré l’attention sur la nature parfois laborieuse et tordue de SOAP.

C’est dans cet environnement que gRPC a été lancé, 10 ans après la première sortie de Microsoft WCF. Évolué directement à partir de l’infrastructure interne de Google RPC (Stubby), gRPC n’a jamais été basé sur les mêmes normes et protocoles qui avaient informé les paramètres de nombreux RPC plus tôt. Et gRPC n’a jamais été basé sur HTTP/2. C’est pourquoi il pourrait s’appuyer sur les nouvelles capacités que le protocole de transport avancé fourni. En particulier, le streaming bidirectionnel, la messagerie binaire et le multiplexe.

## <a name="about-this-guide"></a>À propos de ce guide

Ce guide couvre les principales caractéristiques de gRPC. Les premiers chapitres jetez un coup d’œil de haut niveau aux principales caractéristiques du WCF et les comparent à celles de gRPC. Il identifie où il existe des corrélations directes entre WCF et gRPC et aussi où gRPC offre un avantage. Lorsqu’il n’y a pas de corrélation entre WCF et gRPC, ou lorsque gRPC n’est pas en mesure d’offrir une solution équivalente à WCF, ce guide vous propose des solutions de contournement ou où aller pour obtenir plus d’informations.

À l’aide d’un ensemble d’applications WCF échantillon, chapitre 5 est un regard de plongée profonde à convertir les principaux types de service WCF (simple demande-réponse, aller simple, et streaming) à leurs équivalents dans gRPC.

La dernière section du livre examine comment tirer le meilleur parti de gRPC dans la pratique. Cette section comprend des informations sur l’utilisation d’outils supplémentaires, comme les conteneurs Docker ou Kubernetes, pour profiter de l’efficacité de gRPC. Il comprend également un examen détaillé de la surveillance avec l’exploitation forestière, les mesures et le traçage distribué.

## <a name="who-this-guide-is-for"></a>Audience à laquelle ce guide est destiné

Ce guide a été écrit pour les développeurs travaillant dans .NET Framework ou .NET Core qui ont utilisé WCF et qui cherchent à migrer leurs applications vers un environnement RPC moderne pour .NET Core 3.0 et les versions ultérieures. Le guide peut également être utile plus généralement pour les développeurs mise à niveau ou envisagent de mise à niveau vers .NET Core 3.0 et qui veulent utiliser les outils gRPC intégrés.

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](grpc-overview.md)
