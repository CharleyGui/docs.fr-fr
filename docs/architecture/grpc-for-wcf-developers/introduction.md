---
title: Introduction-gRPC pour les développeurs WCF
description: Introduction
ms.date: 12/15/2020
ms.openlocfilehash: f85d174da6d6493e6f406f132f2ffb773cbcc33d
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938596"
---
# <a name="introduction"></a>Introduction

Aider les machines à communiquer entre elles a été l’une des principales préoccupations de l’ère numérique. En particulier, il existe un effort permanent pour déterminer le mécanisme de communication à distance optimal qui répondra aux demandes d’interopérabilité de l’infrastructure actuelle. Comme vous pouvez l’imaginer, ce mécanisme change au fur et à mesure que les demandes ou l’infrastructure évoluent.

La sortie de .NET Core 3,0 marque une évolution de la façon dont Microsoft fournit des solutions de communication à distance pour les développeurs qui souhaitent fournir des services sur toute une gamme de plateformes. .NET Core et versions ultérieures ne proposent pas Windows Communication Foundation (WCF) prêt à l’emploi mais, avec la sortie de ASP.NET Core 3,0, il offre des fonctionnalités gRPC intégrées.

gRPC est un Framework populaire dans la communauté de logiciels plus larges. Elle est utilisée par les développeurs dans de nombreux langages de programmation pour les scénarios RPC modernes. La communauté et l’écosystème sont vivant et actif. La prise en charge du protocole gRPC est ajoutée aux composants d’infrastructure tels que Kubernetes, les maillages de service, les équilibrages de charge, etc. Ces facteurs, ainsi que sa performance, son efficacité et sa compatibilité multiplateforme, font de gRPC un choix naturel pour les nouvelles applications et les applications WCF qui se déplacent vers .NET.

## <a name="history"></a>Historique

Le principe fondamental d’un réseau informatique puisque rien de plus qu’un groupe d’ordinateurs qui échange des données entre eux pour atteindre un ensemble de tâches interdépendantes n’a pas été modifié depuis son commencement. Mais la complexité, la mise à l’échelle et les attentes ont augmenté de façon exponentielle.

Au cours des années 90, l’accent était principalement sur l’amélioration des réseaux internes qui utilisaient la même langue et les mêmes plates-formes. TCP/IP est devenu la norme Gold pour ce type de communication.

Le focus est rapidement déplacé vers la meilleure façon d’optimiser la communication sur plusieurs plateformes en promouvant une approche indépendante du langage. L’architecture orientée service (SOA, Service-Oriented Architecture) a fourni une structure permettant de coupler librement une vaste collection de services pouvant être fournis à une application.

Le développement de *services Web* s’est produit lorsque toutes les principales plateformes pouvaient accéder à Internet, mais ils ne pouvaient toujours pas interagir entre eux. Les services Web ont des normes et des protocoles ouverts, notamment :

- XML pour baliser et coder les données.
- Protocole SOAP (Simple Object Access Protocol) pour transférer des données.
- WSDL (Web Services Definition Language) pour décrire et connecter des services Web à des applications clientes.
- Universal Description, Discovery and Integration (UDDI) pour rendre les services Web détectables par d’autres services.

SOAP définit les règles selon lesquelles les éléments distribués d’une application peuvent communiquer les uns avec les autres, même s’ils se trouvent sur des plateformes différentes. SOAP est basé sur XML, donc il est explicite. Le sacrifice de rendre le SOAP facilement compréhensible est la taille ; Les messages SOAP sont plus volumineux que les messages dans les protocoles comparables. SOAP a été conçu pour répartir les applications monolithiques dans un formulaire multicomposant sans perte de sécurité ou de contrôle. WCF a donc été conçu pour fonctionner avec ce type de système, contrairement à gRPC, qui commençait comme un système distribué. WCF a traité certaines de ces limitations en développant et en documentant des protocoles d’extension propriétaires pour la pile SOAP, mais au détriment d’un manque de prise en charge d’autres plateformes.

