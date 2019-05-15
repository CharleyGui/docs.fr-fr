---
title: Paramètres DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 0cdca872e9e76b7491dc571209292a692a06d8f8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583755"
---
# <a name="dataadapter-parameters"></a>Paramètres DataAdapter
L'objet <xref:System.Data.Common.DbDataAdapter> possède quatre propriétés qui sont utilisées pour récupérer des données dans la source de données et y mettre des données à jour : la propriété <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> retourne des données de la source de données et les propriétés <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> et <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> sont utilisées pour gérer les modifications au niveau de la source de données. La  propriété `SelectCommand` doit être définie avant d'appeler la méthode `Fill` du `DataAdapter`. Les propriétés `InsertCommand`, `UpdateCommand` ou `DeleteCommand` doivent être définies avant que la méthode `Update` du `DataAdapter` ne soit appelée, en fonction des modifications qui ont été apportées aux données dans le <xref:System.Data.DataTable>. Par exemple, si des lignes ont été ajoutées, `InsertCommand` doit être défini avant d'appeler `Update`. Lorsque `Update` traite une ligne insérée, mise à jour ou supprimée, le `DataAdapter` utilise la propriété `Command` respective pour traiter l'action. Les informations actuelles concernant la ligne modifiée sont passées à l’objet `Command` par le biais de la collection `Parameters`.  
  
 Lorsque vous mettez à jour une ligne à la source de données, vous appelez l’instruction de mise à jour, qui utilise un identificateur unique pour identifier la ligne dans la table à mettre à jour. Cet identificateur unique est généralement la valeur d'un champ de clé primaire. L'instruction UPDATE utilise les paramètres qui contiennent l'identificateur unique ainsi que les colonnes et les valeurs à mettre à jour, comme indiqué dans l'instruction Transact-SQL suivante.  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  La syntaxe des espaces réservés des paramètres dépend de la source de données. Cet exemple montre les espaces réservés pour une source de données SQL Server. Utilisez des espaces réservés point d'interrogation (?) pour les paramètres <xref:System.Data.OleDb> et <xref:System.Data.Odbc>.  
  
 Dans cet exemple Visual Basic, le `CompanyName` champ est mis à jour avec la valeur de la `@CompanyName` paramètre pour la ligne où `CustomerID` est égal à la valeur de la `@CustomerID` paramètre. Les paramètres extraient les informations à partir de la ligne modifiée à l’aide de la <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> propriété de la <xref:System.Data.SqlClient.SqlParameter> objet. Les paramètres suivants sont ceux de l'instruction UPDATE de l'exemple précédent. Le code est basé sur l'hypothèse que la variable `adapter` représente un objet <xref:System.Data.SqlClient.SqlDataAdapter> valide.  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 La méthode `Add` de la collection `Parameters` prend le nom du paramètre, le type de données, la taille (si elle est applicable au type) et le nom de la propriété <xref:System.Data.Common.DbParameter.SourceColumn%2A> du `DataTable`. Notez que la propriété <xref:System.Data.Common.DbParameter.SourceVersion%2A> du paramètre `@CustomerID` a la valeur `Original`. Cela garantit que la ligne existante dans la source de données est mise à jour si la valeur de la ou des colonnes d'identification a été modifiée dans l'objet <xref:System.Data.DataRow>. Dans ce cas, la valeur de ligne `Original` correspondrait à la valeur actuelle de la source de données et la valeur de ligne `Current` contiendrait la valeur mise à jour. Le `SourceVersion` du paramètre `@CompanyName` n'est pas défini et utilise la valeur de ligne `Current` par défaut.  
  
