---
title: Classement
ms.date: 12/13/2019
description: Découvrez comment créer une séquence de classement personnalisée.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242970"
---
# <a name="collation"></a>Classement

Les séquences de classement sont utilisées par SQLite lors de la comparaison des valeurs de texte pour déterminer l’ordre et l’égalité. Vous pouvez spécifier le classement à utiliser lors de la création de colonnes ou par opération dans des requêtes SQL. SQLite comprend trois séquences de classement par défaut.

| Classement | Description                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignore les espaces de fin               |
| NOCASE    | Non-respect de la casse pour les caractères ASCII A-Z |
| BINARY    | Respecte la casse. Compare les octets directement   |

## <a name="custom-collation"></a>Classement personnalisé

Vous pouvez également définir vos propres séquences de classement ou remplacer celles qui sont intégrées à l’aide <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>de. L’exemple suivant illustre le remplacement du classement nocase pour prendre en charge les caractères Unicode. L' [exemple de code complet](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) est disponible sur GitHub.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like (opérateur)

L’opérateur LIKE dans SQLite ne respecte pas les classements. L’implémentation par défaut a la même sémantique que le classement nocase. Elle ne respecte pas la casse pour les caractères ASCII de A à Z.

Vous pouvez facilement faire en sorte que l’opérateur LIKE respecte la casse en utilisant l’instruction pragma suivante :

```sql
PRAGMA case_sensitive_like = 1
```

Pour plus d’informations sur la substitution de l’implémentation de l’opérateur LIKE [, consultez fonctions définies](user-defined-functions.md) par l’utilisateur.

## <a name="see-also"></a>Voir aussi

* [Fonctions définies par l’utilisateur](user-defined-functions.md)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