Windows Communication Foundation est une infrastructure pour la création de services. Il a été conçu au début des 2000 pour aider les développeurs utilisant une SOA précoce à gérer la complexité de l’utilisation de SOAP. Bien qu’il supprime la nécessité pour les développeurs d’écrire leurs propres protocoles SOAP, WCF utilise toujours SOAP pour permettre l’interopérabilité avec d’autres systèmes. WCF a également été conçu pour fournir des solutions sur plusieurs protocoles (HTTP/1.1, net. TCP, etc.).

## <a name="microservices"></a>Microservices

Dans les architectures de microservices, les applications volumineuses sont générées sous la forme d’une collection de services modulaires plus petits. Chaque composant effectue une tâche ou un processus spécifique, et les composants sont conçus pour fonctionner de manière interdépendante, mais peuvent être isolés si nécessaire.

Les microservices présentent les avantages suivants :

- Les modifications et les mises à niveau peuvent être gérées indépendamment.
- La gestion des erreurs est plus efficace, car les problèmes peuvent être suivis à des services spécifiques qui sont ensuite isolés, reconstruits, testés et redéployés indépendamment des autres services.
- L’extensibilité peut être limitée à des instances ou des services spécifiques plutôt qu’à l’application entière.
- Le développement peut avoir lieu dans plusieurs équipes, avec moins de frottements que lorsque de nombreuses équipes travaillent sur un même code base.

Le passage à l’augmentation de la virtualisation, des cloud computing, des conteneurs et des Internet des objets a contribué à la montée en continu des microservices. Mais les microservices ne sont pas sans les défis. L’infrastructure fragmentée/décentralisée insiste sur le besoin de simplicité et de rapidité lors de la communication entre les services. Cela attire l’attention sur la nature parfois laborieuse et convertie de SOAP.

Dans cet environnement, gRPC a été lancé, 10 ans après la première publication de WCF par Microsoft. Développé directement à partir de la Stubby (Internal infrastructure RPC) de Google, gRPC n’a jamais été basé sur les mêmes normes et protocoles qui avaient informé les paramètres de nombreux RPC antérieurs. Et gRPC n’était jamais basé sur HTTP/2. C’est la raison pour laquelle elle peut s’appuyer sur les nouvelles fonctionnalités fournies par le protocole de transport avancé. En particulier, la diffusion bidirectionnelle, la messagerie binaire et le multiplexage.

## <a name="about-this-guide"></a>À propos de ce guide

Ce guide couvre les principales fonctionnalités de gRPC. Les premiers chapitres ont une vue d’ensemble des principales fonctionnalités de WCF et les comparent à ceux d’gRPC. Il identifie l’emplacement des corrélations directes entre WCF et gRPC et également où gRPC offre un avantage. Lorsqu’il n’existe aucune corrélation entre WCF et gRPC, ou lorsque gRPC n’est pas en mesure d’offrir une solution équivalente à WCF, ce guide suggère des solutions de contournement ou l’endroit où accéder pour plus d’informations.

À l’aide d’un ensemble d’exemples d’applications WCF, le chapitre 5 est une présentation approfondie de la conversion des principaux types de service WCF (requête-réponse simple, unidirectionnelle et streaming) vers leurs équivalents dans gRPC.

La dernière section du livre explique comment obtenir le meilleur de gRPC dans la pratique. Cette section contient des informations sur l’utilisation d’autres outils, tels que les conteneurs dockers ou Kubernetes, pour tirer parti de l’efficacité de gRPC. Il comprend également un aperçu détaillé de la surveillance avec la journalisation, les métriques et le suivi distribué.

## <a name="who-this-guide-is-for"></a>Audience à laquelle ce guide est destiné

Ce guide a été rédigé pour les développeurs qui travaillent dans .NET Framework ou .NET Core qui ont utilisé WCF et qui cherchent à migrer leurs applications vers un environnement RPC moderne pour .NET Core 3,0 et versions ultérieures. Le guide peut également être utile plus généralement pour les développeurs qui effectuent une mise à niveau vers .NET ou en envisageant la mise à niveau, et qui souhaitent utiliser les outils gRPC intégrés.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](grpc-overview.md)
