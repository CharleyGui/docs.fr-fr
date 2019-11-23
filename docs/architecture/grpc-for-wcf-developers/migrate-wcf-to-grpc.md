---
title: Migrer une solution WCF vers gRPC-gRPC pour les développeurs WCF
description: Comment migrer différents types de service WCF vers l’équivalent dans gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 33823d20e1593323a03da12981c5a4534c4d491a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971772"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrer une solution WCF vers gRPC

Ce chapitre aborde l’utilisation des projets ASP.NET Core 3,0 gRPC et montre comment migrer différents types de service WCF vers l’équivalent gRPC :

- Créez un projet ASP.NET Core 3,0 gRPC.
- Opérations de requête-réponse simples pour gRPC RPC unaire.
- Opérations unidirectionnelles vers gRPC client streaming RPC.
- Services duplex intégral vers gRPC de diffusion en continu bidirectionnelle RPC.

Il y a également une comparaison entre l’utilisation de services de streaming et les champs répétés pour le renvoi de jeux de données, ainsi que l’utilisation des bibliothèques clientes à la fin du chapitre.

L’exemple d’application WCF est un stub minimal d’un ensemble de services commerciaux boursiers, à l’aide de la bibliothèque de conteneurs IoC (inversion Open source of Control) appelée *Autofac* pour l’injection de dépendances. Il comprend trois services, un pour chaque type de service WCF. Les services seront abordés plus en détail dans les sections suivantes. Les solutions peuvent être téléchargées à partir de [dotnet-architecture/GRPC-pour-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) sur GitHub. Les services utilisent des données factices pour réduire les dépendances externes.

Les exemples incluent les implémentations WCF et gRPC de chaque service.

>[!div class="step-by-step"]
>[Précédent](ws-protocols.md)
>[Suivant](create-project.md)
