---
title: Paramètres table
description: Découvrez comment marshaler plusieurs lignes de données d’une application cliente en SQL Server à l’aide de paramètres table.
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 7b1f0a6c416f660f06cea099197ba136f84407f9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286195"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="374f4-103">Paramètres table</span><span class="sxs-lookup"><span data-stu-id="374f4-103">Table-Valued Parameters</span></span>
<span data-ttu-id="374f4-104">Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données.</span><span class="sxs-lookup"><span data-stu-id="374f4-104">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="374f4-105">Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique.</span><span class="sxs-lookup"><span data-stu-id="374f4-105">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="374f4-106">Les lignes de données entrantes sont stockées dans une variable de table que vous pouvez ensuite utiliser à l’aide de Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="374f4-106">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="374f4-107">Les valeurs de colonne dans les paramètres table sont accessibles à l’aide d’instructions Transact-SQL SELECT standard.</span><span class="sxs-lookup"><span data-stu-id="374f4-107">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="374f4-108">Les paramètres table sont fortement typés et leur structure est validée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="374f4-108">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="374f4-109">La taille des paramètres table est limitée uniquement par la mémoire du serveur.</span><span class="sxs-lookup"><span data-stu-id="374f4-109">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="374f4-110">Vous ne pouvez pas renvoyer de données dans un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="374f4-110">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="374f4-111">car il prennent uniquement des valeurs d’entrée ; le mot clé OUTPUT n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="374f4-111">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="374f4-112">Pour plus d’informations sur les paramètres table, consultez les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="374f4-112">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="374f4-113">Ressource</span><span class="sxs-lookup"><span data-stu-id="374f4-113">Resource</span></span>|<span data-ttu-id="374f4-114">Description</span><span class="sxs-lookup"><span data-stu-id="374f4-114">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="374f4-115">Utiliser les paramètres table (Moteur de base de données)</span><span class="sxs-lookup"><span data-stu-id="374f4-115">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="374f4-116">Décrit comment créer et utiliser des paramètres table.</span><span class="sxs-lookup"><span data-stu-id="374f4-116">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="374f4-117">[Types de tables définis par l'utilisateur](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="374f4-117">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="374f4-118">Décrit les types de tables définis par l’utilisateur qui permettent de déclarer des paramètres table.</span><span class="sxs-lookup"><span data-stu-id="374f4-118">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="374f4-119">Passage de plusieurs lignes dans les versions précédentes de SQL Server</span><span class="sxs-lookup"><span data-stu-id="374f4-119">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="374f4-120">Avant l’introduction des paramètres table dans SQL Server 2008, les options permettant de passer plusieurs lignes de données à une procédure stockée ou à une commande SQL paramétrée étaient limitées.</span><span class="sxs-lookup"><span data-stu-id="374f4-120">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="374f4-121">Un développeur peut choisir parmi les options suivantes pour transmettre plusieurs lignes au serveur :</span><span class="sxs-lookup"><span data-stu-id="374f4-121">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="374f4-122">Utilisez une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données.</span><span class="sxs-lookup"><span data-stu-id="374f4-122">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="374f4-123">La quantité de données transmissibles selon cette méthode est limitée par le nombre de paramètres autorisés.</span><span class="sxs-lookup"><span data-stu-id="374f4-123">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="374f4-124">Les procédures SQL Server peuvent contenir jusqu’à 2 100 paramètres.</span><span class="sxs-lookup"><span data-stu-id="374f4-124">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="374f4-125">Une logique côté serveur est requise pour assembler ces différentes valeurs dans une variable de table ou une table temporaire à des fins de traitement.</span><span class="sxs-lookup"><span data-stu-id="374f4-125">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="374f4-126">Regroupez plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis transmettez ces valeurs de texte à une procédure ou une instruction.</span><span class="sxs-lookup"><span data-stu-id="374f4-126">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="374f4-127">Cela requiert que la procédure ou l’instruction inclue la logique nécessaire pour valider les structures de données et dissocier les valeurs.</span><span class="sxs-lookup"><span data-stu-id="374f4-127">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="374f4-128">Créez une série d’instructions SQL pour les modifications de données qui affectent plusieurs lignes, telles que celles créées en appelant la méthode `Update` d’un <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="374f4-128">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="374f4-129">Les modifications peuvent être envoyées au serveur individuellement ou regroupées par lot.</span><span class="sxs-lookup"><span data-stu-id="374f4-129">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="374f4-130">Toutefois, même lorsqu’elles sont soumises dans des lots contenant plusieurs instructions, chaque instruction est exécutée séparément sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="374f4-130">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="374f4-131">Utilisez le programme utilitaire `bcp` ou l’objet <xref:System.Data.SqlClient.SqlBulkCopy> pour charger de nombreuses lignes de données dans une table.</span><span class="sxs-lookup"><span data-stu-id="374f4-131">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="374f4-132">Bien que cette technique soit très efficace, elle ne prend pas en charge le traitement côté serveur à moins que les données ne soient chargées dans une table temporaire ou une variable table.</span><span class="sxs-lookup"><span data-stu-id="374f4-132">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="374f4-133">Création de types de paramètre table</span><span class="sxs-lookup"><span data-stu-id="374f4-133">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="374f4-134">Les paramètres table sont basés sur des structures de table fortement typées qui sont définies à l’aide des instructions Transact-SQL CREATe TYPE.</span><span class="sxs-lookup"><span data-stu-id="374f4-134">Table-valued parameters are based on strongly typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="374f4-135">Vous devez créer un type de table et définir la structure dans SQL Server avant de pouvoir utiliser les paramètres table dans vos applications clientes.</span><span class="sxs-lookup"><span data-stu-id="374f4-135">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="374f4-136">Pour plus d’informations sur la création de types de table, consultez [types de tables définis par l’utilisateur](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="374f4-136">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="374f4-137">L’instruction suivante crée un type table nommé CategoryTableType qui se compose de colonnes CategoryID et CategoryName :</span><span class="sxs-lookup"><span data-stu-id="374f4-137">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="374f4-138">Après avoir créé un type table, vous pouvez déclarer des paramètres table basés sur ce type.</span><span class="sxs-lookup"><span data-stu-id="374f4-138">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="374f4-139">Le fragment Transact-SQL suivant montre comment déclarer un paramètre table dans une définition de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="374f4-139">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="374f4-140">Notez que le mot clé READONLY est requis pour déclarer un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="374f4-140">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="374f4-141">Modification des données à l'aide des paramètres table (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="374f4-141">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="374f4-142">Les paramètres table peuvent être utilisés dans des modifications de données basées sur des jeux qui affectent plusieurs lignes en exécutant une instruction unique.</span><span class="sxs-lookup"><span data-stu-id="374f4-142">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="374f4-143">Par exemple, vous pouvez sélectionner toutes les lignes d’un paramètre table et les insérer dans une table de base de données, ou créer une instruction de mise à jour en joignant un paramètre table à la table à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="374f4-143">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="374f4-144">L’instruction Transact-SQL UPDATE suivante montre comment utiliser un paramètre table en le joignant à la table Categories.</span><span class="sxs-lookup"><span data-stu-id="374f4-144">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="374f4-145">Si vous utilisez un paramètre table avec un JOIN dans une clause FROM, vous devez également créer un alias pour celui-ci (ici, le paramètre table a pour alias « ec ») :</span><span class="sxs-lookup"><span data-stu-id="374f4-145">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="374f4-146">Cet exemple Transact-SQL montre comment sélectionner des lignes d’un paramètre table pour effectuer une insertion (INSERT) dans une opération basée sur un jeu unique.</span><span class="sxs-lookup"><span data-stu-id="374f4-146">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="374f4-147">Limites des paramètres table</span><span class="sxs-lookup"><span data-stu-id="374f4-147">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="374f4-148">Les paramètres table présentent plusieurs limitations :</span><span class="sxs-lookup"><span data-stu-id="374f4-148">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="374f4-149">Vous ne pouvez pas passer de paramètres table aux [fonctions CLR définies par l’utilisateur](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span><span class="sxs-lookup"><span data-stu-id="374f4-149">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="374f4-150">Les paramètres table peuvent uniquement être indexés pour prendre en charge les contraintes UNIQUE ou PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="374f4-150">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="374f4-151">SQL Server ne tient pas à jour de statistiques sur les paramètres table.</span><span class="sxs-lookup"><span data-stu-id="374f4-151">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="374f4-152">Les paramètres table sont en lecture seule dans le code Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="374f4-152">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="374f4-153">Il n’est pas possible de mettre à jour les valeurs de colonne dans les lignes d’un paramètre table, ni d’insérer ou de supprimer des lignes.</span><span class="sxs-lookup"><span data-stu-id="374f4-153">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="374f4-154">Pour modifier les données transmises à une procédure stockée ou à une instruction paramétrable dans un paramètre table, il faut les insérer dans une table temporaire ou une variable de table.</span><span class="sxs-lookup"><span data-stu-id="374f4-154">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="374f4-155">Vous ne pouvez pas utiliser d’instructions ALTER TABLE pour modifier la conception de paramètres table.</span><span class="sxs-lookup"><span data-stu-id="374f4-155">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="374f4-156">Exemple : configuration d'un SqlParameter</span><span class="sxs-lookup"><span data-stu-id="374f4-156">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="374f4-157"><xref:System.Data.SqlClient> prend en charge le remplissage des paramètres table à partir d’objets <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord>.</span><span class="sxs-lookup"><span data-stu-id="374f4-157"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="374f4-158">Vous devez spécifier un nom de type pour le paramètre table à l’aide de la propriété <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> d’un objet <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="374f4-158">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="374f4-159">Le `TypeName` doit correspondre au nom d’un type compatible précédemment créé sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="374f4-159">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="374f4-160">Le fragment de code suivant montre comment configurer <xref:System.Data.SqlClient.SqlParameter> pour insérer des données.</span><span class="sxs-lookup"><span data-stu-id="374f4-160">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="374f4-161">Dans l’exemple ci-dessous, la variable `addedCategories` contient un <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="374f4-161">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="374f4-162">Pour voir comment la variable est remplie, consultez les exemples de la section suivante, [Passage d'un paramètre table à une procédure stockée](#passing).</span><span class="sxs-lookup"><span data-stu-id="374f4-162">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

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
  
 <span data-ttu-id="374f4-163">Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table, tel qu’indiqué dans ce fragment :</span><span class="sxs-lookup"><span data-stu-id="374f4-163">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a><span data-ttu-id="374f4-164">Passage d’un paramètre table à une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="374f4-164">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="374f4-165">Cet exemple montre comment passer des données de paramètre table à une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="374f4-165">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="374f4-166">Le code extrait des lignes ajoutées dans une nouvelle <xref:System.Data.DataTable> à l’aide de la méthode <xref:System.Data.DataTable.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="374f4-166">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="374f4-167">Le code définit ensuite une <xref:System.Data.SqlClient.SqlCommand>, en définissant la propriété <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> sur la valeur <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="374f4-167">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="374f4-168"><xref:System.Data.SqlClient.SqlParameter> est rempli à l’aide de la méthode <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> et le <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> est défini sur `Structured`.</span><span class="sxs-lookup"><span data-stu-id="374f4-168">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="374f4-169">La <xref:System.Data.SqlClient.SqlCommand> est ensuite exécutée à l’aide de la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.</span><span class="sxs-lookup"><span data-stu-id="374f4-169">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="374f4-170">Passage d'un paramètre table à une instruction SQL paramétrée</span><span class="sxs-lookup"><span data-stu-id="374f4-170">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="374f4-171">L’exemple suivant montre comment insérer des données dans la table dbo.Categories à l’aide d’une instruction INSERT avec une sous-requête SELECT qui a un paramètre table comme source de données.</span><span class="sxs-lookup"><span data-stu-id="374f4-171">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="374f4-172">Lors du passage d’un paramètre table à une instruction SQL paramétrable, vous devez spécifier un nom de type pour le paramètre table à l’aide de la nouvelle propriété <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> d’un <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="374f4-172">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="374f4-173">Ce `TypeName` doit correspondre au nom d’un type compatible précédemment créé sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="374f4-173">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="374f4-174">Le code de cet exemple utilise la propriété `TypeName` pour référencer la structure de type définie dans dbo.CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="374f4-174">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="374f4-175">Si vous fournissez une valeur pour une colonne d’identité dans un paramètre table, vous devez émettre l’instruction SET IDENTITY_INSERT pour la session.</span><span class="sxs-lookup"><span data-stu-id="374f4-175">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="374f4-176">Diffusion en continu des lignes à l'aide d'un objet DataReader</span><span class="sxs-lookup"><span data-stu-id="374f4-176">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="374f4-177">Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table.</span><span class="sxs-lookup"><span data-stu-id="374f4-177">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="374f4-178">Le fragment de code suivant montre comment récupérer des données d’une base de données Oracle à l’aide d’une <xref:System.Data.OracleClient.OracleCommand> et d’un <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="374f4-178">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="374f4-179">Le code configure ensuite une <xref:System.Data.SqlClient.SqlCommand> pour appeler une procédure stockée avec un seul paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="374f4-179">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="374f4-180">La propriété <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> du <xref:System.Data.SqlClient.SqlParameter> a la valeur `Structured`.</span><span class="sxs-lookup"><span data-stu-id="374f4-180">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="374f4-181"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> transmet le jeu de résultats `OracleDataReader` à la procédure stockée en tant que paramètre table.</span><span class="sxs-lookup"><span data-stu-id="374f4-181">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="374f4-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="374f4-182">See also</span></span>

- [<span data-ttu-id="374f4-183">Configuration des paramètres et des types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="374f4-183">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="374f4-184">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="374f4-184">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="374f4-185">Paramètres DataAdapter</span><span class="sxs-lookup"><span data-stu-id="374f4-185">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="374f4-186">SQL Server des opérations de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="374f4-186">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="374f4-187">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="374f4-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
