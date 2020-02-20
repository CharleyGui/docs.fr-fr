---
title: Liaisons et transports WCF-gRPC pour les développeurs WCF
description: Découvrez comment les différents transports et liaisons WCF sont comparés à gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: ebe324eace8f5f418b920c59f6d72eaaa686ef02
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503348"
---
# <a name="wcf-bindings-and-transports"></a>Liaisons WCF et transports

Windows Communication Foundation (WCF) a des *liaisons* intégrées qui spécifient différents protocoles réseau, formats de transmission et d’autres détails d’implémentation. gRPC possède un seul protocole réseau et un seul format de câble. (Techniquement, vous *pouvez* personnaliser le format de câble, mais cela dépasse le cadre de ce document.) Vous pouvez découvrir que gRPC offre la meilleure solution dans la plupart des cas. 

Ce qui suit est une brève discussion sur les liaisons WCF les plus pertinentes et sur leur comparaison avec leurs équivalents dans gRPC.

## <a name="nettcp"></a>NetTCP

La liaison NetTCP de WCF permet d’obtenir des connexions persistantes, des messages de petite taille et une messagerie bidirectionnelle. Mais il fonctionne uniquement entre les clients et les serveurs .NET. gRPC offre les mêmes fonctionnalités, mais est pris en charge sur plusieurs plateformes et langages de programmation. 

gRPC comporte de nombreuses fonctionnalités de liaison NetTCP de WCF, mais elles ne sont pas toujours implémentées de la même façon. Par exemple, dans WCF, le chiffrement est contrôlé par la configuration et géré dans le Framework. Dans gRPC, le chiffrement est effectué au niveau de la connexion via HTTP/2 sur TLS.

## <a name="http"></a>HTTP

La liaison WCF appelée BasicHttpBinding est généralement basée sur du texte et utilise SOAP comme format de câble. Elle est lente par rapport à la liaison NetTCP. Il est généralement utilisé pour fournir une interopérabilité multiplateforme, ou une connexion sur une infrastructure Internet. 

L’équivalent dans gRPC utilise HTTP/2 comme couche de transport sous-jacente avec le format de transmission binaire Protobuf pour les messages. Il peut donc offrir des performances au niveau du service NetTCP et à l’interopérabilité multiplateforme complète avec tous les langages et infrastructures de programmation modernes.

## <a name="named-pipes"></a>Canaux nommés

WCF a fourni une liaison de *canaux nommés* pour la communication entre les processus sur le même ordinateur physique. La première version de ASP.NET Core gRPC ne prend pas en charge les canaux nommés. L’ajout de la prise en charge du client et du serveur pour les canaux nommés (et les sockets de domaine UNIX) est un objectif pour une version ultérieure.

## <a name="msmq"></a>MSMQ

MSMQ est une file d’attente de messages Windows propriétaire. La liaison de WCF à MSMQ active les demandes « déclencher et oublier » de clients qui peuvent être traitées à tout moment à l’avenir. gRPC ne fournit pas en mode natif les fonctionnalités de file d’attente de messages. 

La meilleure solution consiste à utiliser directement un système de messagerie comme Azure Service Bus, RabbitMQ ou Kafka. Vous pouvez l’implémenter avec le client en plaçant des messages directement dans la file d’attente, ou un service de diffusion en continu client gRPC qui met en file d’attente les messages.

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (également appelé WCF REST), avec les attributs `WebGet` et `WebInvoke`, vous permettait de développer des API RESTful qui pourraient parler JSON à un moment où cela était moins courant. Si vous avez une API RESTful générée avec WCF REST, envisagez de la migrer vers une application d’API Web ASP.NET Core MVC standard. Cette migration fournit les mêmes fonctionnalités qu’une conversion vers gRPC.

>[!div class="step-by-step"]
>[Précédent](wcf-endpoints-grpc-methods.md)
>[Suivant](rpc-types.md)
