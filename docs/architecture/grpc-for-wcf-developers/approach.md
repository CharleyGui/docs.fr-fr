---
title: Comment gRPC approche RPC-gRPC pour les développeurs WCF
description: Comparaison des principales fonctionnalités de WCF à gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: b924d2f20b54de2d6476a0b27626d5dd7fd0986f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711479"
---
# <a name="how-grpc-approaches-rpc"></a>Comment gRPC approche RPC

Windows Communication Foundation (WCF) et gRPC sont des implémentations du modèle d' *appel de procédure distante* (RPC). Ce modèle vise à effectuer des appels à des services qui s’exécutent sur un autre ordinateur, ou dans un processus différent, à fonctionner de manière transparente, comme les appels de méthode dans l’application cliente. Alors que les objectifs de WCF et de gRPC sont les mêmes, les détails de l’implémentation sont très différents.

Le tableau suivant montre comment les fonctionnalités clés de WCF sont liées à gRPC et où vous trouverez des explications plus détaillées.

| Fonctionnalités | WCF | gRPC |
| -------- | --- | ---- |
| Objectif | Séparer le code d’entreprise de l’implémentation réseau. | Séparez le code d’entreprise de la définition d’interface et de l’implémentation réseau. |
| Définir des services et des messages (chapitres 3-4)  | Contrat de service, contrat d’opération et contrat de données. | Utilise le fichier proto pour déclarer des services et des messages. |
| Langue (chapitres 3-5) | Contrats écrits en C# Visual Basic ou. | Langue de la mémoire tampon du protocole. |
| Format câble (chapitre 3) | Configurable, y compris SOAP/XML, XML brut, JSON et binaire .NET. | Format binaire du tampon de protocole (bien qu’il soit possible d’utiliser d’autres formats).
| Interopérabilité (chapitre 4) | Lors de l’utilisation de SOAP sur HTTP. | Support officiel : .NET, Java, Python, JavaScript, C/C++, Go, rouille, Ruby, SWIFT, DART, php. Support non officiel pour d’autres langages de la communauté. |
| Mise en réseau (chapitre 4) | Configuré au moment de l’exécution. Basculez entre NetTCP, HTTP et MSMQ. | HTTP/2, actuellement sur TCP uniquement avec ASP.NET Core gRPC. |
| Approche (chapitre 4) | Génération du runtime de la sérialisation, de la désérialisation et du code de mise en réseau dans les classes de base. | Génération au moment de la génération de la sérialisation, de la désérialisation et du code de mise en réseau dans les classes de base. |
| Sécurité (chapitre 6) | Authentification, WS-Security, chiffrement des messages. | Informations d’identification, sécurité de ASP.NET Core, mise en réseau TLS. |

>[!div class="step-by-step"]
>[Précédent](grpc-overview.md)
>[Suivant](interface-definition-language.md)
