---
title: Types de données
ms.date: 12/13/2019
description: Décrit les types de données pris en charge et certaines des limites qui les entourent.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389042"
---
# <a name="data-types"></a>Types de données

SQLite n’a que quatre types de données primitives : INTEGER, REAL, TEXT et BLOB. Les API qui retournent les valeurs de base de données comme un `object` ne retourneront jamais qu’un de ces quatre types. D’autres types .NET sont pris en charge par Microsoft.Data.Sqlite, mais les valeurs sont finalement contraintes entre ces types et l’un des quatre types primitifs.

| .NET           | SQLite  | Notes                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` ou `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | yyyy-MM-dd HH:mm:ss. FFFFFFF                                   |
| DateTimeOffset | TEXT    | yyyy-MM-dd HH:mm:ss. FFFFFFzzz                                |
| Decimal        | TEXT    | `0.0###########################`Format. REAL serait perdu. |
| Double         | real    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Unique         | real    |                                                               |
| String         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d.hh:mm:ss.fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt32         | INTEGER |                                                               |
| UInt64         | INTEGER | Les grandes valeurs débordent                                         |

## <a name="alternative-types"></a>Types alternatifs

Certains types .NET peuvent être lus à partir de types SQLite alternatifs. Les paramètres peuvent également être configurés pour utiliser ces types alternatifs. Pour plus d’informations, consultez [Paramètres](parameters.md#alternative-types).

| .NET           | SQLite  | Notes          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| DateTime       | real    | Julian valeur de jour |
| DateTimeOffset | real    | Julian valeur de jour |
| Guid           | BLOB    |                  |
| TimeSpan       | real    | En jours          |

Par exemple, la requête suivante lit une valeur TimeSpan à partir d’une colonne REAL dans l’ensemble de résultats.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Types de colonnes

SQLite utilise un système de type dynamique où le type de valeur est associé à la valeur elle-même et non à la colonne où elle est stockée. Vous êtes libre d’utiliser n’importe quel nom de type colonne que vous voulez. Microsoft.Data.Sqlite n’appliquera pas de sémantique supplémentaire à ces noms.

Le nom de type colonne a un impact sur [l’affinité de type](https://www.sqlite.org/datatype3.html#type_affinity). Un gotcha commun est que l’utilisation d’un type de colonne de STRING va essayer de convertir les valeurs en INTEGER ou REAL, ce qui peut conduire à des résultats inattendus. Nous vous recommandons d’utiliser uniquement les quatre noms primitifs de type SQLite : INTEGER, REAL, TEXT et BLOB.

SQLite vous permet de spécifier des facettes de type comme la longueur, la précision et l’échelle, mais elles ne sont pas appliquées par le moteur de base de données. Votre application est responsable de l’application de ces derniers.

## <a name="see-also"></a>Voir aussi

- [Datatypes Dans SQLite](https://www.sqlite.org/datatype3.html)
