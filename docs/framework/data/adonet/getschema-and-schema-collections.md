---
title: Collections GetSchema et Schema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: e18c23e9bbec97a64110aba6eb7241761ecece06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149555"
---
# <a name="getschema-and-schema-collections"></a>Collections GetSchema et Schema
Les classes **de connexion** dans chacun des fournisseurs gérés par le cadre .NET implémentent une méthode **GetSchema** qui est utilisée pour récupérer les <xref:System.Data.DataTable>informations schématiques sur la base de données qui est actuellement connectée, et les informations schéma retournées de la méthode **GetSchema** se présente sous la forme d’un . La méthode **GetSchema** est une méthode surchargée qui fournit des paramètres facultatifs pour spécifier la collecte de schémas à revenir, et de limiter la quantité d’informations retournées.  
  
## <a name="specifying-the-schema-collections"></a>Spécification des collections de schémas  
 Le premier paramètre facultatif de la méthode **GetSchema** est le nom de collection qui est spécifié comme une chaîne. Il y a deux types de collection de schémas : les collections de schémas communes qui sont communes à tous les fournisseurs et les collections de schémas spécifiques qui sont spécifiques à chaque fournisseur.  
  
 Vous pouvez interroger un fournisseur géré par .NET Framework pour déterminer la liste des collections de schémas pris en charge en appelant la méthode **GetSchema** sans arguments, ou avec le nom de collection de schémas "MetaDataCollections". Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu’elles prennent en charge et le nombre d’éléments d’identification qu’elles utilisent.  
  
### <a name="retrieving-schema-collections-example"></a>Exemple d'extraction de collections de schémas  
 Les exemples suivants démontrent <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> comment utiliser la méthode du fournisseur <xref:System.Data.SqlClient.SqlConnection> de données-cadres .NET pour la classe SQL Server pour récupérer des informations schématiques sur toutes les tables contenues dans la base de données de l’échantillon **AdventureWorks** :  
  
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

- [Récupération des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