> [!NOTE]
>  Pour les deux le `Fill` opérations de la `DataAdapter` et `Get` méthodes de la `DataReader`, le type .NET Framework est déduit à partir du type retourné par le fournisseur de données .NET Framework. Les types déduits de .NET Framework et les méthodes d’accesseur pour les types de données Microsoft SQL Server, OLE DB et ODBC sont décrites dans [mappages de Type de données dans ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn, Parameter.SourceVersion  
 Le `SourceColumn` et `SourceVersion` peuvent être passés comme arguments au constructeur `Parameter`ou définis comme propriétés d'un `Parameter` existant. `SourceColumn` est le nom de l'objet <xref:System.Data.DataColumn> provenant de l'objet <xref:System.Data.DataRow> dans lequel la valeur de `Parameter` sera récupérée. `SourceVersion` spécifie la version du `DataRow` que le `DataAdapter` utilise pour récupérer la valeur.  
  
 Le tableau suivant présente les valeurs d'énumération <xref:System.Data.DataRowVersion> disponibles pour être utilisées avec `SourceVersion`.  
  
|Énumération DataRowVersion|Description|  
|--------------------------------|-----------------|  
|`Current`|Le paramètre utilise la valeur actuelle de la colonne. Il s'agit de la valeur par défaut.|  
|`Default`|Ce paramètre utilise le `DefaultValue` de la colomne.|  
|`Original`|Le paramètre utilise la valeur d'origine de la colonne.|  
|`Proposed`|Le paramètre utilise une valeur proposée.|  
  
 L'exemple de code `SqlClient` de la section suivante définit un paramètre d'une propriété <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> dans lequel la colonne `CustomerID` est utilisée comme `SourceColumn` pour deux paramètres : `@CustomerID` (`SET CustomerID = @CustomerID`) et `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`). Le `@CustomerID` paramètre est utilisé pour mettre à jour le **CustomerID** colonne à la valeur actuelle dans le `DataRow`. Par conséquent, le `CustomerID` `SourceColumn` avec un `SourceVersion` de `Current` est utilisé. Le `@OldCustomerID` paramètre est utilisé pour identifier la ligne actuelle dans la source de données. Puisque la valeur de colonne correspondante se trouve dans la version `Original` de la ligne, le même `SourceColumn` (`CustomerID`) avec un `SourceVersion` ayant la valeur `Original` est utilisé.  
  
## <a name="working-with-sqlclient-parameters"></a>Utilisation de paramètres SqlClient  
 L'exemple suivant montre comment créer un objet <xref:System.Data.SqlClient.SqlDataAdapter> et affecter la valeur <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> à la propriété <xref:System.Data.MissingSchemaAction.AddWithKey> de manière à récupérer des informations de schéma supplémentaires de la base de données. Les propriétés <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> et <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> définies, ainsi que les objets <xref:System.Data.SqlClient.SqlParameter> correspondants ajoutés à la collection <xref:System.Data.SqlClient.SqlCommand.Parameters%2A>. La méthode retourne un objet `SqlDataAdapter`.  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>Espaces réservés pour les paramètres OleDb  
 Pour les objets <xref:System.Data.OleDb.OleDbDataAdapter> et <xref:System.Data.Odbc.OdbcDataAdapter>, vous devez utiliser les espaces réservés point d'interrogation (?) pour identifier les paramètres.  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =   
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =   
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =   
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 Les instructions de requête paramétrées définissent les paramètres d'entrée et de sortie à créer. Pour créer un paramètre, utilisez la méthode `Parameters.Add` ou le constructeur `Parameter` pour spécifier le nom de colonne, le type de données et la taille. Pour les types de données intrinsèques, comme `Integer`, il n'est pas nécessaire d'inclure la taille, ou vous pouvez spécifier la taille par défaut.  
  
 L'exemple de code suivant crée les paramètres d'une instruction SQL et remplit un `DataSet`.  
  
## <a name="oledb-example"></a>Exemple OleDb  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter   
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## <a name="odbc-parameters"></a>Paramètres Odbc  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  Si un nom de paramètre n’est pas fourni pour un paramètre, le paramètre reçoit un nom incrémentiel par défaut du paramètre*N* *,* en commençant par « Parameter1 ». Nous vous recommandons d’éviter le paramètre*N* convention de dénomination lorsque vous fournissez un nom de paramètre, car le nom que vous fournissez peut entrer en conflit avec un nom de paramètre par défaut existant dans le `ParameterCollection`. Si le nom fourni existe déjà, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Mise à jour de sources de données avec des DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [Modification des données avec les procédures stockées](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [Mappages de types de données dans ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
