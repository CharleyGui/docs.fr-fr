---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179987"
---
> [!NOTE]
> En commençant par .NET Core 2.0, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) vous n’avez pas à courir parce qu’il est `dotnet build` exécuté `dotnet run`implicitement par toutes les commandes qui nécessitent une restauration pour se produire, tels que et . Cette commande reste néanmoins valide dans certains scénarios où une restauration explicite est nécessaire, comme des [builds d’intégration continue dans Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou dans les systèmes de génération qui doivent contrôler explicitement le moment auquel la restauration se produit.
>
> Cette commande prend également en charge les options de `dotnet restore` quand elles sont passées sous leur forme longue (par exemple `--source`). Les options sous forme abrégée, comme `-s`, ne sont pas prises en charge.
