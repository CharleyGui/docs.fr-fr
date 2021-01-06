---
title: Protocoles WS-*-gRPC pour les développeurs WCF
description: Examen des protocoles WS-* pris en charge par WCF et des alternatives disponibles avec gRPC
author: markrendle
ms.date: 12/15/2020
ms.openlocfilehash: d6fffdd5153c799c78ad949a3b16fa72e9612e43
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938479"
---
# <a name="ws--protocols"></a>WS- \* protocoles

L’un des avantages réels de l’utilisation de Windows Communication Foundation (WCF) était qu’il prenait en charge un grand nombre des protocoles _WS- \*_ standard existants. Cette section aborde brièvement la manière dont gRPC gère les mêmes WS- \* Protocols et explique les options disponibles lorsqu’il n’existe aucune alternative.

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a>Échange de métadonnées : WS-Policy, WS-Discovery, etc.

Les services SOAP exposent les documents de schéma Web Services Description Language (WSDL) avec des informations telles que les formats de données, les opérations ou les options de communication. Vous pouvez utiliser ce schéma pour générer le code client.

gRPC fonctionne de façon optimale lorsque les serveurs et les clients sont générés à partir des mêmes `.proto` fichiers, mais une extension facultative de réflexion de serveur permet d’exposer des informations dynamiques à partir d’un serveur en cours d’exécution. Pour plus d’informations, consultez le package NuGet [GRPC. Reflection](https://nuget.org/packages/Grpc.Reflection) et l’article sur la [réflexion de serveur C# GRPC](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .

Le protocole de WS-Discovery est utilisé pour rechercher des services sur un réseau local. les services gRPC sont situés dans DNS ou dans un registre de service tel que consul ou ZooKeeper.

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a>Sécurité : WS-Security, WS-Federation, chiffrement XML, etc.

La sécurité, l’authentification et l’autorisation sont couvertes plus en détail dans le [chapitre 6](security.md). Toutefois, il est intéressant de noter que, contrairement à WCF, gRPC ne prend pas en charge WS-Security, WS-Federation ou le chiffrement XML. Même dans ce cas, gRPC offre une excellente sécurité. Tout le trafic réseau gRPC est automatiquement chiffré lorsqu’il utilise HTTP/2 sur TLS. Vous pouvez utiliser des certificats X509 pour l’authentification client/serveur mutuelle.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC ne fournit pas d’équivalent à WS-ReliableMessaging. La sémantique de nouvelle tentative doit être gérée dans le code, éventuellement avec une bibliothèque telle que [Polly](https://github.com/App-vNext/Polly). Lorsque vous exécutez dans Kubernetes ou des environnements d’orchestration similaires, les [maillages de service](service-mesh.md) peuvent également aider à fournir une messagerie fiable entre les services.

## <a name="ws-transaction-ws-coordination"></a>WS-transaction, WS-Coordination

L’implémentation par WCF des transactions distribuées utilise Microsoft Distributed Transaction Coordinator (MSDTC). Il fonctionne avec les gestionnaires de ressources qui le prennent spécifiquement en charge, comme SQL Server, MSMQ ou les systèmes de fichiers Windows. Il n’existe pas encore d’équivalent dans le monde des microservices moderne, en partie en raison de la plus large gamme de technologies utilisées. Pour plus d’informations sur les transactions, consultez [l’annexe a](appendix.md).

>[!div class="step-by-step"]
>[Précédent](error-handling.md) 
> [Suivant](migrate-wcf-to-grpc.md)
