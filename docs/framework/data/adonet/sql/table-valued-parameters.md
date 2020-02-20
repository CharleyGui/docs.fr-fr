---
title: Paramètres table
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: d99cea1641dc61c1cae6d6b1634359211ce788ae
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452303"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="d3fbf-102">Paramètres table</span><span class="sxs-lookup"><span data-stu-id="d3fbf-102">Table-Valued Parameters</span></span>
<span data-ttu-id="d3fbf-103">Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="d3fbf-104">Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="d3fbf-105">Les lignes de données entrantes sont stockées dans une variable de table que vous pouvez ensuite utiliser à l’aide de Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="d3fbf-106">Les valeurs de colonne dans les paramètres table sont accessibles à l’aide d’instructions Transact-SQL SELECT standard.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="d3fbf-107">Les paramètres table sont fortement typés et leur structure est validée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="d3fbf-108">La taille des paramètres table est uniquement limitée par la mémoire du serveur.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3fbf-109">Vous ne pouvez pas retourner de données dans un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="d3fbf-110">Les paramètres table sont des paramètres d'entrée uniquement ; le mot clé OUTPUT n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="d3fbf-111">Pour plus d'informations sur l'utilisation des paramètres table, consultez les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="d3fbf-112">Ressource</span><span class="sxs-lookup"><span data-stu-id="d3fbf-112">Resource</span></span>|<span data-ttu-id="d3fbf-113">Description</span><span class="sxs-lookup"><span data-stu-id="d3fbf-113">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="d3fbf-114">Utiliser les paramètres table (moteur de base de données)</span><span class="sxs-lookup"><span data-stu-id="d3fbf-114">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="d3fbf-115">Décrit comment créer et utiliser des paramètres table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="d3fbf-116">[Types de tables définis par l’utilisateur](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="d3fbf-116">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="d3fbf-117">Décrit les types de tables définis par l’utilisateur qui permettent de déclarer des paramètres table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="d3fbf-118">Passage de plusieurs lignes dans les versions précédentes de SQL Server</span><span class="sxs-lookup"><span data-stu-id="d3fbf-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="d3fbf-119">Avant l’introduction des paramètres table dans SQL Server 2008, les options permettant de passer plusieurs lignes de données à une procédure stockée ou à une commande SQL paramétrée étaient limitées.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="d3fbf-120">Un développeur pouvait choisir parmi les options suivantes pour passer plusieurs lignes au serveur :</span><span class="sxs-lookup"><span data-stu-id="d3fbf-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="d3fbf-121">Utiliser une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="d3fbf-122">La quantité des données qui peuvent être passées à l'aide de cette méthode est limitée par le nombre de paramètres autorisés.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="d3fbf-123">Les procédures SQL Server peuvent contenir jusqu’à 2 100 paramètres.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="d3fbf-124">La logique côté serveur est requise pour assembler ces valeurs individuelles dans une variable de table ou dans une table temporaire à des fins de traitement.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="d3fbf-125">Regrouper plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis passer ces valeurs texte à une procédure ou à une instruction.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="d3fbf-126">Cela implique pour la procédure ou l'instruction d'inclure la logique nécessaire permettant de valider les structures de données et de dégrouper les valeurs.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="d3fbf-127">Créer une série d'instructions SQL individuelles pour les modifications de données qui affectent plusieurs lignes, telles que celles créées en appelant la méthode `Update` d'un objet <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="d3fbf-128">Les modifications peuvent être soumises au serveur individuellement ou être traitées par lot dans des groupes.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="d3fbf-129">Cependant, même lorsqu'elles sont soumises dans des lots qui contiennent plusieurs instructions, chaque instruction est exécutée séparément sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="d3fbf-130">Utiliser l'utilitaire `bcp` ou l'objet <xref:System.Data.SqlClient.SqlBulkCopy> pour charger plusieurs lignes de données dans une table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="d3fbf-131">Même si cette technique est très efficace, elle ne prend pas en charge le traitement côté serveur sauf si les données sont chargées dans une table temporaire ou dans une variable de table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="d3fbf-132">Création de types de paramètre table</span><span class="sxs-lookup"><span data-stu-id="d3fbf-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="d3fbf-133">Les paramètres table sont basés sur des structures de table fortement typées qui sont définies à l’aide d’instructions Transact-SQL CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-133">Table-valued parameters are based on strongly-typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="d3fbf-134">Vous devez créer un type de table et définir la structure dans SQL Server avant de pouvoir utiliser les paramètres table dans vos applications clientes.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="d3fbf-135">Pour plus d’informations sur la création de types de table, consultez [types de tables définis par l’utilisateur](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="d3fbf-135">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="d3fbf-136">L'instruction suivante crée un type de table nommé CategoryTableType qui se compose des colonnes CategoryID et CategoryName :</span><span class="sxs-lookup"><span data-stu-id="d3fbf-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="d3fbf-137">Après avoir créé un type de table, vous pouvez déclarer des paramètres table basés sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="d3fbf-138">Le fragment Transact-SQL suivant montre comment déclarer un paramètre table dans une définition de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="d3fbf-139">Notez que le mot clé READONLY est obligatoire pour déclarer un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="d3fbf-140">Modification des données à l'aide des paramètres table (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d3fbf-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="d3fbf-141">Des paramètres table peuvent être utilisés dans des modifications de données basées sur des jeux qui affectent plusieurs lignes en exécutant une instruction unique.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="d3fbf-142">Par exemple, vous pouvez sélectionner toutes les lignes d'un paramètre table et les insérer dans une table de base de données, ou créer une instruction de mise à jour en joignant un paramètre table à la table à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="d3fbf-143">L’instruction Transact-SQL UPDATE suivante montre comment utiliser un paramètre table en le joignant à la table Categories.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="d3fbf-144">Lorsque vous utilisez un paramètre table avec une condition JOIN dans une clause FROM, vous devez également créer des alias pour celui-ci, comme ci-après, où le paramètre table se voit attribuer l'alias "ec" :</span><span class="sxs-lookup"><span data-stu-id="d3fbf-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="d3fbf-145">Cet exemple Transact-SQL montre comment sélectionner des lignes d’un paramètre table pour effectuer une insertion (INSERT) dans une opération basée sur un jeu unique.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="d3fbf-146">Limites des paramètres table</span><span class="sxs-lookup"><span data-stu-id="d3fbf-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="d3fbf-147">Les paramètres table présentent plusieurs limites :</span><span class="sxs-lookup"><span data-stu-id="d3fbf-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="d3fbf-148">Vous ne pouvez pas passer de paramètres table aux [fonctions CLR définies par l’utilisateur](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span><span class="sxs-lookup"><span data-stu-id="d3fbf-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="d3fbf-149">Les paramètres table peuvent uniquement être indexés pour prendre en charge les contraintes UNIQUE ou PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="d3fbf-150">SQL Server ne tient pas à jour de statistiques sur les paramètres table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="d3fbf-151">Les paramètres table sont en lecture seule dans le code Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="d3fbf-152">Vous ne pouvez pas mettre les valeurs de colonne à jour dans les lignes d'un paramètre table et vous ne pouvez pas insérer ni supprimer de ligne.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="d3fbf-153">Pour modifier les données qui sont passées à une procédure stockée ou à une instruction paramétrée dans un paramètre table, vous devez insérer les données dans une table temporaire ou dans une variable de table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="d3fbf-154">Vous ne pouvez pas utiliser d'instruction ALTER TABLE pour modifier la conception des paramètres table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="d3fbf-155">Exemple : configuration d'un SqlParameter</span><span class="sxs-lookup"><span data-stu-id="d3fbf-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="d3fbf-156"><xref:System.Data.SqlClient> prend en charge le remplissage des paramètres table à partir d’objets <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="d3fbf-157">Vous devez spécifier un nom de type pour le paramètre table à l’aide de la propriété <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> d’un objet <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="d3fbf-158">Le `TypeName` doit correspondre au nom d'un type compatible précédemment créé sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="d3fbf-159">Le fragment de code suivant montre comment configurer l'objet <xref:System.Data.SqlClient.SqlParameter> pour insérer des données.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
 
