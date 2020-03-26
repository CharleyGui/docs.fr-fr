---
title: Classement
ms.date: 12/13/2019
description: Apprenez à créer une séquence de collation personnalisée.
ms.openlocfilehash: b93c82a4ace154b8293b05effa8f9e9294fa7708
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506539"
---
# <a name="collation"></a>Classement

Les séquences de collation sont utilisées par SQLite pour comparer les valeurs textUELLEs pour déterminer l’ordre et l’égalité. Vous pouvez spécifier la collation à utiliser lors de la création de colonnes ou par opération dans les requêtes SQL. SQLite comprend trois séquences de collation par défaut.

| Classement | Description                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignore l’espace blanc qui suit               |
| NOCASE    | Cas insensible pour les personnages ASCII A-Z |
| BINARY    | Sensible aux cas. Compare directement les octets   |

## <a name="custom-collation"></a>Collation personnalisée

Vous pouvez également définir vos propres séquences de collation <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>ou remplacer les séquences intégrées à l’aide de . L’exemple suivant montre la collation NOCASE pour prendre en charge les caractères Unicode. Le [code d’échantillon complet](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) est disponible sur GitHub.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like (opérateur)

L’opérateur LIKE de SQLite n’honore pas les collations. La mise en œuvre par défaut a la même sémantique que la collation NOCASE. Ce n’est que insensible aux caractères ASCII A à Z.

Vous pouvez facilement rendre l’opérateur LIKE sensible au cas en utilisant la déclaration pragma suivante :

```sql
PRAGMA case_sensitive_like = 1
```

Consultez [les fonctions définies par l’utilisateur](user-defined-functions.md) pour plus de détails sur la mise en œuvre de l’opérateur LIKE.

## <a name="see-also"></a>Voir aussi

* [Fonctions définies par l’utilisateur](user-defined-functions.md)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
