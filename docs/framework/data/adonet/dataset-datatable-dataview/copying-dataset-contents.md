---
title: Copie de contenu de DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151362"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="7a933-102">Copie de contenu de DataSet</span><span class="sxs-lookup"><span data-stu-id="7a933-102">Copying DataSet Contents</span></span>
<span data-ttu-id="7a933-103">Vous pouvez créer une <xref:System.Data.DataSet> copie d’un afin que vous puissiez travailler avec des données sans affecter les données d’origine, ou travailler avec un sous-ensemble des données à partir d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7a933-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="7a933-104">Lors de la copie d’un **DataSet**, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="7a933-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="7a933-105">Créez une copie exacte du **DataSet**, y compris le schéma, les données, les informations d’état de ligne et les versions de ligne.</span><span class="sxs-lookup"><span data-stu-id="7a933-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="7a933-106">Créez un **ensemble de données** qui contient le schéma d’un **DataSet**existant, mais seulement des lignes qui ont été modifiées.</span><span class="sxs-lookup"><span data-stu-id="7a933-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="7a933-107">Vous pouvez retourner toutes les lignes qui ont été modifiées, ou spécifier un **DataRowState**spécifique .</span><span class="sxs-lookup"><span data-stu-id="7a933-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="7a933-108">Pour plus d’informations sur les états de ligne, voir [Row States et Row Versions](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="7a933-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="7a933-109">Copiez le schéma, ou structure relationnelle, du **DataSet** seulement, sans copier les lignes.</span><span class="sxs-lookup"><span data-stu-id="7a933-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="7a933-110">Les lignes peuvent être importées dans un objet <xref:System.Data.DataTable> existant à l'aide de la méthode <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a933-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="7a933-111">Pour créer une copie exacte du **DataSet** qui comprend <xref:System.Data.DataSet.Copy%2A> à la fois le schéma et les données, utilisez la méthode du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7a933-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="7a933-112">L’exemple de code suivant montre comment créer une copie exacte du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7a933-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="7a933-113">Pour créer une copie d’un ensemble de **données** qui comprend le schéma et uniquement <xref:System.Data.DataSet.GetChanges%2A> les données représentant les lignes **ajoutées,** **modifiées**ou **supprimées,** utilisez la méthode du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7a933-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="7a933-114">Vous pouvez également utiliser **GetChanges** pour retourner uniquement les lignes avec un état de ligne spécifié en passant une valeur **DataRowState** lors de l’appel **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="7a933-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="7a933-115">L’exemple de code suivant montre comment passer un **DataRowState** lors de l’appel **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="7a933-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="7a933-116">Pour créer une copie d’un **ensemble** de <xref:System.Data.DataSet.Clone%2A> données qui ne comprend que des schémas, utilisez la méthode du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7a933-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="7a933-117">Vous pouvez également ajouter des lignes existantes au **DataSet** cloné à l’aide de la méthode **ImportRow** de la **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="7a933-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="7a933-118">**ImportRow** ajoute des données, l’état de la ligne et les informations de version de ligne à la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7a933-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="7a933-119">Les valeurs de colonne ne seront ajoutées que si le nom de colonne est identique et le type de données compatible.</span><span class="sxs-lookup"><span data-stu-id="7a933-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="7a933-120">L’exemple de code suivant crée un clone d’un **DataSet,** puis ajoute les lignes de l’original **DataSet** à la table **des clients** dans le clone **DataSet** pour les clients où la colonne **CountryRegion** a la valeur "Allemagne".</span><span class="sxs-lookup"><span data-stu-id="7a933-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a933-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a933-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="7a933-122">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="7a933-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7a933-123">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7a933-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
