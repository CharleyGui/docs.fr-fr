---
title: Migrer une solution WCF vers gRPC-gRPC pour les développeurs WCF
description: Migration de différents types de services WCF vers l’équivalent dans gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 12e724ab46a33547d352da7a604a5a994e617bc2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628512"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrer une solution WCF vers gRPC

Ce chapitre décrit comment utiliser des projets ASP.NET Core 3,0 gRPC et illustre la migration de différents types de services Windows Communication Foundation (WCF) vers l’équivalent gRPC :

- Créez un projet ASP.NET Core 3,0 gRPC.
- Opérations de requête-réponse simples pour gRPC RPC unaire.
- Opérations unidirectionnelles vers gRPC client streaming RPC.
- Services duplex intégral vers gRPC de diffusion en continu bidirectionnelle RPC.

Il y a également une comparaison entre l’utilisation de services de streaming et les champs répétés pour le retour de jeux de données, et il existe une discussion sur l’utilisation des bibliothèques clientes à la fin du chapitre.

L’exemple d’application WCF est un stub minimal d’un ensemble de services commerciaux boursiers. Il utilise la bibliothèque de conteneurs inversion Open source de Control (IoC) appelée Autofac pour l’injection de dépendances. Il comprend trois services, un pour chaque type de service WCF. Les services seront abordés plus en détail dans les sections suivantes. Vous pouvez télécharger les solutions à partir de [dotnet-architecture/GRPC-pour-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) sur GitHub. Les services utilisent des données factices pour réduire les dépendances externes.

Les exemples incluent les implémentations WCF et gRPC de chaque service.

>[!div class="step-by-step"]
>[Précédent](ws-protocols.md)
>[Suivant](create-project.md)
