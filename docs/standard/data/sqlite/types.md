---
title: Types de données
ms.date: 12/13/2019
description: Décrit les types de données pris en charge et certaines des limitations qui les entourent.
ms.openlocfilehash: ae70cb91a5a6d9cfed45a5a47dda25a70362871e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447180"
---
# <a name="data-types"></a>Types de données

SQLite possède uniquement quatre types de données primitifs : entier, réel, texte et objet BLOB. Les API qui retournent des valeurs de base de données en tant que `object` ne retourneront jamais l’un de ces quatre types. Les types .NET supplémentaires sont pris en charge par Microsoft. Data. sqlite, mais les valeurs sont finalement forcées entre ces types et l’un des quatre types primitifs.

| .NET           | SQLite  | Notes                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` ou `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | AAAA-MM-JJ HH : mm : SS. FFFFFFF                                   |
| DateTimeOffset | TEXT    | AAAA-MM-JJ HH : mm : SS. FFFFFFFzzz                                |
| Decimal        | TEXT    | format de `0.0###########################`. Le réel serait une perte. |
| Double         | RÉEL    |                                                               |
| GUID           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Single         | RÉEL    |                                                               |
| Chaîne         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. hh : mm : SS. fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt64         | INTEGER | Dépassement de valeurs élevées                                         |

## <a name="alternative-types"></a>Autres types

Certains types .NET peuvent être lus à partir d’autres types de SQLite. Les paramètres peuvent également être configurés pour utiliser ces types alternatifs. Pour plus d’informations, consultez [Paramètres](parameters.md#alternative-types).

| .NET           | SQLite  | Notes          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| DateTime       | RÉEL    | Valeur du jour julien |
| DateTimeOffset | RÉEL    | Valeur du jour julien |
| GUID           | BLOB    |                  |
| TimeSpan       | RÉEL    | En jours          |

Par exemple, la requête suivante lit une valeur TimeSpan à partir d’une colonne réelle dans le jeu de résultats.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Types de colonnes

SQLite utilise un système de type dynamique où le type d’une valeur est associé à la valeur elle-même et non à la colonne où elle est stockée. Vous êtes libre d’utiliser le nom du type de colonne de votre choix. Microsoft. Data. sqlite n’applique aucune sémantique supplémentaire à ces noms.

Le nom du type de colonne a un impact sur l' [affinité de type](https://www.sqlite.org/datatype3.html#type_affinity). Un piège courant est que l’utilisation d’un type de colonne de chaîne essaiera de convertir des valeurs en entier ou réel, ce qui peut entraîner des résultats inattendus. Nous vous recommandons d’utiliser uniquement les quatre noms de type SQLite primitifs : entier, réel, texte et objet BLOB.

SQLite vous permet de spécifier des facettes de type telles que la longueur, la précision et l’échelle, mais elles ne sont pas appliquées par le moteur de base de données. Votre application est chargée de l’appliquer.

## <a name="see-also"></a>Voir aussi

- [Types de données dans SQLite](https://www.sqlite.org/datatype3.html)
