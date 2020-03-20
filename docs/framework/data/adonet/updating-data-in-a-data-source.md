---
title: Mise à jour des données dans une source de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 18bb03e17b19243ee1bc6e3f7ebd70afb4d4c60b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174444"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="afbdb-102">Mise à jour des données dans une source de données</span><span class="sxs-lookup"><span data-stu-id="afbdb-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="afbdb-103">Les instructions SQL qui modifient les données (comme INSERT, UPDATE ou DELETE) ne retournent pas de ligne.</span><span class="sxs-lookup"><span data-stu-id="afbdb-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="afbdb-104">De même, de nombreuses procédures stockées effectuent une action mais ne retournent pas de ligne.</span><span class="sxs-lookup"><span data-stu-id="afbdb-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="afbdb-105">Pour exécuter des commandes qui ne renvoient pas les lignes, créez un objet **de commande** avec la commande SQL appropriée et une **connexion,** y compris les **paramètres**requis.</span><span class="sxs-lookup"><span data-stu-id="afbdb-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="afbdb-106">Exécutez la commande avec la méthode **ExecuteNonQuery** de l’objet **de commande.**</span><span class="sxs-lookup"><span data-stu-id="afbdb-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="afbdb-107">La méthode **ExecuteNonQuery** renvoie un intégriste qui représente le nombre de lignes affectées par la déclaration ou la procédure stockée qui a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="afbdb-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="afbdb-108">Si plusieurs instructions sont exécutées, la valeur retournée est la somme des enregistrements affectés par toutes ces instructions.</span><span class="sxs-lookup"><span data-stu-id="afbdb-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afbdb-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="afbdb-109">Example</span></span>  
 <span data-ttu-id="afbdb-110">L’exemple de code suivant exécute une déclaration INSERT pour insérer un enregistrement dans une base de données à l’aide **d’ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="afbdb-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 <span data-ttu-id="afbdb-111">L’exemple de code suivant exécute la procédure stockée créée par le code d’échantillon dans [Performing Catalog Operations](performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="afbdb-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="afbdb-112">Aucune ligne n’est retournée par la procédure stockée, de sorte que la méthode **ExecuteNonQuery** est utilisée, mais la procédure stockée ne reçoivent un paramètre d’entrée et retourne un paramètre de sortie et une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="afbdb-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="afbdb-113">Pour <xref:System.Data.OleDb.OleDbCommand> l’objet, le paramètre **ReturnValue** doit d’abord être ajouté à la collection **Paramètres.**</span><span class="sxs-lookup"><span data-stu-id="afbdb-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a><span data-ttu-id="afbdb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afbdb-114">See also</span></span>

- [<span data-ttu-id="afbdb-115">Utilisation des commandes pour modifier les données</span><span class="sxs-lookup"><span data-stu-id="afbdb-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="afbdb-116">Mise à jour des sources de données avec les DataAdapter</span><span class="sxs-lookup"><span data-stu-id="afbdb-116">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="afbdb-117">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="afbdb-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="afbdb-118">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="afbdb-118">ADO.NET Overview</span></span>](ado-net-overview.md)
