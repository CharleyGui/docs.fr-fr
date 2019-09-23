---
title: Liaisons et transports WCF-gRPC pour les développeurs WCF
description: Découvrez comment les différents transports et liaisons WCF sont comparés à gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 50bac73ee68d7156fc5fed55dfffb3ba7f2de924
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184056"
---
# <a name="wcf-bindings-and-transports"></a>Liaisons et transports WCF

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

WCF possède un grand nombre de *liaisons* intégrées différentes qui spécifient des protocoles réseau, des formats de transmission et d’autres détails d’implémentation. gRPC possède un seul protocole réseau et un seul format de câble (techniquement, le format de câble *peut* être personnalisé, mais cela n’entre pas dans le cadre de cet ouvrage). Vous découvrirez probablement que gRPC offre la meilleure solution dans la plupart des cas. Ce qui suit est une brève discussion sur les liaisons WCF les plus pertinentes et sur leur comparaison avec leur équivalent dans gRPC.

## <a name="nettcp"></a>NetTCP

La liaison NetTCP de WCF permet les connexions persistantes, les petits messages et la messagerie bidirectionnelle, mais fonctionne uniquement entre les clients et les serveurs .NET. gRPC offre les mêmes fonctionnalités, mais est pris en charge sur plusieurs plateformes et langages de programmation. gRPC possède un grand nombre des fonctionnalités de la liaison WCF NetTCP, bien qu’elles ne soient pas toujours implémentées de la même façon. Par exemple, dans WCF, le chiffrement est contrôlé par la configuration et géré dans le Framework. Dans gRPC, le chiffrement est effectué au niveau de la connexion à l’aide de HTTP/2 sur TLS.

## <a name="http"></a>HTTP

Le BasicHttpBinding de WCF est généralement basé sur du texte, avec SOAP comme format de câble, et est très lent par les normes des applications modernes en réseau. Elle est utilisée uniquement pour fournir une interopérabilité multiplateforme, ou une connexion sur une infrastructure Internet. L’équivalent dans gRPC, car il utilise HTTP/2 comme couche de transport sous-jacente avec le format de transmission binaire Protobuf pour les messages, peut offrir des performances de niveau de service NetTCP, mais avec une interopérabilité multiplateforme complète avec tous les langages de programmation modernes et infrastructures.

## <a name="named-pipes"></a>Canaux nommés

WCF a fourni une liaison de canaux nommés pour la communication entre les processus sur le même ordinateur physique. Les canaux nommés ne sont pas pris en charge par la première version de ASP.NET Core gRPC.

En dehors de Windows, les fonctionnalités fournies par les canaux nommés sont généralement fournies par les sockets de domaine UNIX. Ces sockets sont des sockets TCP standard représentés par des adresses de système de fichiers, par `/var/run/docker.sock`exemple, que gRPC peut utiliser en tant que client et serveur. Si vous devez utiliser la fonctionnalité de style canaux nommés sur Windows, la prochaine mise à jour vers Windows 10 et Windows Server, dans 2019 4e trimestre, ajoute des sockets de domaine en tant que fonctionnalité Native entièrement prise en charge dans Windows. Par conséquent, les services gRPC s’exécutant sur ces versions et versions ultérieures de Windows (ou sur Linux) peuvent utiliser des sockets de domaine plutôt que des canaux nommés. Toutefois, si votre équipe ne parvient pas à effectuer la mise à jour vers la dernière version de Windows, vous devez utiliser des sockets TCP localhost. Les problèmes de sécurité liés à l’utilisation des sockets TCP locaux peuvent être résolus par l’utilisation de l’authentification par certificat entre le client et le serveur.

## <a name="msmq"></a>MSMQ

MSMQ est une file d’attente de messages Windows propriétaire. La liaison de WCF à MSMQ active les demandes « déclencher et oublier » de clients qui peuvent être traitées à tout moment à l’avenir. gRPC ne fournit pas en mode natif les fonctionnalités de file d’attente de messages. La meilleure solution consiste à utiliser directement un système de messagerie comme Azure Service Bus, RabbitMQ ou Kafka. Cela peut être implémenté avec le client qui place des messages directement dans la file d’attente, ou un service de diffusion en continu client gRPC qui met en file d’attente les messages.

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (également appelé WCF REST), avec les `WebGet` attributs et `WebInvoke` , vous permettait de développer des API ReSTful qui pourraient parler JSON à un moment où ce était moins courant. Par conséquent, si vous avez une API RESTful générée avec WCF REST, envisagez de la migrer vers une application API Web standard ASP.NET Core MVC, qui fournirait des fonctionnalités équivalentes, plutôt que de les convertir en gRPC.

>[!div class="step-by-step"]
>[Précédent](wcf-endpoints-grpc-methods.md)
>[Suivant](rpc-types.md)
