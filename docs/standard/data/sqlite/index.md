---
title: Vue d’ensemble
ms.date: 12/13/2019
description: Un aperçu de Microsoft.Data.Sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543597"
---
# <a name="microsoftdatasqlite-overview"></a>Aperçu de Microsoft.Data.Sqlite

Microsoft.Data.Sqlite est un fournisseur [de ADO.NET](../../../framework/data/adonet/index.md) léger pour SQLite. Le fournisseur [de base de cadre d’entité](/ef/core/) pour SQLite est construit au-dessus de cette bibliothèque. Cependant, il peut également être utilisé de façon indépendante ou avec d’autres bibliothèques d’accès aux données.

## <a name="installation"></a>Installation

La dernière version stable est disponible sur [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-cli"></a>[CLI .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Studio visuel](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Usage

Cette bibliothèque met en œuvre les abstractions ADO.NET communes pour les connexions, les commandes, les lecteurs de données, etc.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Voir aussi

* [Chaînes de connexion](connection-strings.md)
* [Référence des API](/dotnet/api/?view=msdata-sqlite-3.0)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
