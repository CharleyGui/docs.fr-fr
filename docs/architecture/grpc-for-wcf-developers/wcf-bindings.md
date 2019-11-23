---
title: Liaisons et transports WCF-gRPC pour les développeurs WCF
description: Découvrez comment les différents transports et liaisons WCF sont comparés à gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 233e3d030bc1f4450bd5cd6a7d7770486ca9e95a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966902"
---
# <a name="wcf-bindings-and-transports"></a>Liaisons WCF et transports

WCF possède un grand nombre de *liaisons* intégrées différentes qui spécifient des protocoles réseau, des formats de transmission et d’autres détails d’implémentation. gRPC possède un seul protocole réseau et un seul format de câble (techniquement, le format de câble *peut* être personnalisé, mais cela n’entre pas dans le cadre de cet ouvrage). Vous découvrirez probablement que gRPC offre la meilleure solution dans la plupart des cas. Ce qui suit est une brève discussion sur les liaisons WCF les plus pertinentes et sur leur comparaison avec leur équivalent dans gRPC.

## <a name="nettcp"></a>NetTCP

La liaison NetTCP de WCF permet les connexions persistantes, les petits messages et la messagerie bidirectionnelle, mais fonctionne uniquement entre les clients et les serveurs .NET. gRPC offre les mêmes fonctionnalités, mais est pris en charge sur plusieurs plateformes et langages de programmation. gRPC possède un grand nombre des fonctionnalités de la liaison WCF NetTCP, bien qu’elles ne soient pas toujours implémentées de la même façon. Par exemple, dans WCF, le chiffrement est contrôlé par la configuration et géré dans le Framework. Dans gRPC, le chiffrement est effectué au niveau de la connexion à l’aide de HTTP/2 sur TLS.

## <a name="http"></a>HTTP

Le BasicHttpBinding de WCF est généralement basé sur du texte, avec SOAP comme format de câble, et est lent comparé à la liaison NetTCP. Il est généralement utilisé pour fournir une interopérabilité multiplateforme, ou une connexion sur une infrastructure Internet. L’équivalent dans gRPC, car il utilise HTTP/2 comme couche de transport sous-jacente avec le format de transmission binaire Protobuf pour les messages, peut offrir des performances de niveau de service NetTCP, mais avec une interopérabilité multiplateforme complète avec tous les langages de programmation modernes et infrastructures.

## <a name="named-pipes"></a>Canaux nommés

WCF a fourni une liaison de canaux nommés pour la communication entre les processus sur le même ordinateur physique. Les canaux nommés ne sont pas pris en charge par la première version de ASP.NET Core gRPC. L’ajout de la prise en charge du client et du serveur pour les canaux nommés (et les sockets de domaine UNIX) est un objectif pour une version ultérieure.

## <a name="msmq"></a>MSMQ

MSMQ est une file d’attente de messages Windows propriétaire. La liaison de WCF à MSMQ active les demandes « déclencher et oublier » de clients qui peuvent être traitées à tout moment à l’avenir. gRPC ne fournit pas en mode natif les fonctionnalités de file d’attente de messages. La meilleure solution consiste à utiliser directement un système de messagerie comme Azure Service Bus, RabbitMQ ou Kafka. Cela peut être implémenté avec le client qui place des messages directement dans la file d’attente, ou un service de diffusion en continu client gRPC qui met en file d’attente les messages.

## <a name="webhttpbinding"></a>WebHttpBinding

Le script WebHttpBinding (également appelé WCF ReST), avec les attributs `WebGet` et `WebInvoke`, vous permettait de développer des API ReSTful qui pourraient parler JSON à un moment où ce était moins courant. Par conséquent, si vous avez une API RESTful générée avec WCF REST, envisagez de la migrer vers une application API Web standard ASP.NET Core MVC, qui fournirait des fonctionnalités équivalentes, plutôt que de les convertir en gRPC.

>[!div class="step-by-step"]
>[Précédent](wcf-endpoints-grpc-methods.md)
>[Suivant](rpc-types.md)
