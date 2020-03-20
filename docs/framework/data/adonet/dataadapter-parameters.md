---
title: Paramètres DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 9954570dcf33c5eea4dcccf880de2c307de0aeca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151544"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="90979-102">Paramètres DataAdapter</span><span class="sxs-lookup"><span data-stu-id="90979-102">DataAdapter Parameters</span></span>
<span data-ttu-id="90979-103">L'objet <xref:System.Data.Common.DbDataAdapter> possède quatre propriétés qui sont utilisées pour récupérer des données dans la source de données et y mettre des données à jour : la propriété <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> retourne des données de la source de données et les propriétés <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> et <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> sont utilisées pour gérer les modifications au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="90979-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="90979-104">La  propriété `SelectCommand` doit être définie avant d'appeler la méthode `Fill` du `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="90979-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="90979-105">Les propriétés `InsertCommand`, `UpdateCommand` ou `DeleteCommand` doivent être définies avant que la méthode `Update` du `DataAdapter` ne soit appelée, en fonction des modifications qui ont été apportées aux données dans le <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="90979-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="90979-106">Par exemple, si des lignes ont été ajoutées, `InsertCommand` doit être défini avant d'appeler `Update`.</span><span class="sxs-lookup"><span data-stu-id="90979-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="90979-107">Lorsque `Update` traite une ligne insérée, mise à jour ou supprimée, le `DataAdapter` utilise la propriété `Command` respective pour traiter l'action.</span><span class="sxs-lookup"><span data-stu-id="90979-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="90979-108">Les informations actuelles concernant la ligne modifiée sont passées à l’objet `Command` par le biais de la collection `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="90979-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="90979-109">Lorsque vous mettez à jour une ligne à la source de données, vous appelez l’instruction UPDATE, qui utilise un identifiant unique pour identifier la ligne dans la table à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="90979-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="90979-110">Cet identificateur unique est généralement la valeur d'un champ de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="90979-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="90979-111">L'instruction UPDATE utilise les paramètres qui contiennent l'identificateur unique ainsi que les colonnes et les valeurs à mettre à jour, comme indiqué dans l'instruction Transact-SQL suivante.</span><span class="sxs-lookup"><span data-stu-id="90979-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="90979-112">La syntaxe des espaces réservés des paramètres dépend de la source de données.</span><span class="sxs-lookup"><span data-stu-id="90979-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="90979-113">Cet exemple montre les espaces réservés pour une source de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90979-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="90979-114">Utilisez des espaces réservés point d'interrogation (?) pour les paramètres <xref:System.Data.OleDb> et <xref:System.Data.Odbc>.</span><span class="sxs-lookup"><span data-stu-id="90979-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="90979-115">Dans cet exemple de `CompanyName` base visuelle, le `@CompanyName` champ est mis `CustomerID` à jour avec `@CustomerID` la valeur du paramètre pour la ligne où correspond à la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="90979-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="90979-116">Les paramètres récupèrent les informations <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> de la <xref:System.Data.SqlClient.SqlParameter> ligne modifiée à l’aide de la propriété de l’objet.</span><span class="sxs-lookup"><span data-stu-id="90979-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="90979-117">Les paramètres suivants sont ceux de l'instruction UPDATE de l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="90979-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="90979-118">Le code est basé sur l'hypothèse que la variable `adapter` représente un objet <xref:System.Data.SqlClient.SqlDataAdapter> valide.</span><span class="sxs-lookup"><span data-stu-id="90979-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="90979-119">La méthode `Add` de la collection `Parameters` prend le nom du paramètre, le type de données, la taille (si elle est applicable au type) et le nom de la propriété <xref:System.Data.Common.DbParameter.SourceColumn%2A> du `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="90979-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="90979-120">Notez que la propriété <xref:System.Data.Common.DbParameter.SourceVersion%2A> du paramètre `@CustomerID` a la valeur `Original`.</span><span class="sxs-lookup"><span data-stu-id="90979-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="90979-121">Cela garantit que la ligne existante dans la source de données est mise à jour si la valeur de la ou des colonnes d'identification a été modifiée dans l'objet <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="90979-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="90979-122">Dans ce cas, la valeur de ligne `Original` correspondrait à la valeur actuelle de la source de données et la valeur de ligne `Current` contiendrait la valeur mise à jour.</span><span class="sxs-lookup"><span data-stu-id="90979-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="90979-123">Le `SourceVersion` du paramètre `@CompanyName` n'est pas défini et utilise la valeur de ligne `Current` par défaut.</span><span class="sxs-lookup"><span data-stu-id="90979-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90979-124">Pour les `Fill` opérations `DataAdapter` et `Get` les méthodes `DataReader`de la , le type cadre .NET est déduit du type retourné du fournisseur de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90979-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="90979-125">Les types de frameworks .NET déduits et les méthodes d’accesseur pour Microsoft SQL Server, OLE DB et ODBC types de données sont décrits dans [les cartographies de type de données dans ADO.NET](data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="90979-125">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="90979-126">Parameter.SourceColumn, Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="90979-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="90979-127">Le `SourceColumn` et `SourceVersion` peuvent être passés comme arguments au constructeur `Parameter`ou définis comme propriétés d'un `Parameter` existant.</span><span class="sxs-lookup"><span data-stu-id="90979-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="90979-128">`SourceColumn` est le nom de l'objet <xref:System.Data.DataColumn> provenant de l'objet <xref:System.Data.DataRow> dans lequel la valeur de `Parameter` sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="90979-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="90979-129">`SourceVersion` spécifie la version du `DataRow` que le `DataAdapter` utilise pour récupérer la valeur.</span><span class="sxs-lookup"><span data-stu-id="90979-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="90979-130">Le tableau suivant présente les valeurs d'énumération <xref:System.Data.DataRowVersion> disponibles pour être utilisées avec `SourceVersion`.</span><span class="sxs-lookup"><span data-stu-id="90979-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="90979-131">Énumération DataRowVersion</span><span class="sxs-lookup"><span data-stu-id="90979-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="90979-132">Description</span><span class="sxs-lookup"><span data-stu-id="90979-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="90979-133">Le paramètre utilise la valeur actuelle de la colonne.</span><span class="sxs-lookup"><span data-stu-id="90979-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="90979-134">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="90979-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="90979-135">Ce paramètre utilise le `DefaultValue` de la colomne.</span><span class="sxs-lookup"><span data-stu-id="90979-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="90979-136">Le paramètre utilise la valeur d'origine de la colonne.</span><span class="sxs-lookup"><span data-stu-id="90979-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="90979-137">Le paramètre utilise une valeur proposée.</span><span class="sxs-lookup"><span data-stu-id="90979-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="90979-138">L'exemple de code `SqlClient` de la section suivante définit un paramètre d'une propriété <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> dans lequel la colonne `CustomerID` est utilisée comme `SourceColumn` pour deux paramètres : `@CustomerID` (`SET CustomerID = @CustomerID`) et `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span><span class="sxs-lookup"><span data-stu-id="90979-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="90979-139">Le `@CustomerID` paramètre est utilisé pour mettre à jour `DataRow`la colonne **CustomerID** à la valeur actuelle dans le .</span><span class="sxs-lookup"><span data-stu-id="90979-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="90979-140">En conséquence, `CustomerID` `SourceColumn` le `SourceVersion` avec `Current` un de est utilisé.</span><span class="sxs-lookup"><span data-stu-id="90979-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="90979-141">Le `@OldCustomerID` paramètre est utilisé pour identifier la ligne actuelle dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="90979-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="90979-142">Puisque la valeur de colonne correspondante se trouve dans la version `Original` de la ligne, le même `SourceColumn` (`CustomerID`) avec un `SourceVersion` ayant la valeur `Original` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="90979-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="90979-143">Utilisation de paramètres SqlClient</span><span class="sxs-lookup"><span data-stu-id="90979-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="90979-144">L'exemple suivant montre comment créer un objet <xref:System.Data.SqlClient.SqlDataAdapter> et affecter la valeur <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> à la propriété <xref:System.Data.MissingSchemaAction.AddWithKey> de manière à récupérer des informations de schéma supplémentaires de la base de données.</span><span class="sxs-lookup"><span data-stu-id="90979-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="90979-145">Les propriétés <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> et <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> définies, ainsi que les objets <xref:System.Data.SqlClient.SqlParameter> correspondants ajoutés à la collection <xref:System.Data.SqlClient.SqlCommand.Parameters%2A>.</span><span class="sxs-lookup"><span data-stu-id="90979-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="90979-146">La méthode retourne un objet `SqlDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="90979-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="90979-147">Espaces réservés pour les paramètres OleDb</span><span class="sxs-lookup"><span data-stu-id="90979-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="90979-148">Pour les objets <xref:System.Data.OleDb.OleDbDataAdapter> et <xref:System.Data.Odbc.OdbcDataAdapter>, vous devez utiliser les espaces réservés point d'interrogation (?) pour identifier les paramètres.</span><span class="sxs-lookup"><span data-stu-id="90979-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="90979-149">Les instructions de requête paramétrées définissent les paramètres d'entrée et de sortie à créer.</span><span class="sxs-lookup"><span data-stu-id="90979-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="90979-150">Pour créer un paramètre, utilisez la méthode `Parameters.Add` ou le constructeur `Parameter` pour spécifier le nom de colonne, le type de données et la taille.</span><span class="sxs-lookup"><span data-stu-id="90979-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="90979-151">Pour les types de données intrinsèques, comme `Integer`, il n'est pas nécessaire d'inclure la taille, ou vous pouvez spécifier la taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="90979-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="90979-152">L'exemple de code suivant crée les paramètres d'une instruction SQL et remplit un `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="90979-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="90979-153">Exemple OleDb</span><span class="sxs-lookup"><span data-stu-id="90979-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="90979-154">Paramètres Odbc</span><span class="sxs-lookup"><span data-stu-id="90979-154">Odbc Parameters</span></span>  
  
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
> <span data-ttu-id="90979-155">Si un nom de paramètre n’est pas fourni pour un paramètre, le paramètre reçoit un nom par défaut différentiel de*ParaN* *,* en commençant par "Parameter1".</span><span class="sxs-lookup"><span data-stu-id="90979-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="90979-156">Nous vous recommandons d’éviter la convention de nommage Paramét*N* lorsque vous fournissez `ParameterCollection`un nom de paramètre, parce que le nom que vous fournissez pourrait entrer en conflit avec un nom de paramètre par défaut existant dans le .</span><span class="sxs-lookup"><span data-stu-id="90979-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="90979-157">Si le nom fourni existe déjà, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="90979-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90979-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90979-158">See also</span></span>

- [<span data-ttu-id="90979-159">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="90979-159">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="90979-160">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="90979-160">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="90979-161">Mise à jour des sources de données avec les DataAdapter</span><span class="sxs-lookup"><span data-stu-id="90979-161">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="90979-162">Modification des données avec les procédures stockées</span><span class="sxs-lookup"><span data-stu-id="90979-162">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="90979-163">Mappages de types de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90979-163">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="90979-164">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90979-164">ADO.NET Overview</span></span>](ado-net-overview.md)