<span data-ttu-id="d3fbf-160">Dans l’exemple ci-dessous, la variable `addedCategories` contient un <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d3fbf-161">Pour voir comment la variable est remplie, consultez les exemples de la section suivante, [transmission d’un paramètre table à une procédure stockée](#passing).</span><span class="sxs-lookup"><span data-stu-id="d3fbf-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="d3fbf-162">Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table, tel qu’indiqué dans ce fragment :</span><span class="sxs-lookup"><span data-stu-id="d3fbf-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing"></a><span data-ttu-id="d3fbf-163">Passage d’un paramètre table à une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="d3fbf-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="d3fbf-164">Cet exemple montre comment passer des données de paramètre table à une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="d3fbf-165">Le code extrait les lignes ajoutées dans un nouvel objet <xref:System.Data.DataTable> à l'aide de la méthode <xref:System.Data.DataTable.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="d3fbf-166">Le code définit ensuite un objet <xref:System.Data.SqlClient.SqlCommand>, en affectant <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> à la propriété <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="d3fbf-167"><xref:System.Data.SqlClient.SqlParameter> est rempli à l'aide de la méthode <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> et <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> a la valeur `Structured`.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="d3fbf-168"><xref:System.Data.SqlClient.SqlCommand> est ensuite exécuté à l'aide de la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="d3fbf-169">Passage d'un paramètre table à une instruction SQL paramétrée</span><span class="sxs-lookup"><span data-stu-id="d3fbf-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="d3fbf-170">L'exemple suivant montre comment insérer des données dans la table dbo.Categories à l'aide de l'instruction INSERT avec une sous-requête SELECT qui a un paramètre table comme source de données.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="d3fbf-171">Lors du passage d'un paramètre table a une instruction SQL paramétrée, vous devez spécifier un nom de type pour le paramètre table à l'aide de la nouvelle propriété <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> d'un objet <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="d3fbf-172">Ce `TypeName` doit correspondre au nom d'un type compatible précédemment créé sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="d3fbf-173">Dans cet exemple, le code utilise la propriété `TypeName` pour référencer la structure de type définie dans dbo.CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3fbf-174">Si vous indiquez une valeur pour une colonne d'identité d'un paramètre table, vous devez émettre l'instruction SET IDENTITY_INSERT pour la session.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="d3fbf-175">Diffusion en continu des lignes à l'aide d'un objet DataReader</span><span class="sxs-lookup"><span data-stu-id="d3fbf-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="d3fbf-176">Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="d3fbf-177">Le fragment de code suivant montre comment extraire des données d'une base de données Oracle à l'aide d'un objet <xref:System.Data.OracleClient.OracleCommand> et d'un objet <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="d3fbf-178">Le code configure ensuite un objet <xref:System.Data.SqlClient.SqlCommand> pour appeler une procédure stockée avec un paramètre d'entrée unique.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="d3fbf-179">La propriété <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> de l'objet <xref:System.Data.SqlClient.SqlParameter> a la valeur `Structured`.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="d3fbf-180"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passe le jeu de résultats `OracleDataReader` à la procédure stockée sous la forme d'un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="d3fbf-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3fbf-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3fbf-181">See also</span></span>

- [<span data-ttu-id="d3fbf-182">Configuration des paramètres et des types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="d3fbf-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="d3fbf-183">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="d3fbf-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="d3fbf-184">Paramètres DataAdapter</span><span class="sxs-lookup"><span data-stu-id="d3fbf-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="d3fbf-185">Opérations sur les données SQL Server dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d3fbf-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="d3fbf-186">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d3fbf-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
