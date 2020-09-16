---
ms.openlocfilehash: 19002cce40fdc929716a761a5e01303be4decb35
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537824"
---
Vous n’avez pas à exécuter [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , car il est exécuté implicitement par toutes les commandes qui nécessitent une restauration, comme,,,, `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` et `dotnet pack` . Pour désactiver la restauration implicite, utilisez l' `--no-restore` option.

La `dotnet restore` commande est toujours utile dans certains scénarios où la restauration explicite est appropriée, comme les [Builds d’intégration continue dans Azure DevOps services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de génération qui doivent contrôler explicitement le moment où la restauration se produit.

Pour plus d’informations sur la gestion des flux NuGet, consultez la [ `dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).

Cette commande prend en charge les `dotnet restore` options quand elles sont transmises sous la forme longue (par exemple, `--source` ). Les options sous forme abrégée, comme `-s`, ne sont pas prises en charge.
