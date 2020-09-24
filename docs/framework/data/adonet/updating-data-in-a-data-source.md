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
# <a name="updating-data-in-a-data-source"></a>Mise à jour des données dans une source de données

Les instructions SQL qui modifient les données (comme INSERT, UPDATE ou DELETE) ne retournent pas de ligne. De même, de nombreuses procédures stockées effectuent une action mais ne retournent pas de ligne. Pour exécuter des commandes qui ne retournent pas de lignes, créez un objet **Command** avec la commande SQL appropriée et une **connexion**, y compris tous les **paramètres**requis. Exécutez la commande avec la méthode **ExecuteNonQuery** de l’objet **Command** .  
  
 La méthode **ExecuteNonQuery** retourne un entier qui représente le nombre de lignes affectées par l’instruction ou la procédure stockée qui a été exécutée. Si plusieurs instructions sont exécutées, la valeur retournée est la somme des enregistrements affectés par toutes ces instructions.  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant exécute une instruction INSERT pour insérer un enregistrement dans une base de données à l’aide de **ExecuteNonQuery**.  
  
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
  
 L’exemple de code suivant exécute la procédure stockée créée par l’exemple de code lors de l' [exécution d’opérations de catalogue](performing-catalog-operations.md). Aucune ligne n’est retournée par la procédure stockée. la méthode **ExecuteNonQuery** est donc utilisée, mais la procédure stockée ne reçoit pas de paramètre d’entrée et retourne un paramètre de sortie et une valeur de retour.  
  
 Pour l' <xref:System.Data.OleDb.OleDbCommand> objet, le paramètre **returnValue** doit être d’abord ajouté à la collection **Parameters** .  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des commandes pour modifier les données](using-commands-to-modify-data.md)
- [Mise à jour des sources de données avec les DataAdapter](updating-data-sources-with-dataadapters.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
