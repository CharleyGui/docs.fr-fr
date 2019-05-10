---
title: Copie de contenu de DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: 29afeb84498f2b1d000940ddc28545602a44d408
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626151"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="15949-102">Copie de contenu de DataSet</span><span class="sxs-lookup"><span data-stu-id="15949-102">Copying DataSet Contents</span></span>
<span data-ttu-id="15949-103">Vous pouvez créer une copie d’un <xref:System.Data.DataSet> afin que vous pouvez travailler avec des données sans affecter les données d’origine, ou travailler avec un sous-ensemble des données à partir d’un **jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="15949-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="15949-104">Lorsque vous copiez un **DataSet**, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="15949-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="15949-105">Créer une copie exacte de la **DataSet**, y compris le schéma, les données, les informations d’état de ligne et les versions de ligne.</span><span class="sxs-lookup"><span data-stu-id="15949-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="15949-106">Créer un **DataSet** qui contient le schéma de configuration existant **DataSet**, mais uniquement les lignes qui ont été modifiées.</span><span class="sxs-lookup"><span data-stu-id="15949-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="15949-107">Vous pouvez retourner toutes les lignes qui ont été modifiées, ou spécifier un spécifique **DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="15949-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="15949-108">Pour plus d’informations sur les États des lignes, consultez [États des lignes et des Versions de ligne](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="15949-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="15949-109">Copier le schéma, ou la structure relationnelle, de la **DataSet** uniquement, sans copie toutes les lignes.</span><span class="sxs-lookup"><span data-stu-id="15949-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="15949-110">Les lignes peuvent être importées dans un objet <xref:System.Data.DataTable> existant à l'aide de la méthode <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="15949-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="15949-111">Pour créer une copie exacte de la **DataSet** qui inclut le schéma et les données, utilisez le <xref:System.Data.DataSet.Copy%2A> méthode de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="15949-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="15949-112">L’exemple de code suivant montre comment créer une copie exacte de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="15949-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="15949-113">Pour créer une copie d’un **DataSet** qui inclut le schéma et seulement les données représentant **Added**, **Modified**, ou **Deleted** lignes, utilisez le <xref:System.Data.DataSet.GetChanges%2A> méthode de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="15949-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="15949-114">Vous pouvez également utiliser **GetChanges** pour retourner uniquement les lignes avec un état de ligne spécifié en passant une **DataRowState** valeur lors de l’appel **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="15949-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="15949-115">L’exemple de code suivant montre comment passer un **DataRowState** lors de l’appel **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="15949-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="15949-116">Pour créer une copie d’un **DataSet** qui inclut uniquement le schéma, utilisez le <xref:System.Data.DataSet.Clone%2A> méthode de la **jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="15949-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="15949-117">Vous pouvez également ajouter des lignes existantes à cloné **DataSet** à l’aide de la **ImportRow** méthode de la **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="15949-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="15949-118">**ImportRow** ajoute des données, l’état de ligne et les informations de version de ligne à la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="15949-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="15949-119">Les valeurs de colonne ne seront ajoutées que si le nom de colonne est identique et le type de données compatible.</span><span class="sxs-lookup"><span data-stu-id="15949-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="15949-120">L’exemple de code suivant crée un clone d’un **DataSet** , puis ajoute les lignes à partir de la version d’origine **DataSet** à la **clients** table dans le **jeu de données**  clone pour les clients où le **CountryRegion** colonne a la valeur « Germany ».</span><span class="sxs-lookup"><span data-stu-id="15949-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15949-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15949-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="15949-122">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="15949-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="15949-123">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="15949-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
