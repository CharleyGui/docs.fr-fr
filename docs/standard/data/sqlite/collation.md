---
title: Collation
ms.date: 12/13/2019
description: Découvrez comment créer une séquence de classement personnalisée.
ms.openlocfilehash: 9cc574a75c8f5347dd9bb44e36af72e50afa57b4
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777387"
---
# <a name="collation"></a>Collation

Les séquences de classement sont utilisées par SQLite lors de la comparaison des valeurs de texte pour déterminer l’ordre et l’égalité. Vous pouvez spécifier le classement à utiliser lors de la création de colonnes ou par opération dans des requêtes SQL. SQLite comprend trois séquences de classement par défaut.

| Collation | Description                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignore les espaces de fin               |
| NOCASE    | Non-respect de la casse pour les caractères ASCII A-Z |
| BINARY    | Respecte la casse. Compare les octets directement   |

## <a name="custom-collation"></a>Classement personnalisé

Vous pouvez également définir vos propres séquences de classement ou remplacer celles prédéfinies à l’aide de <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>. L’exemple suivant illustre le remplacement du classement nocase pour prendre en charge les caractères Unicode. L' [exemple de code complet](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/CollationSample/Program.cs) est disponible sur GitHub.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like (opérateur)

L’opérateur LIKE dans SQLite ne respecte pas les classements. L’implémentation par défaut a la même sémantique que le classement nocase. Elle ne respecte pas la casse pour les caractères ASCII de A à Z.

Vous pouvez facilement faire en sorte que l’opérateur LIKE respecte la casse en utilisant l’instruction pragma suivante :

```sql
PRAGMA case_sensitive_like = 0
```

Pour plus d’informations sur la substitution de l’implémentation de l’opérateur LIKE [, consultez fonctions définies](user-defined-functions.md) par l’utilisateur.

## <a name="see-also"></a>Voir aussi

* [Fonctions définies par l’utilisateur](user-defined-functions.md)
* [Syntaxe SQL](https://www.sqlite.org/lang.html)
