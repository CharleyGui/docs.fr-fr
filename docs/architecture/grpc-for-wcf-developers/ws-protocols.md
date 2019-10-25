---
title: Protocoles WS-*-gRPC pour les développeurs WCF
description: Examen des protocoles WS-* pris en charge par WCF et des alternatives disponibles avec gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4e7b80df182fb69cc51e14738e59ad87efaf5dd2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846039"
---
# <a name="ws--protocols"></a>Protocoles WS-\*

L’un des avantages réels de l’utilisation de Windows Communication Foundation (WCF) était qu’il prenait en charge un grand nombre des protocoles _WS-\*_ standard existants. Cette section aborde brièvement la manière dont gRPC gère les mêmes protocoles WS-\* et décrit les options disponibles lorsqu’il n’existe aucune alternative.

## <a name="metadata-exchange---ws-policy-ws-discovery-and-so-on"></a>Échange de métadonnées-WS-Policy, WS-Discovery, etc.

Les services SOAP exposent les documents de schéma Web Services Description Language (WSDL) avec des informations telles que les formats de données, les opérations ou les options de communication. Ce schéma peut être utilisé pour générer le code client.

gRPC fonctionne de façon optimale lorsque les serveurs et les clients sont générés à partir des mêmes fichiers de `.proto`, mais une extension de serveur en option de réflexion de serveur permet d’exposer des informations dynamiques à partir d’un serveur en cours d’exécution. Pour plus d’informations, consultez le package NuGet [GRPC. Reflection](https://nuget.org/packages/Grpc.Reflection) et l’article sur la [réflexion de serveur GRPC C# ](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .

Le protocole WS-Discovery est utilisé pour rechercher des services sur un réseau local. les services gRPC se trouvent généralement à l’aide de DNS ou d’un registre de service, tel que consul ou ZooKeeper.

## <a name="security--ws-security-ws-federation-xml-encryption-and-so-on"></a>Sécurité : WS-Security, WS-Federation, chiffrement XML, etc.

La sécurité, l’authentification et l’autorisation sont couvertes plus en détail dans le [chapitre 6](security.md). Toutefois, il est intéressant de noter que, contrairement à WCF, gRPC ne prend pas en charge WS-Security, WS Federation ou le chiffrement XML. Même dans ce cas, gRPC fournit une excellente sécurité. tout le trafic réseau gRPC est automatiquement chiffré lors de l’utilisation du protocole HTTP/2 sur TLS, et les certificats X509 peuvent être utilisés pour l’authentification client/serveur mutuelle.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC ne fournit pas d’équivalent à WS-ReliableMessaging. La sémantique de nouvelle tentative doit être gérée dans le code, éventuellement avec une bibliothèque telle que [Polly](https://github.com/App-vNext/Polly). En cas d’exécution dans Kubernetes ou dans des environnements d’orchestration similaires, les [maillages de service](service-mesh.md) peuvent également aider à fournir une messagerie fiable entre les services.

## <a name="ws-transaction-ws-coordination"></a>WS-transaction, WS-coordination

L’implémentation WCF des transactions distribuées utilise Windows Distributed Transaction Coordinator ou MSDTC. Il fonctionne avec les gestionnaires de ressources qui le prennent spécifiquement en charge, comme SQL Server, MSMQ ou les systèmes de fichiers Windows. Dans le monde des microservices modernes, en partie en raison de la plus large gamme de technologies en cours d’utilisation, il n’y a pas encore d’équivalent. Pour plus d’informations sur les transactions, consultez [l’annexe a](appendix.md).

>[!div class="step-by-step"]
>[Précédent](error-handling.md)
>[Suivant](migrate-wcf-to-grpc.md)
