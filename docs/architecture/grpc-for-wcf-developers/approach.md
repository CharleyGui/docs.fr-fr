---
title: Comment gRPC approche RPC-gRPC pour les développeurs WCF
description: Comparaison des principales fonctionnalités de WCF à gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 1ebfd102217c9685c5ff5200386c642b2017e98f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968128"
---
# <a name="how-grpc-approaches-rpc"></a>Comment gRPC approche RPC

Windows Communication Foundation (WCF) et gRPC sont des implémentations du modèle d' *appel de procédure distante* (RPC), qui vise à faire des appels aux services s’exécutant sur un autre ordinateur, ou dans un processus différent, à fonctionner en toute transparence comme s’il s’agissait d’appels de méthode dans l’application cliente. Alors que les objectifs de WCF et de gRPC sont les mêmes, les détails de l’implémentation sont très différents.

Le tableau suivant montre comment les fonctionnalités clés de WCF sont liées à gRPC et où vous trouverez des explications plus détaillées dans le reste du livre.

| Fonctionnalités | WCF | gRPC |
| -------- | --- | ---- |
| Objectif | Séparer le code d’entreprise de l’implémentation réseau | Séparer le code d’entreprise de la définition d’interface et de l’implémentation réseau |
| Définir des services et des messages (chapitre 3-4)  | Contrat de service, contrat d’opération et contrat de données | Utilise un fichier proto pour déclarer des services et des messages |
| Langue (chapitre 3-5) | Contrats écrits en C# Visual Basic | Langue de la mémoire tampon du protocole |
| Format câble (chapitre 3) | Configurable, y compris SOAP/XML, XML brut, JSON, .NET Binary, etc. | Format binaire du tampon de protocole (bien qu’il soit possible d’utiliser d’autres formats).
| Interopérabilité (chapitre 4) | Lors de l’utilisation de SOAP sur HTTP | Support officiel : .NET, Java, Python, JavaScript, C/C++, Go, rouille, Ruby, SWIFT, DART, php. Support non officiel pour d’autres langages de la communauté. |
| Mise en réseau (chapitre 4) | Configuré au moment de l’exécution. Basculez entre NetTCP, HTTP, MSMQ, et ainsi de suite. | HTTP/2, actuellement sur TCP uniquement avec ASP.NET Core gRPC. |
| Approche (chapitre 4) | Génération de la sérialisation/Deserialization et du code de mise en réseau dans les classes de base | Génération au moment de la génération du/Deserialization de sérialisation et du code réseau dans les classes de base |
| Sécurité (chapitre 6) | Authentification, WS-Security, chiffrement des messages | Informations d’identification, sécurité de la ASP.NET Core, mise en réseau TLS |

>[!div class="step-by-step"]
>[Précédent](grpc-overview.md)
>[Suivant](interface-definition-language.md)
