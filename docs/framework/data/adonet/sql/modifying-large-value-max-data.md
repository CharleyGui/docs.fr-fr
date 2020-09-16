---
title: Modification de données de valeur élevée (max)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 8a077c56f4de5a88e9c2a6f932c9a8b5ffc6b974
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556965"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="62b38-102">Modification de données de valeurs élevées (max) dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="62b38-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="62b38-103">Les types de données LOB (Large Object) sont ceux dont la taille maximale de ligne dépasse huit kilo-octets (Ko).</span><span class="sxs-lookup"><span data-stu-id="62b38-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="62b38-104">SQL Server fournit un spécificateur `max` pour les types de données `varchar`, `nvarchar` et `varbinary` afin de permettre le stockage de valeurs pouvant atteindre 2^32 octets.</span><span class="sxs-lookup"><span data-stu-id="62b38-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="62b38-105">Les colonnes de table et les variables Transact-SQL peuvent spécifier des types de données `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="62b38-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="62b38-106">Dans ADO.NET, les types de données `max` peuvent être extraits par un `DataReader` et spécifiés comme valeurs de paramètre d'entrée ou de sortie sans que cela nécessite une manipulation particulière.</span><span class="sxs-lookup"><span data-stu-id="62b38-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="62b38-107">Pour les types de données `varchar` de valeur élevée, les données peuvent être récupérées et mises à jour de façon incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="62b38-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="62b38-108">Les types de données `max` peuvent être utilisés pour effectuer des comparaisons, en tant que variables Transact-SQL, ainsi que des concaténations.</span><span class="sxs-lookup"><span data-stu-id="62b38-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="62b38-109">Elles peuvent également être utilisées dans les clauses DISTINCT, ORDER BY et GROUP BY d’une instruction SELECT, ainsi que dans les agrégats, jointures et sous-requêtes.</span><span class="sxs-lookup"><span data-stu-id="62b38-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="62b38-110">Le tableau suivant présente des liens vers les ressources dans la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="62b38-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="62b38-111">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="62b38-111">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="62b38-112">[Utilisation de types de données de valeur élevée](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="62b38-112">[Using Large-Value Data Types](/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span></span>  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="62b38-113">Restrictions relatives aux types de valeur élevée</span><span class="sxs-lookup"><span data-stu-id="62b38-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="62b38-114">Les restrictions suivantes s’appliquent aux types de données `max`, et n’existent pas pour les types de données plus petits :</span><span class="sxs-lookup"><span data-stu-id="62b38-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="62b38-115">Un `sql_variant` ne peut pas contenir un type de données `varchar` de valeur élevée.</span><span class="sxs-lookup"><span data-stu-id="62b38-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="62b38-116">Les colonnes `varchar` de valeur élevée ne peuvent pas être spécifiées en tant que colonne clé dans un index.</span><span class="sxs-lookup"><span data-stu-id="62b38-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="62b38-117">Elles sont autorisées dans une colonne incluse dans un index non cluster.</span><span class="sxs-lookup"><span data-stu-id="62b38-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="62b38-118">Les colonnes `varchar` de valeur élevée ne peuvent pas être utilisées en tant que colonnes clés de partitionnement.</span><span class="sxs-lookup"><span data-stu-id="62b38-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="62b38-119">Utilisation de types de valeur élevée dans Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="62b38-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="62b38-120">La fonction Transact-SQL `OPENROWSET` est une méthode unique de connexion et d’accès aux données distantes.</span><span class="sxs-lookup"><span data-stu-id="62b38-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="62b38-121">Elle inclut toutes les informations de connexion nécessaires pour accéder à des données distantes à partir d'une source de données OLE DB.</span><span class="sxs-lookup"><span data-stu-id="62b38-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="62b38-122">Il est possible de référencer `OPENROWSET` dans la clause FROM d’une requête comme s’il s’agissait du nom d’une table.</span><span class="sxs-lookup"><span data-stu-id="62b38-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="62b38-123">Il peut également être référencé comme table cible d'une instruction INSERT, UPDATE ou DELETE, sujette aux capacités du fournisseur OLE DB.</span><span class="sxs-lookup"><span data-stu-id="62b38-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="62b38-124">La fonction `OPENROWSET` comprend le fournisseur de jeu de lignes `BULK`, qui permet de lire directement les données d'un fichier sans devoir les charger dans une table cible.</span><span class="sxs-lookup"><span data-stu-id="62b38-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="62b38-125">Cela vous permet d’utiliser `OPENROWSET` dans une simple instruction INSERT SELECT.</span><span class="sxs-lookup"><span data-stu-id="62b38-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="62b38-126">Les arguments de l’option `OPENROWSET BULK` permettent d’exercer un contrôle important sur l’emplacement où commence et se termine la lecture de données, sur la manière de gérer les erreurs et sur la façon d’interpréter les données.</span><span class="sxs-lookup"><span data-stu-id="62b38-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="62b38-127">Vous pouvez par exemple spécifier que le fichier de données soit lu comme un ensemble d’une seule ligne et d’une seule colonne du type `varbinary`, `varchar` ou `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="62b38-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="62b38-128">Pour obtenir la syntaxe complète et les options, consultez la Documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="62b38-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="62b38-129">L’exemple suivant insère une photo dans la table ProductPhoto de l’exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="62b38-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="62b38-130">Lors de l’utilisation du fournisseur `BULK OPENROWSET`, vous devez fournir la liste nommée des colonnes même si vous n’insérez pas de valeurs dans chaque colonne.</span><span class="sxs-lookup"><span data-stu-id="62b38-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="62b38-131">Dans ce cas, la clé primaire est définie comme une colonne d’identité et peut être omise dans la liste des colonnes.</span><span class="sxs-lookup"><span data-stu-id="62b38-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="62b38-132">Notez que vous devez également fournir un nom de corrélation à la fin de l’instruction `OPENROWSET`, dans ce cas ThumbnailPhoto.</span><span class="sxs-lookup"><span data-stu-id="62b38-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="62b38-133">Cela correspond à la colonne de la table `ProductPhoto` dans laquelle le fichier est chargé.</span><span class="sxs-lookup"><span data-stu-id="62b38-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="62b38-134">Mise à jour de données à l'aide de UPDATE .WRITE</span><span class="sxs-lookup"><span data-stu-id="62b38-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="62b38-135">L’instruction Transact-SQL UPDATE possède une nouvelle syntaxe WRITE permettant de modifier le contenu des colonnes `varchar(max)`, `nvarchar(max)` ou `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="62b38-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="62b38-136">Cela vous permet d’effectuer des mises à jour partielles des données.</span><span class="sxs-lookup"><span data-stu-id="62b38-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="62b38-137">La syntaxe UPDATE .WRITE est présentée ici sous forme abrégée :</span><span class="sxs-lookup"><span data-stu-id="62b38-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="62b38-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="62b38-138">UPDATE</span></span>  
  
 <span data-ttu-id="62b38-139">{ *\<object>* }</span><span class="sxs-lookup"><span data-stu-id="62b38-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="62b38-140">SET</span><span class="sxs-lookup"><span data-stu-id="62b38-140">SET</span></span>  
  
 <span data-ttu-id="62b38-141">{ *column_name* = {. WRITE ( *expression* , @Offset , @Length )}</span><span class="sxs-lookup"><span data-stu-id="62b38-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="62b38-142">La méthode WRITE spécifie qu’une section de la valeur *column_name* sera modifiée.</span><span class="sxs-lookup"><span data-stu-id="62b38-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="62b38-143">L’expression est la valeur qui sera copiée dans *column_name*, `@Offset` est le point à partir duquel l’expression sera écrite et l’argument `@Length` indique la longueur de la section dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="62b38-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="62b38-144">Si</span><span class="sxs-lookup"><span data-stu-id="62b38-144">If</span></span>|<span data-ttu-id="62b38-145">Alors</span><span class="sxs-lookup"><span data-stu-id="62b38-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="62b38-146">L’expression est définie sur NULL</span><span class="sxs-lookup"><span data-stu-id="62b38-146">The expression is set to NULL</span></span>|<span data-ttu-id="62b38-147">`@Length` est ignoré et la valeur de *column_name* est tronquée à l’emplacement spécifié par `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="62b38-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="62b38-148">`@Offset` est NULL</span><span class="sxs-lookup"><span data-stu-id="62b38-148">`@Offset` is NULL</span></span>|<span data-ttu-id="62b38-149">L’opération de mise à jour ajoute l’expression à la fin de la valeur de *column_name* existante et `@Length` est ignoré.</span><span class="sxs-lookup"><span data-stu-id="62b38-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="62b38-150">`@Offset` est supérieur à la longueur de la valeur column_name</span><span class="sxs-lookup"><span data-stu-id="62b38-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="62b38-151">SQL Server retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="62b38-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="62b38-152">`@Length` est NULL</span><span class="sxs-lookup"><span data-stu-id="62b38-152">`@Length` is NULL</span></span>|<span data-ttu-id="62b38-153">La mise à jour supprime toutes les données de `@Offset` jusqu’à la fin de la valeur de `column_name`.</span><span class="sxs-lookup"><span data-stu-id="62b38-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="62b38-154">Ni `@Offset` ni `@Length` ne peuvent être un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="62b38-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62b38-155"> Exemple</span><span class="sxs-lookup"><span data-stu-id="62b38-155">Example</span></span>  
 <span data-ttu-id="62b38-156">Cet exemple Transact-SQL met à jour une valeur partielle dans DocumentSummary, une colonne `nvarchar(max)` dans la table Document de la base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="62b38-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="62b38-157">Le terme « components » est remplacé par le terme « features », en spécifiant le terme de remplacement, la position de départ (décalage) du terme à remplacer dans les données existantes et le nombre de caractères à remplacer (longueur).</span><span class="sxs-lookup"><span data-stu-id="62b38-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="62b38-158">L’exemple comprend des instructions SELECT avant et après l’instruction UPDATE pour comparer les résultats.</span><span class="sxs-lookup"><span data-stu-id="62b38-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="62b38-159">Utilisation de types de valeur élevée dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="62b38-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="62b38-160">Vous pouvez utiliser des types de valeur élevée dans ADO.NET en spécifiant des types de valeur élevée comme objets <xref:System.Data.SqlClient.SqlParameter> d’un objet <xref:System.Data.SqlClient.SqlDataReader> afin de retourner un jeu de résultats, ou en utilisant un objet <xref:System.Data.SqlClient.SqlDataAdapter> pour remplir un `DataSet`/`DataTable`.</span><span class="sxs-lookup"><span data-stu-id="62b38-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="62b38-161">Il n’y a aucune différence entre la façon dont vous travaillez avec un type de valeur élevée et le type de données de plus petite valeur associé.</span><span class="sxs-lookup"><span data-stu-id="62b38-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="62b38-162">Utilisation de GetSqlBytes pour récupérer des données</span><span class="sxs-lookup"><span data-stu-id="62b38-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="62b38-163">La méthode `GetSqlBytes` du <xref:System.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="62b38-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="62b38-164">Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `varbinary(max)` d’une table et un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données en tant que <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="62b38-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="62b38-165">Utilisation de GetSqlChars pour extraire des données</span><span class="sxs-lookup"><span data-stu-id="62b38-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="62b38-166">La méthode `GetSqlChars` du <xref:System.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varchar(max)` ou `nvarchar(max)`.</span><span class="sxs-lookup"><span data-stu-id="62b38-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="62b38-167">Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `nvarchar(max)` d’une table et un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données.</span><span class="sxs-lookup"><span data-stu-id="62b38-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="62b38-168">Utilisation de GetSqlBinary pour extraire des données</span><span class="sxs-lookup"><span data-stu-id="62b38-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="62b38-169">La méthode `GetSqlBinary` d’un <xref:System.Data.SqlClient.SqlDataReader> peut être utilisée pour récupérer le contenu d’une colonne `varbinary(max)`.</span><span class="sxs-lookup"><span data-stu-id="62b38-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="62b38-170">Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlCommand> nommé `cmd` qui sélectionne des données `varbinary(max)` d’une table et un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données en tant que flux <xref:System.Data.SqlTypes.SqlBinary>.</span><span class="sxs-lookup"><span data-stu-id="62b38-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="62b38-171">Utilisation de GetBytes pour extraire des données</span><span class="sxs-lookup"><span data-stu-id="62b38-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="62b38-172">La méthode `GetBytes` d’un <xref:System.Data.SqlClient.SqlDataReader> lit un flux d'octets à partir de l'offset de colonne spécifié dans un tableau d’octets commençant à l’offset de tableau donné.</span><span class="sxs-lookup"><span data-stu-id="62b38-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="62b38-173">Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les octets dans un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="62b38-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="62b38-174">Notez que, contrairement à `GetSqlBytes`, `GetBytes` nécessite une taille pour la mémoire tampon du tableau.</span><span class="sxs-lookup"><span data-stu-id="62b38-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="62b38-175">Utilisation de GetValue pour extraire des données</span><span class="sxs-lookup"><span data-stu-id="62b38-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="62b38-176">La méthode `GetValue` d’un <xref:System.Data.SqlClient.SqlDataReader> lit la valeur à partir de l’offset de colonne spécifié dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="62b38-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="62b38-177">Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données binaires à partir de l’offset de la première colonne, puis les données de chaîne à partir du deuxième offset de colonne.</span><span class="sxs-lookup"><span data-stu-id="62b38-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="62b38-178">Conversion de types de valeur élevée en types CLR</span><span class="sxs-lookup"><span data-stu-id="62b38-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="62b38-179">Vous pouvez convertir le contenu d’une colonne `varchar(max)` ou `nvarchar(max)` à l’aide d’une des méthodes de conversion de chaînes, comme `ToString`.</span><span class="sxs-lookup"><span data-stu-id="62b38-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="62b38-180">Le fragment de code suivant suppose un objet <xref:System.Data.SqlClient.SqlDataReader> nommé `reader` qui récupère les données.</span><span class="sxs-lookup"><span data-stu-id="62b38-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a><span data-ttu-id="62b38-181"> Exemple</span><span class="sxs-lookup"><span data-stu-id="62b38-181">Example</span></span>  
 <span data-ttu-id="62b38-182">Le code suivant récupère le nom et l’objet `LargePhoto` à partir de la table `ProductPhoto` dans la base de données `AdventureWorks` et l’enregistre dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="62b38-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="62b38-183">L’assembly doit être compilé avec une référence à l’espace de noms <xref:System.Drawing>.</span><span class="sxs-lookup"><span data-stu-id="62b38-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="62b38-184">La méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> du <xref:System.Data.SqlClient.SqlDataReader> retourne un objet <xref:System.Data.SqlTypes.SqlBytes> qui expose une propriété `Stream`.</span><span class="sxs-lookup"><span data-stu-id="62b38-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="62b38-185">Le code utilise celle-ci pour créer un nouvel objet `Bitmap`, puis l’enregistre dans le Gif `ImageFormat`.</span><span class="sxs-lookup"><span data-stu-id="62b38-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="62b38-186">Utilisation de paramètres de types de valeur élevée</span><span class="sxs-lookup"><span data-stu-id="62b38-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="62b38-187">Les types de valeur élevée peuvent être utilisés dans des objets <xref:System.Data.SqlClient.SqlParameter> de la même façon que vous utilisez des types de valeur plus petits dans des objets <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="62b38-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="62b38-188">Vous pouvez extraire des types de valeur élevée en tant que valeurs <xref:System.Data.SqlClient.SqlParameter>, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="62b38-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="62b38-189">Le code suppose que la procédure stockée GetDocumentSummary suivante existe dans l’exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="62b38-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="62b38-190">La procédure stockée prend un caractère d’entrée nommé @DocumentID et retourne le contenu de la colonne DocumentSummary dans le paramètre de sortie @DocumentSummary.</span><span class="sxs-lookup"><span data-stu-id="62b38-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a><span data-ttu-id="62b38-191"> Exemple</span><span class="sxs-lookup"><span data-stu-id="62b38-191">Example</span></span>  
 <span data-ttu-id="62b38-192">Le code ADO.NET crée des objets <xref:System.Data.SqlClient.SqlConnection> et <xref:System.Data.SqlClient.SqlCommand> pour exécuter la procédure stockée GetDocumentSummary et récupérer le résumé du document, qui est stocké en tant que type de valeur élevée.</span><span class="sxs-lookup"><span data-stu-id="62b38-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="62b38-193">Le code transmet une valeur pour le paramètre d’entrée @DocumentID et affiche les résultats retournés dans le paramètre de sortie @DocumentSummary dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="62b38-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="62b38-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62b38-194">See also</span></span>

- [<span data-ttu-id="62b38-195">SQL Server des données binaires et de grande valeur</span><span class="sxs-lookup"><span data-stu-id="62b38-195">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="62b38-196">Mappages de types de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="62b38-196">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="62b38-197">SQL Server des opérations de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="62b38-197">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="62b38-198">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="62b38-198">ADO.NET Overview</span></span>](../ado-net-overview.md)
