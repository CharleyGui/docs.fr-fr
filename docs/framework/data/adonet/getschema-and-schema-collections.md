---
title: Collections GetSchema et Schema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: cea9deb7fe019fea189a87fc08468d010929db9a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177447"
---
# <a name="getschema-and-schema-collections"></a>Collections GetSchema et Schema

Les classes de **connexion** de chacun des .NET Framework fournisseurs managés implémentent une méthode **GetSchema** qui est utilisée pour récupérer des informations de schéma sur la base de données actuellement connectée, et les informations de schéma retournées par la méthode **GetSchema** sont fournies sous la forme d’un <xref:System.Data.DataTable> . La méthode **GetSchema** est une méthode surchargée qui fournit des paramètres facultatifs pour spécifier la collection de schémas à retourner et restreindre la quantité d’informations retournées.  
  
## <a name="specifying-the-schema-collections"></a>Spécification des collections de schémas  

 Le premier paramètre facultatif de la méthode **GetSchema** est le nom de la collection qui est spécifié en tant que chaîne. Il y a deux types de collection de schémas : les collections de schémas communes qui sont communes à tous les fournisseurs et les collections de schémas spécifiques qui sont spécifiques à chaque fournisseur.  
  
 Vous pouvez interroger un fournisseur managé .NET Framework pour déterminer la liste des collections de schémas prises en charge en appelant la méthode **GetSchema** sans argument ou avec le nom de la collection de schémas « MetaDataCollections ». Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu’elles prennent en charge et le nombre d’éléments d’identification qu’elles utilisent.  
  
### <a name="retrieving-schema-collections-example"></a>Exemple d'extraction de collections de schémas  

 Les exemples suivants montrent comment utiliser la <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> méthode de la .NET Framework fournisseur de données pour la classe SQL Server <xref:System.Data.SqlClient.SqlConnection> pour récupérer des informations de schéma sur toutes les tables contenues dans l’exemple de base de données **AdventureWorks** :  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
   End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
   Console.WriteLine("Press any key to continue.");  
   Console.ReadKey();  
   }  
 }  
  
  private static string GetConnectionString()  
  {  
   // To avoid storing the connection string in your code,  
   // you can retrieve it from a configuration file.  
   return "Data Source=(local);Database=AdventureWorks;" +  
      "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Extraction des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
