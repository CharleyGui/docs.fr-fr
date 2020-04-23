---
ms.openlocfilehash: 6c04437c2a211b244e6c5eda0893b267c59668e9
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102765"
---
Vous n’avez pas [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) à courir parce qu’il est géré implicitement par `dotnet new`toutes `dotnet build` `dotnet run`les `dotnet test`commandes qui nécessitent une restauration à se produire, tels que , , , , `dotnet publish`, et `dotnet pack`. Pour désactiver la restauration `--no-restore` implicite, utilisez l’option.

La `dotnet restore` commande est encore utile dans certains scénarios où la restauration explicite est logique, comme [l’intégration continue s’accumule dans Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de construction qui doivent contrôler explicitement lorsque la restauration se produit.

Pour plus d’informations sur la façon [ `dotnet restore` ](../docs/core/tools/dotnet-restore.md)de gérer les flux NuGet, consultez la documentation .

Cette commande `dotnet restore` prend en charge les options lorsqu’elle est passée sous la forme longue (par exemple, `--source`). Les options sous forme abrégée, comme `-s`, ne sont pas prises en charge.
