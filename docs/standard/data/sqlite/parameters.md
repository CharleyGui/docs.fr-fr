---
title: Paramètres
ms.date: 12/13/2019
description: Apprenez à utiliser les paramètres SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400455"
---
# <a name="parameters"></a>Paramètres

Les paramètres sont utilisés pour se protéger contre les attaques d’injection SQL. Au lieu de concatenating entrée utilisateur avec les instructions SQL, utilisez des paramètres pour s’assurer que l’entrée n’est jamais traitée comme une valeur littérale et jamais exécutée. Dans SQLite, les paramètres sont généralement autorisés partout où un littéal est autorisé dans les déclarations SQL.

Les paramètres peuvent être préfixés avec l’un ou l’autre, `:` `@`, ou `$`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Voir [les types de données](types.md) pour plus de détails sur la façon dont les valeurs .NET sont cartographiées aux valeurs SQLite.

## <a name="truncation"></a>Troncation

Utilisez <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> la propriété pour tronquer les valeurs TEXT et BLOB.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Types alternatifs

Parfois, vous pouvez utiliser un autre type SQLite. Faites-le en <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> fixant la propriété.

Les cartes de type alternatif suivantes peuvent être utilisées. Pour les cartes par défaut, voir [les types de données](types.md).

| Valeur          | SqliteType (SqliteType) | Notes           |
| -------------- | ---------- | ---------------- |
| Char           | Integer    | UTF-16           |
| DateTime       | Real       | Julian valeur de jour |
| DateTimeOffset | Real       | Julian valeur de jour |
| Guid           | Objet blob       |                  |
| TimeSpan       | Real       | En jours          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Paramètres de sortie

SQLite ne prend pas en charge les paramètres de sortie. Valeurs de rendement dans les résultats de la requête à la place.

## <a name="see-also"></a>Voir aussi

* [Types de données](types.md)
