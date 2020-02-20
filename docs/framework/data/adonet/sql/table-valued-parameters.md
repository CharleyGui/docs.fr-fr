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
# <a name="table-valued-parameters"></a>Paramètres table
Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table que vous pouvez ensuite utiliser à l’aide de Transact-SQL.  
  
 Les valeurs de colonne dans les paramètres table sont accessibles à l’aide d’instructions Transact-SQL SELECT standard. Les paramètres table sont fortement typés et leur structure est validée automatiquement. La taille des paramètres table est uniquement limitée par la mémoire du serveur.  
  
> [!NOTE]
> Vous ne pouvez pas retourner de données dans un paramètre table. Les paramètres table sont des paramètres d'entrée uniquement ; le mot clé OUTPUT n'est pas pris en charge.  
  
 Pour plus d'informations sur l'utilisation des paramètres table, consultez les ressources suivantes.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Utiliser les paramètres table (moteur de base de données)](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|Décrit comment créer et utiliser des paramètres table.|  
|[Types de tables définis par l’utilisateur](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))|Décrit les types de tables définis par l’utilisateur qui permettent de déclarer des paramètres table.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Passage de plusieurs lignes dans les versions précédentes de SQL Server  
 Avant l’introduction des paramètres table dans SQL Server 2008, les options permettant de passer plusieurs lignes de données à une procédure stockée ou à une commande SQL paramétrée étaient limitées. Un développeur pouvait choisir parmi les options suivantes pour passer plusieurs lignes au serveur :  
  
- Utiliser une série de paramètres individuels pour représenter les valeurs dans plusieurs colonnes et lignes de données. La quantité des données qui peuvent être passées à l'aide de cette méthode est limitée par le nombre de paramètres autorisés. Les procédures SQL Server peuvent contenir jusqu’à 2 100 paramètres. La logique côté serveur est requise pour assembler ces valeurs individuelles dans une variable de table ou dans une table temporaire à des fins de traitement.  
  
- Regrouper plusieurs valeurs de données dans des chaînes délimitées ou des documents XML, puis passer ces valeurs texte à une procédure ou à une instruction. Cela implique pour la procédure ou l'instruction d'inclure la logique nécessaire permettant de valider les structures de données et de dégrouper les valeurs.  
  
- Créer une série d'instructions SQL individuelles pour les modifications de données qui affectent plusieurs lignes, telles que celles créées en appelant la méthode `Update` d'un objet <xref:System.Data.SqlClient.SqlDataAdapter>. Les modifications peuvent être soumises au serveur individuellement ou être traitées par lot dans des groupes. Cependant, même lorsqu'elles sont soumises dans des lots qui contiennent plusieurs instructions, chaque instruction est exécutée séparément sur le serveur.  
  
- Utiliser l'utilitaire `bcp` ou l'objet <xref:System.Data.SqlClient.SqlBulkCopy> pour charger plusieurs lignes de données dans une table. Même si cette technique est très efficace, elle ne prend pas en charge le traitement côté serveur sauf si les données sont chargées dans une table temporaire ou dans une variable de table.  
  
## <a name="creating-table-valued-parameter-types"></a>Création de types de paramètre table  
 Les paramètres table sont basés sur des structures de table fortement typées qui sont définies à l’aide d’instructions Transact-SQL CREATE TYPE. Vous devez créer un type de table et définir la structure dans SQL Server avant de pouvoir utiliser les paramètres table dans vos applications clientes. Pour plus d’informations sur la création de types de table, consultez [types de tables définis par l’utilisateur](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).  
  
 L'instruction suivante crée un type de table nommé CategoryTableType qui se compose des colonnes CategoryID et CategoryName :  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Après avoir créé un type de table, vous pouvez déclarer des paramètres table basés sur celui-ci. Le fragment Transact-SQL suivant montre comment déclarer un paramètre table dans une définition de procédure stockée. Notez que le mot clé READONLY est obligatoire pour déclarer un paramètre table.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modification des données à l'aide des paramètres table (Transact-SQL)  
 Des paramètres table peuvent être utilisés dans des modifications de données basées sur des jeux qui affectent plusieurs lignes en exécutant une instruction unique. Par exemple, vous pouvez sélectionner toutes les lignes d'un paramètre table et les insérer dans une table de base de données, ou créer une instruction de mise à jour en joignant un paramètre table à la table à mettre à jour.  
  
 L’instruction Transact-SQL UPDATE suivante montre comment utiliser un paramètre table en le joignant à la table Categories. Lorsque vous utilisez un paramètre table avec une condition JOIN dans une clause FROM, vous devez également créer des alias pour celui-ci, comme ci-après, où le paramètre table se voit attribuer l'alias "ec" :  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 Cet exemple Transact-SQL montre comment sélectionner des lignes d’un paramètre table pour effectuer une insertion (INSERT) dans une opération basée sur un jeu unique.  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Limites des paramètres table  
 Les paramètres table présentent plusieurs limites :  
  
