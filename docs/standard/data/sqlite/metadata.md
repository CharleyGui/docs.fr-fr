---
title: Métadonnées
ms.date: 12/13/2019
description: Découvrez comment récupérer des métadonnées sur la base de données.
ms.openlocfilehash: b2f2704a748627d9943943fa2fa7b1b7e9f3007f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447194"
---
# <a name="metadata"></a>Métadonnées

Il existe deux API pour la récupération des métadonnées dans ADO.NET. L’une récupère les métadonnées relatives aux résultats de la requête. L’autre extrait les métadonnées relatives au schéma de base de données.

## <a name="query-result-metadata"></a>Métadonnées de résultat de la requête

Vous pouvez récupérer des métadonnées sur les résultats d’une requête <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> à l' `SqliteDataReader`aide de la méthode sur. Le retourné <xref:System.Data.DataTable> contient les colonnes suivantes :

| Colonne             | Type    | Description                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | Boolean | True si la colonne Origin peut être NULL.                                    |
| `BaseCatalogName`  | String  | Nom de la base de données de la colonne d’origine. Toujours NULL pour les expressions.    |
| `BaseColumnName`   | String  | Nom sans alias de la colonne d’origine. Toujours NULL pour les expressions.    |
| `BaseSchemaName`   | String  | Toujours NULL. SQLite ne prend pas en charge les schémas.                              |
| `BaseServerName`   | String  | Chemin d’accès au fichier de base de données spécifié dans la chaîne de connexion.         |
| `BaseTableName`    | String  | Nom de la table de la colonne d’origine. Toujours NULL pour les expressions.       |
| `ColumnName`       | String  | Nom ou alias de la colonne dans le jeu de résultats.                        |
| `ColumnOrdinal`    | Int32   | Ordinal de la colonne dans le jeu de résultats.                              |
| `ColumnSize`       | Int32   | Toujours-1. Cela peut changer dans les versions ultérieures de `Microsoft.Data.Sqlite`.   |
| `DataType`         | Type    | Type de données .NET par défaut de la colonne.                                 |
| `DataTypeName`     | String  | Type de données SQLite de la colonne.                                       |
| `IsAliased`        | Boolean | True si le nom de colonne est un alias dans le jeu de résultats.                     |
| `IsAutoIncrement`  | Boolean | True si la colonne Origin a été créée avec le mot clé AUTOINCREMENT.     |
| `IsExpression`     | Boolean | True si la colonne provient d’une expression dans la requête.            |
| `IsKey`            | Boolean | True si la colonne Origin fait partie de la clé primaire.                     |
| `IsUnique`         | Boolean | True si la colonne Origin est UNIQUE.                                      |
| `NumericPrecision` | Int16   | Toujours NULL. Cela peut changer dans les versions ultérieures de `Microsoft.Data.Sqlite`. |
| `NumericScale`     | Int16   | Toujours NULL. Cela peut changer dans les versions ultérieures de `Microsoft.Data.Sqlite`. |

L’exemple suivant montre comment utiliser `GetSchemaTable` pour créer une chaîne de débogage qui affiche des métadonnées sur un résultat :

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

Par exemple, cette requête génère la chaîne de débogage suivante :

```sql
SELECT id AS post_id,
       title,
       body,
       random() AS random
FROM post
```

```output
post.id AS post_id INTEGER PRIMARY KEY AUTOINCREMENT
post.title TEXT NOT NULL UNIQUE
post.body TEXT
(expression) AS random BLOB
```

## <a name="schema-metadata"></a>Métadonnées de schéma

Microsoft. Data. sqlite n’implémente pas la méthode GetSchema sur DbConnection. Au lieu de cela, vous pouvez interroger directement les informations de schéma à l’aide des instructions [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table et PRAGMA comme [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) et [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).

Par exemple, cette requête récupère les métadonnées relatives à toutes les colonnes de la base de données.

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a>Voir aussi

* [Stockage du schéma SQL Database](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [Instructions PRAGMA](https://www.sqlite.org/pragma.html)
* [Types de données](types.md)
