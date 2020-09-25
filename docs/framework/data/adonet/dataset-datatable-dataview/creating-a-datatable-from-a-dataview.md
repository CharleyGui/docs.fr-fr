---
title: Création d'un DataTable à partir d'un DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d45cf41-d8ae-4409-af3e-a96a7e476d85
ms.openlocfilehash: 42843ec40f4f7271526e341dc53bdbc2ef11db38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198728"
---
# <a name="creating-a-datatable-from-a-dataview"></a><span data-ttu-id="26f11-102">Création d'un DataTable à partir d'un DataView</span><span class="sxs-lookup"><span data-stu-id="26f11-102">Creating a DataTable from a DataView</span></span>

<span data-ttu-id="26f11-103">Après avoir extrait des données d'une source de données et rempli un objet <xref:System.Data.DataTable> avec les données, vous pouvez trier, filtrer ou limiter d'une autre manière les données retournées sans devoir les extraire de nouveau.</span><span class="sxs-lookup"><span data-stu-id="26f11-103">Once you have retrieved data from a data source, and have filled a <xref:System.Data.DataTable> with the data, you may want to sort, filter, or otherwise limit the returned data without retrieving it again.</span></span> <span data-ttu-id="26f11-104">La classe <xref:System.Data.DataView> le permet.</span><span class="sxs-lookup"><span data-stu-id="26f11-104">The <xref:System.Data.DataView> class makes this possible.</span></span> <span data-ttu-id="26f11-105">En outre, si vous devez créer un nouveau <xref:System.Data.DataTable> à partir de la <xref:System.Data.DataView> , vous pouvez utiliser la <xref:System.Data.DataView.ToTable%2A> méthode pour copier toutes les lignes et les colonnes, ou un sous-ensemble des données dans un nouveau <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="26f11-105">In addition, if you need to create a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView>, you can use the <xref:System.Data.DataView.ToTable%2A> method to copy all the rows and columns, or a subset of the data into a new <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="26f11-106">La méthode <xref:System.Data.DataView.ToTable%2A> fournit des surcharges pour :</span><span class="sxs-lookup"><span data-stu-id="26f11-106">The <xref:System.Data.DataView.ToTable%2A> method provides overloads to:</span></span>  
  
- <span data-ttu-id="26f11-107">créer un objet <xref:System.Data.DataTable> contenant des colonnes qui sont un sous-ensemble des colonnes de l'objet <xref:System.Data.DataView> ;</span><span class="sxs-lookup"><span data-stu-id="26f11-107">Create a <xref:System.Data.DataTable> containing columns that are a subset of the columns in the <xref:System.Data.DataView>.</span></span>  
  
- <span data-ttu-id="26f11-108">Créez un <xref:System.Data.DataTable> qui n’inclue que des lignes distinctes de, de la même façon que <xref:System.Data.DataView> le mot clé distinct dans Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="26f11-108">Create a <xref:System.Data.DataTable> that includes only distinct rows from the <xref:System.Data.DataView>, analogously to the DISTINCT keyword in Transact-SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26f11-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="26f11-109">Example</span></span>  

 <span data-ttu-id="26f11-110">L’exemple d’application console suivant crée un <xref:System.Data.DataTable> qui contient les données de la table **Person. contact** dans l’exemple de base de données **AdventureWorks** .</span><span class="sxs-lookup"><span data-stu-id="26f11-110">The following console application example creates a <xref:System.Data.DataTable> that contains data from the **Person.Contact** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="26f11-111">Ensuite, l’exemple crée un trié et filtré <xref:System.Data.DataView> en fonction du <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="26f11-111">Next, the example creates a sorted and filtered <xref:System.Data.DataView> based on the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="26f11-112">Après avoir affiché le contenu du <xref:System.Data.DataTable> et du <xref:System.Data.DataView> , l’exemple crée un nouveau <xref:System.Data.DataTable> à partir du <xref:System.Data.DataView> en appelant la <xref:System.Data.DataView.ToTable%2A> méthode, en sélectionnant uniquement un sous-ensemble des colonnes disponibles.</span><span class="sxs-lookup"><span data-stu-id="26f11-112">After displaying the contents of the <xref:System.Data.DataTable> and the <xref:System.Data.DataView>, the example creates a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView> by calling the <xref:System.Data.DataView.ToTable%2A> method, selecting only a subset of the available columns.</span></span> <span data-ttu-id="26f11-113">Pour terminer, l'exemple affiche le contenu du nouvel objet <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="26f11-113">Finally, the example displays the contents of the new <xref:System.Data.DataTable>.</span></span>  
  
