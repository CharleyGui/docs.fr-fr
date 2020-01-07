---
title: Parameters
ms.date: 12/13/2019
description: Découvrez comment utiliser les paramètres SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447187"
---
# <a name="parameters"></a>Parameters

Les paramètres sont utilisés pour se protéger contre les attaques par injection SQL. Au lieu de concaténer les entrées utilisateur avec les instructions SQL, utilisez des paramètres pour vous assurer que l’entrée n’est jamais traitée comme une valeur littérale et qu’elle n’est jamais exécutée. Dans SQLite, les paramètres sont généralement autorisés partout où un littéral est autorisé dans les instructions SQL.

Les paramètres peuvent être précédés de `:`, `@`ou `$`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Pour plus d’informations sur la façon dont les valeurs .NET sont mappées aux valeurs SQLite, consultez [types de données](types.md) .

## <a name="truncation"></a>Troncation

Utilisez la propriété <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> pour tronquer les valeurs de texte et d’objet BLOB.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Autres types

Parfois, vous souhaiterez peut-être utiliser un autre type de SQLite. Pour ce faire, définissez la propriété <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>.

Les mappages de type alternatifs suivants peuvent être utilisés. Pour les mappages par défaut, consultez [types de données](types.md).

| Value          | SqliteType | Notes          |
| -------------- | ---------- | ---------------- |
| Char           | Entier    | UTF-16           |
| DateTime       | Real       | Valeur du jour julien |
| DateTimeOffset | Real       | Valeur du jour julien |
| GUID           | Objet Blob       |                  |
| TimeSpan       | Real       | En jours          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Paramètres de sortie

SQLite ne prend pas en charge les paramètres de sortie. Retournent les valeurs dans les résultats de la requête à la place.

## <a name="see-also"></a>Voir aussi

* [Types de données](types.md)
