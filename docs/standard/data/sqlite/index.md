---
title: Vue d’ensemble
ms.date: 12/13/2019
description: Vue d’ensemble de Microsoft. Data. sqlite
ms.openlocfilehash: 7c952848f7e7ea04f11fe9340f77a1f376a1be07
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552438"
---
# <a name="microsoftdatasqlite-overview"></a>Vue d’ensemble de Microsoft. Data. sqlite

Microsoft. Data. sqlite est un fournisseur [ADO.net](../../../framework/data/adonet/index.md) léger pour SQLite. Le fournisseur [Entity Framework Core](/ef/core/) pour SQLite s’appuie sur cette bibliothèque. Toutefois, il peut également être utilisé indépendamment ou avec d’autres bibliothèques d’accès aux données.

## <a name="installation"></a>Installation

La dernière version stable est disponible sur [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-cli"></a>[CLI .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Utilisation

Cette bibliothèque implémente les abstractions ADO.NET courantes pour les connexions, les commandes, les lecteurs de données, etc.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Voir aussi

* [Chaînes de connexion](connection-strings.md)
* [Référence sur l’API](../../../../api/index.md?view=msdata-sqlite-3.0)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