- Vous ne pouvez pas passer de paramètres table aux [fonctions CLR définies par l’utilisateur](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).  
  
- Les paramètres table peuvent uniquement être indexés pour prendre en charge les contraintes UNIQUE ou PRIMARY KEY. SQL Server ne tient pas à jour de statistiques sur les paramètres table.  
  
- Les paramètres table sont en lecture seule dans le code Transact-SQL. Vous ne pouvez pas mettre les valeurs de colonne à jour dans les lignes d'un paramètre table et vous ne pouvez pas insérer ni supprimer de ligne. Pour modifier les données qui sont passées à une procédure stockée ou à une instruction paramétrée dans un paramètre table, vous devez insérer les données dans une table temporaire ou dans une variable de table.  
  
- Vous ne pouvez pas utiliser d'instruction ALTER TABLE pour modifier la conception des paramètres table.  
  
## <a name="configuring-a-sqlparameter-example"></a>Exemple : configuration d'un SqlParameter  
 <xref:System.Data.SqlClient> prend en charge le remplissage des paramètres table à partir d’objets <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord>. Vous devez spécifier un nom de type pour le paramètre table à l’aide de la propriété <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> d’un objet <xref:System.Data.SqlClient.SqlParameter>. Le `TypeName` doit correspondre au nom d'un type compatible précédemment créé sur le serveur. Le fragment de code suivant montre comment configurer l'objet <xref:System.Data.SqlClient.SqlParameter> pour insérer des données.  
 
Dans l’exemple ci-dessous, la variable `addedCategories` contient un <xref:System.Data.DataTable>. Pour voir comment la variable est remplie, consultez les exemples de la section suivante, [transmission d’un paramètre table à une procédure stockée](#passing).

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
  
 Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table, tel qu’indiqué dans ce fragment :  
  
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
  
## <a name="passing"></a>Passage d’un paramètre table à une procédure stockée  
 Cet exemple montre comment passer des données de paramètre table à une procédure stockée. Le code extrait les lignes ajoutées dans un nouvel objet <xref:System.Data.DataTable> à l'aide de la méthode <xref:System.Data.DataTable.GetChanges%2A>. Le code définit ensuite un objet <xref:System.Data.SqlClient.SqlCommand>, en affectant <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> à la propriété <xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlParameter> est rempli à l'aide de la méthode <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> et <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> a la valeur `Structured`. <xref:System.Data.SqlClient.SqlCommand> est ensuite exécuté à l'aide de la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Passage d'un paramètre table à une instruction SQL paramétrée  
 L'exemple suivant montre comment insérer des données dans la table dbo.Categories à l'aide de l'instruction INSERT avec une sous-requête SELECT qui a un paramètre table comme source de données. Lors du passage d'un paramètre table a une instruction SQL paramétrée, vous devez spécifier un nom de type pour le paramètre table à l'aide de la nouvelle propriété <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> d'un objet <xref:System.Data.SqlClient.SqlParameter>. Ce `TypeName` doit correspondre au nom d'un type compatible précédemment créé sur le serveur. Dans cet exemple, le code utilise la propriété `TypeName` pour référencer la structure de type définie dans dbo.CategoryTableType.  
  
> [!NOTE]
> Si vous indiquez une valeur pour une colonne d'identité d'un paramètre table, vous devez émettre l'instruction SET IDENTITY_INSERT pour la session.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>Diffusion en continu des lignes à l'aide d'un objet DataReader  
 Vous pouvez également utiliser n’importe quel objet dérivé de l’objet <xref:System.Data.Common.DbDataReader> pour transmettre en continu des lignes de données à un paramètre table. Le fragment de code suivant montre comment extraire des données d'une base de données Oracle à l'aide d'un objet <xref:System.Data.OracleClient.OracleCommand> et d'un objet <xref:System.Data.OracleClient.OracleDataReader>. Le code configure ensuite un objet <xref:System.Data.SqlClient.SqlCommand> pour appeler une procédure stockée avec un paramètre d'entrée unique. La propriété <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> de l'objet <xref:System.Data.SqlClient.SqlParameter> a la valeur `Structured`. <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passe le jeu de résultats `OracleDataReader` à la procédure stockée sous la forme d'un paramètre table.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Configuration des paramètres et des types de données des paramètres](../configuring-parameters-and-parameter-data-types.md)
- [Commandes et paramètres](../commands-and-parameters.md)
- [Paramètres DataAdapter](../dataadapter-parameters.md)
- [Opérations sur les données SQL Server dans ADO.NET](sql-server-data-operations.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
