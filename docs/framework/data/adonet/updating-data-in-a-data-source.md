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
# <a name="updating-data-in-a-data-source"></a>Mise à jour des données dans une source de données
Les instructions SQL qui modifient les données (comme INSERT, UPDATE ou DELETE) ne retournent pas de ligne. De même, de nombreuses procédures stockées effectuent une action mais ne retournent pas de ligne. Pour exécuter des commandes qui ne renvoient pas les lignes, créez un objet **de commande** avec la commande SQL appropriée et une **connexion,** y compris les **paramètres**requis. Exécutez la commande avec la méthode **ExecuteNonQuery** de l’objet **de commande.**  
  
 La méthode **ExecuteNonQuery** renvoie un intégriste qui représente le nombre de lignes affectées par la déclaration ou la procédure stockée qui a été exécutée. Si plusieurs instructions sont exécutées, la valeur retournée est la somme des enregistrements affectés par toutes ces instructions.  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant exécute une déclaration INSERT pour insérer un enregistrement dans une base de données à l’aide **d’ExecuteNonQuery**.  
  
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
  
 L’exemple de code suivant exécute la procédure stockée créée par le code d’échantillon dans [Performing Catalog Operations](performing-catalog-operations.md). Aucune ligne n’est retournée par la procédure stockée, de sorte que la méthode **ExecuteNonQuery** est utilisée, mais la procédure stockée ne reçoivent un paramètre d’entrée et retourne un paramètre de sortie et une valeur de retour.  
  
 Pour <xref:System.Data.OleDb.OleDbCommand> l’objet, le paramètre **ReturnValue** doit d’abord être ajouté à la collection **Paramètres.**  
  
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