```vb  
Private Sub DemonstrateDataView()  
    ' Retrieve a DataTable from the AdventureWorks sample database.  
    ' connectionString is assumed to be a valid connection string.  
    Dim adapter As New SqlDataAdapter( _  
       "SELECT FirstName, LastName, EmailAddress FROM Person.Contact WHERE FirstName LIKE 'Mich%'", connectionString)  
    Dim table As New DataTable  
  
    adapter.Fill(table)  
    Console.WriteLine("Original table name: " & table.TableName)  
    ' Print current table values.  
    PrintTableOrView(table, "Current Values in Table")  
  
    ' Now create a DataView based on the DataTable.  
    ' Sort and filter the data.  
    Dim view As DataView = table.DefaultView  
    view.Sort = "LastName, FirstName"  
    view.RowFilter = "LastName > 'M'"  
    PrintTableOrView(view, "Current Values in View")  
  
    ' Create a new DataTable based on the DataView,  
    ' requesting only two columns with distinct values  
    ' in the columns.  
    Dim newTable As DataTable = view.ToTable("UniqueLastNames", True, "FirstName", "LastName")  
    PrintTableOrView(newTable, "Table created from DataView")  
    Console.WriteLine("New table name: " & newTable.TableName)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
    End Sub  
  
Private Sub PrintTableOrView(ByVal dv As DataView, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
    Dim table As DataTable = dv.Table  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the view.  
    For Each rowView As DataRowView In dv  
        sw = New System.IO.StringWriter  
  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(rowView(col.ColumnName).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
End Sub  
  
Private Sub PrintTableOrView(ByVal table As DataTable, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the table.  
    For Each row As DataRow In table.Rows  
        sw = New System.IO.StringWriter  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(row(col).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
    End Sub  
End Module  
```  
  
```csharp  
private static void DemonstrateDataView()  
{  
// Retrieve a DataTable from the AdventureWorks sample database.  
// connectionString is assumed to be a valid connection string.  
SqlDataAdapter adapter = new SqlDataAdapter(  
    "SELECT FirstName, LastName, EmailAddress " +  
    "FROM Person.Contact WHERE FirstName LIKE 'Mich%'",
       GetConnectionString());  
DataTable table = new DataTable();  
  
adapter.Fill(table);  
Console.WriteLine("Original table name: " + table.TableName);  
// Print current table values.  
PrintTableOrView(table, "Current Values in Table");  
  
// Now create a DataView based on the DataTable.  
// Sort and filter the data.  
DataView view = table.DefaultView;  
view.Sort = "LastName, FirstName";  
view.RowFilter = "LastName > 'M'";  
PrintTableOrView(view, "Current Values in View");  
  
// Create a new DataTable based on the DataView,  
// requesting only two columns with distinct values  
// in the columns.  
DataTable newTable = view.ToTable("UniqueLastNames",  
     true, "FirstName", "LastName");  
PrintTableOrView(newTable, "Table created from DataView");  
Console.WriteLine("New table name: " + newTable.TableName);  
  
Console.WriteLine("Press any key to continue.");  
Console.ReadKey();  
}  
  
private static void PrintTableOrView(DataView dv, string label)  
{  
System.IO.StringWriter sw;  
string output;  
DataTable table = dv.Table;  
  
Console.WriteLine(label);  
  
// Loop through each row in the view.  
foreach (DataRowView rowView in dv)  
{  
    sw = new System.IO.StringWriter();  
  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(rowView[col.ColumnName].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
}  
Console.WriteLine();  
}  
  
private static void PrintTableOrView(DataTable table, string label)  
{  
System.IO.StringWriter sw;  
string output;  
  
Console.WriteLine(label);  
  
// Loop through each row in the table.  
foreach (DataRow row in table.Rows)  
{  
    sw = new System.IO.StringWriter();  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(row[col].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
} //  
Console.WriteLine();  
}  
```  
  
 <span data-ttu-id="26f11-114">}</span><span class="sxs-lookup"><span data-stu-id="26f11-114">}</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f11-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26f11-115">See also</span></span>

- <xref:System.Data.DataView.ToTable%2A>
- [<span data-ttu-id="26f11-116">DataViews</span><span class="sxs-lookup"><span data-stu-id="26f11-116">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="26f11-117">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="26f11-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
