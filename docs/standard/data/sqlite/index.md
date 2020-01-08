---
title: Vue d'ensemble de
ms.date: 12/13/2019
description: Vue d’ensemble de Microsoft. Data. sqlite
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447229"
---
# <a name="microsoftdatasqlite-overview"></a>Vue d’ensemble de Microsoft. Data. sqlite

Microsoft. Data. sqlite est un fournisseur [ADO.net](../../../framework/data/adonet/index.md) léger pour SQLite. Le fournisseur [Entity Framework Core](/ef/core/) pour SQLite s’appuie sur cette bibliothèque. Toutefois, il peut également être utilisé indépendamment ou avec d’autres bibliothèques d’accès aux données.

## <a name="installation"></a>Installation de

La dernière version stable est disponible sur [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-clitabnetcore-cli"></a>[CLI .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Contrôle

Cette bibliothèque implémente les abstractions ADO.NET courantes pour les connexions, les commandes, les lecteurs de données, etc.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Voir aussi

* [Chaînes de connexion](connection-strings.md)
* [Informations de référence sur les API](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
