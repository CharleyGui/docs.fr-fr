---
title: Liaisons et transports WCF - gRPC pour les développeurs WCF
description: Découvrez comment les différentes liaisons et transports WCF se comparent à gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 3a295268b486578c70c2c98f1d05f89070daaeb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147722"
---
# <a name="wcf-bindings-and-transports"></a>Liaisons WCF et transports

Windows Communication Foundation (WCF) dispose de *liaisons intégrées* qui spécifient différents protocoles réseau, formats de fils et autres détails de mise en œuvre. gRPC n’a en fait qu’un seul protocole réseau et un format de fil. (Techniquement, vous *pouvez* personnaliser le format de fil, mais c’est au-delà de la portée de ce livre.) Vous êtes susceptible de découvrir que gRPC offre la meilleure solution dans la plupart des cas.

Ce qui suit est une brève discussion sur les liaisons WCF les plus pertinentes et comment ils se comparent à leurs équivalents dans gRPC.

## <a name="nettcp"></a>NetTCP (en)

La liaison NetTCP de WCF permet des connexions persistantes, de petits messages et des messages bidirectionnels. Mais il ne fonctionne qu’entre les clients .NET et les serveurs. gRPC permet la même fonctionnalité, mais est pris en charge sur plusieurs langages de programmation et plates-formes.

gRPC a de nombreuses fonctionnalités de la liaison NetTCP de WCF, mais elles ne sont pas toujours mises en œuvre de la même manière. Par exemple, dans WCF, le chiffrement est contrôlé par la configuration et géré dans le cadre. Dans gRPC, le chiffrement est atteint au niveau de connexion par HTTP/2 sur TLS.

## <a name="http"></a>HTTP

La liaison WCF appelée BasicHttpBinding est généralement basée sur le texte et utilise SOAP comme format fil. Il est lent par rapport à la liaison NetTCP. Il est généralement utilisé pour fournir l’interopérabilité multiplateforme, ou la connexion sur l’infrastructure Internet.

L’équivalent dans gRPC utilise HTTP/2 comme couche de transport sous-jacente avec le format binaire de fil Protobuf pour les messages. Ainsi, il peut offrir des performances au niveau de service NetTCP et l’interopérabilité complète inter-plateforme avec tous les langages de programmation modernes et les cadres.

## <a name="named-pipes"></a>Canaux nommés

WCF a fourni une liaison *de tuyaux nommées* pour la communication entre les processus sur la même machine physique. La première version de ASP.NET Core gRPC ne prend pas en charge les tuyaux nommés. L’ajout de la prise de service des clients et des serveurs pour les tuyaux nommés (et les prises de domaine Unix) est un objectif pour une version future.

## <a name="msmq"></a>MSMQ

MSMQ est une file d’attente de messages Windows propriétaire. La liaison de WCF à MSMQ permet de « tirer et d’oublier » les demandes de clients qui pourraient être traitées à tout moment à l’avenir. gRPC ne fournit pas de fonctionnalité de file d’attente de message.

La meilleure alternative est d’utiliser directement un système de messagerie comme Azure Service Bus, RabbitMQ ou Kafka. Vous pouvez implémenter cela avec le client plaçant des messages directement sur la file d’attente, ou un service de streaming client gRPC qui enqueue les messages.

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (également connu sous le `WebGet` nom `WebInvoke` WCF REST), avec le et les attributs, vous a permis de développer des API RESTful qui pourraient parler JSON à une époque où cela était moins fréquent. Si vous avez une API RESTful construite avec WCF REST, envisagez de la migrer vers une application D’API Web CŒur ASP.NET. Cette migration fournirait la même fonctionnalité qu’une conversion en gRPC.

>[!div class="step-by-step"]
>[Suivant précédent](wcf-endpoints-grpc-methods.md)
>[Next](rpc-types.md)
