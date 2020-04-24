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
# <a name="metadata"></a><span data-ttu-id="8d87a-103">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="8d87a-103">Metadata</span></span>

<span data-ttu-id="8d87a-104">Il existe deux API pour la récupération des métadonnées dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8d87a-104">There are two APIs for retrieving metadata in ADO.NET.</span></span> <span data-ttu-id="8d87a-105">L’une récupère les métadonnées relatives aux résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="8d87a-105">One retrieves metadata about query results.</span></span> <span data-ttu-id="8d87a-106">L’autre extrait les métadonnées relatives au schéma de base de données.</span><span class="sxs-lookup"><span data-stu-id="8d87a-106">The other retrieves metadata about the database schema.</span></span>

## <a name="query-result-metadata"></a><span data-ttu-id="8d87a-107">Métadonnées de résultat de la requête</span><span class="sxs-lookup"><span data-stu-id="8d87a-107">Query result metadata</span></span>

<span data-ttu-id="8d87a-108">Vous pouvez récupérer des métadonnées sur les résultats d’une requête <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> à l' `SqliteDataReader`aide de la méthode sur.</span><span class="sxs-lookup"><span data-stu-id="8d87a-108">You can retrieve metadata about the results of a query using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method on `SqliteDataReader`.</span></span> <span data-ttu-id="8d87a-109">Le retourné <xref:System.Data.DataTable> contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d87a-109">The returned <xref:System.Data.DataTable> contains the following columns:</span></span>

