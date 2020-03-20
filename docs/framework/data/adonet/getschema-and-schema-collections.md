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
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="1fd70-102">Collections GetSchema et Schema</span><span class="sxs-lookup"><span data-stu-id="1fd70-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="1fd70-103">Les classes **de connexion** dans chacun des fournisseurs gérés par le cadre .NET implémentent une méthode **GetSchema** qui est utilisée pour récupérer les <xref:System.Data.DataTable>informations schématiques sur la base de données qui est actuellement connectée, et les informations schéma retournées de la méthode **GetSchema** se présente sous la forme d’un .</span><span class="sxs-lookup"><span data-stu-id="1fd70-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1fd70-104">La méthode **GetSchema** est une méthode surchargée qui fournit des paramètres facultatifs pour spécifier la collecte de schémas à revenir, et de limiter la quantité d’informations retournées.</span><span class="sxs-lookup"><span data-stu-id="1fd70-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="1fd70-105">Spécification des collections de schémas</span><span class="sxs-lookup"><span data-stu-id="1fd70-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="1fd70-106">Le premier paramètre facultatif de la méthode **GetSchema** est le nom de collection qui est spécifié comme une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1fd70-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="1fd70-107">Il y a deux types de collection de schémas : les collections de schémas communes qui sont communes à tous les fournisseurs et les collections de schémas spécifiques qui sont spécifiques à chaque fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1fd70-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="1fd70-108">Vous pouvez interroger un fournisseur géré par .NET Framework pour déterminer la liste des collections de schémas pris en charge en appelant la méthode **GetSchema** sans arguments, ou avec le nom de collection de schémas "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="1fd70-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="1fd70-109">Cette opération retourne un <xref:System.Data.DataTable> avec une liste des collections de schémas prises en charge, le nombre de restrictions qu’elles prennent en charge et le nombre d’éléments d’identification qu’elles utilisent.</span><span class="sxs-lookup"><span data-stu-id="1fd70-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="1fd70-110">Exemple d'extraction de collections de schémas</span><span class="sxs-lookup"><span data-stu-id="1fd70-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="1fd70-111">Les exemples suivants démontrent <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> comment utiliser la méthode du fournisseur <xref:System.Data.SqlClient.SqlConnection> de données-cadres .NET pour la classe SQL Server pour récupérer des informations schématiques sur toutes les tables contenues dans la base de données de l’échantillon **AdventureWorks** :</span><span class="sxs-lookup"><span data-stu-id="1fd70-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1fd70-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fd70-112">See also</span></span>

- [<span data-ttu-id="1fd70-113">Récupération des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="1fd70-113">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="1fd70-114">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1fd70-114">ADO.NET Overview</span></span>](ado-net-overview.md)
