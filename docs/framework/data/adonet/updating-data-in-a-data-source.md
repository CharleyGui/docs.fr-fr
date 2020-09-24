---
title: Mise à jour des données dans une source de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 6b0234337c85ace0797d75b72560ccb55635daae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177265"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="8f1e0-102">Mise à jour des données dans une source de données</span><span class="sxs-lookup"><span data-stu-id="8f1e0-102">Updating Data in a Data Source</span></span>

<span data-ttu-id="8f1e0-103">Les instructions SQL qui modifient les données (comme INSERT, UPDATE ou DELETE) ne retournent pas de ligne.</span><span class="sxs-lookup"><span data-stu-id="8f1e0-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="8f1e0-104">De même, de nombreuses procédures stockées effectuent une action mais ne retournent pas de ligne.</span><span class="sxs-lookup"><span data-stu-id="8f1e0-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="8f1e0-105">Pour exécuter des commandes qui ne retournent pas de lignes, créez un objet **Command** avec la commande SQL appropriée et une **connexion**, y compris tous les **paramètres**requis.</span><span class="sxs-lookup"><span data-stu-id="8f1e0-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="8f1e0-106">Exécutez la commande avec la méthode **ExecuteNonQuery** de l’objet **Command** .</span><span class="sxs-lookup"><span data-stu-id="8f1e0-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="8f1e0-107">La méthode **ExecuteNonQuery** retourne un entier qui représente le nombre de lignes affectées par l’instruction ou la procédure stockée qui a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="8f1e0-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="8f1e0-108">Si plusieurs instructions sont exécutées, la valeur retournée est la somme des enregistrements affectés par toutes ces instructions.</span><span class="sxs-lookup"><span data-stu-id="8f1e0-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f1e0-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f1e0-109">Example</span></span>  

 <span data-ttu-id="8f1e0-110">L’exemple de code suivant exécute une instruction INSERT pour insérer un enregistrement dans une base de données à l’aide de **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="8f1e0-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="8f1e0-111">L’exemple de code suivant exécute la procédure stockée créée par l’exemple de code lors de l' [exécution d’opérations de catalogue](performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8f1e0-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="8f1e0-112">Aucune ligne n’est retournée par la procédure stockée. la méthode **ExecuteNonQuery** est donc utilisée, mais la procédure stockée ne reçoit pas de paramètre d’entrée et retourne un paramètre de sortie et une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="8f1e0-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="8f1e0-113">Pour l' <xref:System.Data.OleDb.OleDbCommand> objet, le paramètre **returnValue** doit être d’abord ajouté à la collection **Parameters** .</span><span class="sxs-lookup"><span data-stu-id="8f1e0-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f1e0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f1e0-114">See also</span></span>

- [<span data-ttu-id="8f1e0-115">Utilisation des commandes pour modifier les données</span><span class="sxs-lookup"><span data-stu-id="8f1e0-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="8f1e0-116">Mise à jour des sources de données avec les DataAdapter</span><span class="sxs-lookup"><span data-stu-id="8f1e0-116">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="8f1e0-117">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="8f1e0-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="8f1e0-118">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8f1e0-118">ADO.NET Overview</span></span>](ado-net-overview.md)