| <span data-ttu-id="8d87a-110">Colonne</span><span class="sxs-lookup"><span data-stu-id="8d87a-110">Column</span></span>             | <span data-ttu-id="8d87a-111">Type</span><span class="sxs-lookup"><span data-stu-id="8d87a-111">Type</span></span>    | <span data-ttu-id="8d87a-112">Description</span><span class="sxs-lookup"><span data-stu-id="8d87a-112">Description</span></span>                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | <span data-ttu-id="8d87a-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="8d87a-113">Boolean</span></span> | <span data-ttu-id="8d87a-114">True si la colonne Origin peut être NULL.</span><span class="sxs-lookup"><span data-stu-id="8d87a-114">True if the origin column may be NULL.</span></span>                                    |
| `BaseCatalogName`  | <span data-ttu-id="8d87a-115">String</span><span class="sxs-lookup"><span data-stu-id="8d87a-115">String</span></span>  | <span data-ttu-id="8d87a-116">Nom de la base de données de la colonne d’origine.</span><span class="sxs-lookup"><span data-stu-id="8d87a-116">The name of the origin column's database.</span></span> <span data-ttu-id="8d87a-117">Toujours NULL pour les expressions.</span><span class="sxs-lookup"><span data-stu-id="8d87a-117">Always NULL for expressions.</span></span>    |
| `BaseColumnName`   | <span data-ttu-id="8d87a-118">String</span><span class="sxs-lookup"><span data-stu-id="8d87a-118">String</span></span>  | <span data-ttu-id="8d87a-119">Nom sans alias de la colonne d’origine.</span><span class="sxs-lookup"><span data-stu-id="8d87a-119">The unaliased name of the origin column.</span></span> <span data-ttu-id="8d87a-120">Toujours NULL pour les expressions.</span><span class="sxs-lookup"><span data-stu-id="8d87a-120">Always NULL for expressions.</span></span>    |
| `BaseSchemaName`   | <span data-ttu-id="8d87a-121">String</span><span class="sxs-lookup"><span data-stu-id="8d87a-121">String</span></span>  | <span data-ttu-id="8d87a-122">Toujours NULL.</span><span class="sxs-lookup"><span data-stu-id="8d87a-122">Always NULL.</span></span> <span data-ttu-id="8d87a-123">SQLite ne prend pas en charge les schémas.</span><span class="sxs-lookup"><span data-stu-id="8d87a-123">SQLite doesn't support schemas.</span></span>                              |
| `BaseServerName`   | <span data-ttu-id="8d87a-124">String</span><span class="sxs-lookup"><span data-stu-id="8d87a-124">String</span></span>  | <span data-ttu-id="8d87a-125">Chemin d’accès au fichier de base de données spécifié dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="8d87a-125">The path to the database file specified in the connection string.</span></span>         |
| `BaseTableName`    | <span data-ttu-id="8d87a-126">String</span><span class="sxs-lookup"><span data-stu-id="8d87a-126">String</span></span>  | <span data-ttu-id="8d87a-127">Nom de la table de la colonne d’origine.</span><span class="sxs-lookup"><span data-stu-id="8d87a-127">The name of the origin column's table.</span></span> <span data-ttu-id="8d87a-128">Toujours NULL pour les expressions.</span><span class="sxs-lookup"><span data-stu-id="8d87a-128">Always NULL for expressions.</span></span>       |
| `ColumnName`       | <span data-ttu-id="8d87a-129">String</span><span class="sxs-lookup"><span data-stu-id="8d87a-129">String</span></span>  | <span data-ttu-id="8d87a-130">Nom ou alias de la colonne dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="8d87a-130">The name or alias of the column in the result set.</span></span>                        |
| `ColumnOrdinal`    | <span data-ttu-id="8d87a-131">Int32</span><span class="sxs-lookup"><span data-stu-id="8d87a-131">Int32</span></span>   | <span data-ttu-id="8d87a-132">Ordinal de la colonne dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="8d87a-132">The ordinal of the column in the result set.</span></span>                              |
| `ColumnSize`       | <span data-ttu-id="8d87a-133">Int32</span><span class="sxs-lookup"><span data-stu-id="8d87a-133">Int32</span></span>   | <span data-ttu-id="8d87a-134">Toujours-1.</span><span class="sxs-lookup"><span data-stu-id="8d87a-134">Always -1.</span></span> <span data-ttu-id="8d87a-135">Cela peut changer dans les versions ultérieures de `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="8d87a-135">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span>   |
| `DataType`         | <span data-ttu-id="8d87a-136">Type</span><span class="sxs-lookup"><span data-stu-id="8d87a-136">Type</span></span>    | <span data-ttu-id="8d87a-137">Type de données .NET par défaut de la colonne.</span><span class="sxs-lookup"><span data-stu-id="8d87a-137">The default .NET data type of the column.</span></span>                                 |
| `DataTypeName`     | <span data-ttu-id="8d87a-138">String</span><span class="sxs-lookup"><span data-stu-id="8d87a-138">String</span></span>  | <span data-ttu-id="8d87a-139">Type de données SQLite de la colonne.</span><span class="sxs-lookup"><span data-stu-id="8d87a-139">The SQLite data type of the column.</span></span>                                       |
| `IsAliased`        | <span data-ttu-id="8d87a-140">Boolean</span><span class="sxs-lookup"><span data-stu-id="8d87a-140">Boolean</span></span> | <span data-ttu-id="8d87a-141">True si le nom de colonne est un alias dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="8d87a-141">True if the column name is aliased in the result set.</span></span>                     |
| `IsAutoIncrement`  | <span data-ttu-id="8d87a-142">Boolean</span><span class="sxs-lookup"><span data-stu-id="8d87a-142">Boolean</span></span> | <span data-ttu-id="8d87a-143">True si la colonne Origin a été créée avec le mot clé AUTOINCREMENT.</span><span class="sxs-lookup"><span data-stu-id="8d87a-143">True if the origin column was created with the AUTOINCREMENT keyword.</span></span>     |
| `IsExpression`     | <span data-ttu-id="8d87a-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="8d87a-144">Boolean</span></span> | <span data-ttu-id="8d87a-145">True si la colonne provient d’une expression dans la requête.</span><span class="sxs-lookup"><span data-stu-id="8d87a-145">True if the column originates from an expression in the query.</span></span>            |
| `IsKey`            | <span data-ttu-id="8d87a-146">Boolean</span><span class="sxs-lookup"><span data-stu-id="8d87a-146">Boolean</span></span> | <span data-ttu-id="8d87a-147">True si la colonne Origin fait partie de la clé primaire.</span><span class="sxs-lookup"><span data-stu-id="8d87a-147">True if the origin column is part of the PRIMARY KEY.</span></span>                     |
| `IsUnique`         | <span data-ttu-id="8d87a-148">Boolean</span><span class="sxs-lookup"><span data-stu-id="8d87a-148">Boolean</span></span> | <span data-ttu-id="8d87a-149">True si la colonne Origin est UNIQUE.</span><span class="sxs-lookup"><span data-stu-id="8d87a-149">True if the origin column is UNIQUE.</span></span>                                      |
| `NumericPrecision` | <span data-ttu-id="8d87a-150">Int16</span><span class="sxs-lookup"><span data-stu-id="8d87a-150">Int16</span></span>   | <span data-ttu-id="8d87a-151">Toujours NULL.</span><span class="sxs-lookup"><span data-stu-id="8d87a-151">Always NULL.</span></span> <span data-ttu-id="8d87a-152">Cela peut changer dans les versions ultérieures de `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="8d87a-152">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |
| `NumericScale`     | <span data-ttu-id="8d87a-153">Int16</span><span class="sxs-lookup"><span data-stu-id="8d87a-153">Int16</span></span>   | <span data-ttu-id="8d87a-154">Toujours NULL.</span><span class="sxs-lookup"><span data-stu-id="8d87a-154">Always NULL.</span></span> <span data-ttu-id="8d87a-155">Cela peut changer dans les versions ultérieures de `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="8d87a-155">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |

<span data-ttu-id="8d87a-156">L’exemple suivant montre comment utiliser `GetSchemaTable` pour créer une chaîne de débogage qui affiche des métadonnées sur un résultat :</span><span class="sxs-lookup"><span data-stu-id="8d87a-156">The following example shows how to use `GetSchemaTable` to create a debug string that shows metadata about a result:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

<span data-ttu-id="8d87a-157">Par exemple, cette requête génère la chaîne de débogage suivante :</span><span class="sxs-lookup"><span data-stu-id="8d87a-157">For example, this query would produce the following debug string:</span></span>

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

## <a name="schema-metadata"></a><span data-ttu-id="8d87a-158">Métadonnées de schéma</span><span class="sxs-lookup"><span data-stu-id="8d87a-158">Schema metadata</span></span>

<span data-ttu-id="8d87a-159">Microsoft. Data. sqlite n’implémente pas la méthode GetSchema sur DbConnection.</span><span class="sxs-lookup"><span data-stu-id="8d87a-159">Microsoft.Data.Sqlite doesn't implement the GetSchema method on DbConnection.</span></span> <span data-ttu-id="8d87a-160">Au lieu de cela, vous pouvez interroger directement les informations de schéma à l’aide des instructions [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table et PRAGMA comme [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) et [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span><span class="sxs-lookup"><span data-stu-id="8d87a-160">Instead, you can query directly for schema information using the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and PRAGMA statements like [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) and [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span></span>

<span data-ttu-id="8d87a-161">Par exemple, cette requête récupère les métadonnées relatives à toutes les colonnes de la base de données.</span><span class="sxs-lookup"><span data-stu-id="8d87a-161">For example, this query will retrieve metadata about all the columns in the database.</span></span>

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a><span data-ttu-id="8d87a-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d87a-162">See also</span></span>

* [<span data-ttu-id="8d87a-163">Stockage du schéma SQL Database</span><span class="sxs-lookup"><span data-stu-id="8d87a-163">Storage of the SQL Database Schema</span></span>](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [<span data-ttu-id="8d87a-164">Instructions PRAGMA</span><span class="sxs-lookup"><span data-stu-id="8d87a-164">PRAGMA Statements</span></span>](https://www.sqlite.org/pragma.html)
* [<span data-ttu-id="8d87a-165">Types de données</span><span class="sxs-lookup"><span data-stu-id="8d87a-165">Data types</span></span>](types.md)
