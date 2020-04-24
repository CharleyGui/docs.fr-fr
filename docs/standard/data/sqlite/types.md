---
title: Types de données
ms.date: 12/13/2019
description: Décrit les types de données pris en charge et certaines des limitations qui les entourent.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389042"
---
# <a name="data-types"></a>Types de données

SQLite possède uniquement quatre types de données primitifs : entier, réel, texte et objet BLOB. Les API qui retournent des `object` valeurs de base de données en tant que ne retournent jamais l’un de ces quatre types. Les types .NET supplémentaires sont pris en charge par Microsoft. Data. sqlite, mais les valeurs sont finalement forcées entre ces types et l’un des quatre types primitifs.

| .NET           | SQLite  | Notes                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` ou `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | AAAA-MM-JJ HH : mm : SS. FFFFFFF                                   |
| DateTimeOffset | TEXT    | AAAA-MM-JJ HH : mm : SS. FFFFFFFzzz                                |
| Decimal        | TEXT    | `0.0###########################`format. Le réel serait une perte. |
| Double         | real    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Unique         | real    |                                                               |
| String         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. hh : mm : SS. fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt32         | INTEGER |                                                               |
| UInt64         | INTEGER | Dépassement de valeurs élevées                                         |

## <a name="alternative-types"></a>Autres types

Certains types .NET peuvent être lus à partir d’autres types de SQLite. Les paramètres peuvent également être configurés pour utiliser ces types alternatifs. Pour plus d’informations, consultez [Paramètres](parameters.md#alternative-types).

| .NET           | SQLite  | Notes          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| DateTime       | real    | Valeur du jour julien |
| DateTimeOffset | real    | Valeur du jour julien |
| Guid           | BLOB    |                  |
| TimeSpan       | real    | En jours          |

Par exemple, la requête suivante lit une valeur TimeSpan à partir d’une colonne réelle dans le jeu de résultats.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Types de colonnes

SQLite utilise un système de type dynamique où le type d’une valeur est associé à la valeur elle-même et non à la colonne où elle est stockée. Vous êtes libre d’utiliser le nom du type de colonne de votre choix. Microsoft. Data. sqlite n’applique aucune sémantique supplémentaire à ces noms.

Le nom du type de colonne a un impact sur l' [affinité de type](https://www.sqlite.org/datatype3.html#type_affinity). Un piège courant est que l’utilisation d’un type de colonne de chaîne essaiera de convertir des valeurs en entier ou réel, ce qui peut entraîner des résultats inattendus. Nous vous recommandons d’utiliser uniquement les quatre noms de type SQLite primitifs : entier, réel, texte et objet BLOB.

SQLite vous permet de spécifier des facettes de type telles que la longueur, la précision et l’échelle, mais elles ne sont pas appliquées par le moteur de base de données. Votre application est chargée de l’appliquer.

## <a name="see-also"></a>Voir aussi

- [Types de données dans SQLite](https://www.sqlite.org/datatype3.html)
