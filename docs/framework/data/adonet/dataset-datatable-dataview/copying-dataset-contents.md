---
title: Copie de contenu de DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: 1cadcacab6084bbf3caaf61d98b78fe3067d92f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202368"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="d3b7c-102">Copie de contenu de DataSet</span><span class="sxs-lookup"><span data-stu-id="d3b7c-102">Copying DataSet Contents</span></span>

<span data-ttu-id="d3b7c-103">Vous pouvez créer une copie de afin de pouvoir <xref:System.Data.DataSet> utiliser des données sans affecter les données d’origine, ou utiliser un sous-ensemble des données d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="d3b7c-104">Lors de la copie d’un **jeu de données**, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="d3b7c-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="d3b7c-105">Créez une copie exacte du **DataSet**, y compris le schéma, les données, les informations d’état de ligne et les versions de ligne.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="d3b7c-106">Créez un **DataSet** qui contient le schéma d’un **DataSet**existant, mais uniquement les lignes qui ont été modifiées.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="d3b7c-107">Vous pouvez retourner toutes les lignes qui ont été modifiées ou spécifier un **DataRowState**spécifique.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="d3b7c-108">Pour plus d’informations sur les États de ligne, consultez [États de ligne et versions de ligne](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="d3b7c-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="d3b7c-109">Copiez le schéma, ou structure relationnelle, du **DataSet** uniquement, sans copier les lignes.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="d3b7c-110">Les lignes peuvent être importées dans un objet <xref:System.Data.DataTable> existant à l'aide de la méthode <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="d3b7c-111">Pour créer une copie exacte du **DataSet** qui comprend à la fois le schéma et les données, utilisez la <xref:System.Data.DataSet.Copy%2A> méthode du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d3b7c-112">L’exemple de code suivant montre comment créer une copie exacte du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="d3b7c-113">Pour créer une copie d’un **DataSet** qui comprend le schéma et uniquement les données qui représentent des lignes **ajoutées**, **modifiées**ou **supprimées** , utilisez la <xref:System.Data.DataSet.GetChanges%2A> méthode du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d3b7c-114">Vous pouvez également utiliser **GetChanges** pour retourner uniquement les lignes avec un état de ligne spécifié en passant une valeur **DataRowState** lors de l’appel de **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="d3b7c-115">L’exemple de code suivant montre comment passer un **DataRowState** lors de l’appel de **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="d3b7c-116">Pour créer une copie d’un **DataSet** qui n’inclue que le schéma, utilisez la <xref:System.Data.DataSet.Clone%2A> méthode du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="d3b7c-117">Vous pouvez également ajouter des lignes existantes au DataSet cloné à l’aide de la méthode **ImportRow** de l' **objet** **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="d3b7c-118">**ImportRow** ajoute des données, un état de ligne et des informations de version de ligne à la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="d3b7c-119">Les valeurs de colonne ne seront ajoutées que si le nom de colonne est identique et le type de données compatible.</span><span class="sxs-lookup"><span data-stu-id="d3b7c-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="d3b7c-120">L’exemple de code suivant crée un clone d’un **DataSet** , puis ajoute les lignes du **DataSet** d’origine à la table **Customers** dans le clone du **jeu de données** pour les clients où la colonne **PaysRégion** a la valeur « Germany ».</span><span class="sxs-lookup"><span data-stu-id="d3b7c-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3b7c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3b7c-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="d3b7c-122">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="d3b7c-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="d3b7c-123">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d3b7c-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
