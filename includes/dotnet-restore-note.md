---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102738"
---
Vous n’avez pas à exécuter [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , car il est exécuté implicitement par toutes les commandes qui nécessitent une restauration, comme,,,, `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` et `dotnet pack` . Pour désactiver la restauration implicite, utilisez l' `--no-restore` option.

La `dotnet restore` commande est toujours utile dans certains scénarios où la restauration explicite est appropriée, comme les [Builds d’intégration continue dans Azure DevOps services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de génération qui doivent contrôler explicitement le moment où la restauration se produit.

Pour plus d’informations sur la gestion des flux NuGet, consultez la [ `dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).
