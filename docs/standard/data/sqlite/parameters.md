---
title: Paramètres
ms.date: 12/13/2019
description: Découvrez comment utiliser les paramètres SQL.
ms.openlocfilehash: b24610a5cb65e2b24171452acef9bf55b4995431
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768948"
---
# <a name="parameters"></a>Paramètres

Les paramètres sont utilisés pour se protéger contre les attaques par injection SQL. Au lieu de concaténer les entrées utilisateur avec les instructions SQL, utilisez des paramètres pour vous assurer que l’entrée n’est jamais traitée comme une valeur littérale et qu’elle n’est jamais exécutée. Dans SQLite, les paramètres sont généralement autorisés partout où un littéral est autorisé dans les instructions SQL.

Les paramètres peuvent être préfixés avec `:` , `@` ou `$` .

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Pour plus d’informations sur la façon dont les valeurs .NET sont mappées aux valeurs SQLite, consultez [types de données](types.md) .

## <a name="truncation"></a>Troncation

Utilisez la <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> propriété pour tronquer les valeurs de texte et d’objet BLOB.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Size = 30;
```

## <a name="alternative-types"></a>Autres types

Parfois, vous souhaiterez peut-être utiliser un autre type de SQLite. Pour ce faire, définissez la <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> propriété.

Les mappages de type alternatifs suivants peuvent être utilisés. Pour les mappages par défaut, consultez [types de données](types.md).

| Valeur          | SqliteType | Notes          |
| -------------- | ---------- | ---------------- |
| Char           | Integer    | UTF-16           |
| DateTime       | Real       | Valeur du jour julien |
| DateTimeOffset | Real       | Valeur du jour julien |
| Guid           | Objet blob       |                  |
| TimeSpan       | Real       | En jours          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Paramètres de sortie

SQLite ne prend pas en charge les paramètres de sortie. Retournent les valeurs dans les résultats de la requête à la place.

## <a name="see-also"></a>Voir aussi

* [Types de données](types.md)
