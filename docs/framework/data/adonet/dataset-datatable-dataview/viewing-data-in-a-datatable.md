---
title: Affichage des données dans un DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: ea92b8a5e46bdaa8e94756cd28a3fbcb2789d7b3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204391"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="5be61-102">Affichage des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="5be61-102">Viewing Data in a DataTable</span></span>

<span data-ttu-id="5be61-103">Vous pouvez accéder au contenu d’un <xref:System.Data.DataTable> objet à l’aide des collections **Rows** et **Columns** du **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="5be61-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="5be61-104">Vous pouvez également utiliser la <xref:System.Data.DataTable.Select%2A> méthode pour retourner des sous-ensembles de données dans un **DataTable** en fonction de critères, notamment des critères de recherche, un ordre de tri et un état de ligne.</span><span class="sxs-lookup"><span data-stu-id="5be61-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="5be61-105">En outre, vous pouvez utiliser la <xref:System.Data.DataRowCollection.Find%2A> méthode du **DataRowCollection** lors de la recherche d’une ligne particulière à l’aide d’une valeur de clé primaire.</span><span class="sxs-lookup"><span data-stu-id="5be61-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>

<span data-ttu-id="5be61-106">La méthode **Select** de l’objet **DataTable** retourne un ensemble d' <xref:System.Data.DataRow> objets qui correspondent aux critères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="5be61-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="5be61-107">**Select** accepte des arguments facultatifs d’une expression de filtre, d’une expression de tri et d’un **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="5be61-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="5be61-108">L’expression de filtre identifie les lignes à retourner en fonction des valeurs **DataColumn** , `LastName = 'Smith'`telles que.</span><span class="sxs-lookup"><span data-stu-id="5be61-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="5be61-109">L'expression de tri respecte les conventions SQL standard de tri des colonnes, comme `LastName ASC, FirstName ASC`.</span><span class="sxs-lookup"><span data-stu-id="5be61-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="5be61-110">Pour plus d’informations sur les règles d' <xref:System.Data.DataColumn.Expression%2A> écriture d’expressions, consultez la propriété de la classe **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="5be61-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>

> [!TIP]
> <span data-ttu-id="5be61-111">Si vous effectuez un certain nombre d’appels à la méthode **Select** d’un **DataTable**, vous pouvez augmenter les performances en créant d' <xref:System.Data.DataView> abord un pour le **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="5be61-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="5be61-112">La création du **DataView** indexe les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="5be61-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="5be61-113">La méthode **Select** utilise ensuite cet index, ce qui réduit considérablement le temps nécessaire pour générer le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="5be61-113">The **Select** method then uses that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="5be61-114">Pour plus d’informations sur la création d’un **DataView** pour un **DataTable**, consultez [DataView](dataviews.md).</span><span class="sxs-lookup"><span data-stu-id="5be61-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](dataviews.md).</span></span>

<span data-ttu-id="5be61-115">La méthode **Select** détermine la version des lignes à afficher ou à manipuler en fonction d' <xref:System.Data.DataViewRowState>un.</span><span class="sxs-lookup"><span data-stu-id="5be61-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="5be61-116">Le tableau suivant décrit les valeurs possibles de l’énumération **DataViewRowState** .</span><span class="sxs-lookup"><span data-stu-id="5be61-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>

|<span data-ttu-id="5be61-117">Valeur DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="5be61-117">DataViewRowState value</span></span>|<span data-ttu-id="5be61-118">Description</span><span class="sxs-lookup"><span data-stu-id="5be61-118">Description</span></span>|
|----------------------------|-----------------|
|<span data-ttu-id="5be61-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="5be61-119">**CurrentRows**</span></span>|<span data-ttu-id="5be61-120">Les lignes en cours comprennent les lignes non modifiées, les lignes ajoutées et les lignes modifiées.</span><span class="sxs-lookup"><span data-stu-id="5be61-120">Current rows including unchanged, added, and modified rows.</span></span>|
|<span data-ttu-id="5be61-121">**Supprimé**</span><span class="sxs-lookup"><span data-stu-id="5be61-121">**Deleted**</span></span>|<span data-ttu-id="5be61-122">Ligne supprimée.</span><span class="sxs-lookup"><span data-stu-id="5be61-122">A deleted row.</span></span>|
|<span data-ttu-id="5be61-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="5be61-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="5be61-124">Une version actuelle, qui est une version modifiée des données d'origine.</span><span class="sxs-lookup"><span data-stu-id="5be61-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="5be61-125">(Voir **ModifiedOriginal**.)</span><span class="sxs-lookup"><span data-stu-id="5be61-125">(See **ModifiedOriginal**.)</span></span>|
|<span data-ttu-id="5be61-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="5be61-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="5be61-127">La version d'origine de toutes les lignes modifiées.</span><span class="sxs-lookup"><span data-stu-id="5be61-127">The original version of all modified rows.</span></span> <span data-ttu-id="5be61-128">La version actuelle est disponible à l’aide de **ModifiedCurrent**.</span><span class="sxs-lookup"><span data-stu-id="5be61-128">The current version is available using **ModifiedCurrent**.</span></span>|
|<span data-ttu-id="5be61-129">**Ajoute**</span><span class="sxs-lookup"><span data-stu-id="5be61-129">**Added**</span></span>|<span data-ttu-id="5be61-130">Nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="5be61-130">A new row.</span></span>|
|<span data-ttu-id="5be61-131">**Aucun**</span><span class="sxs-lookup"><span data-stu-id="5be61-131">**None**</span></span>|<span data-ttu-id="5be61-132">Aucune.</span><span class="sxs-lookup"><span data-stu-id="5be61-132">None.</span></span>|
|<span data-ttu-id="5be61-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="5be61-133">**OriginalRows**</span></span>|<span data-ttu-id="5be61-134">Les lignes d'origine, notamment les lignes non modifiées et les lignes supprimées.</span><span class="sxs-lookup"><span data-stu-id="5be61-134">Original rows, including unchanged and deleted rows.</span></span>|
|<span data-ttu-id="5be61-135">**Inchangé**</span><span class="sxs-lookup"><span data-stu-id="5be61-135">**Unchanged**</span></span>|<span data-ttu-id="5be61-136">Ligne non modifiée.</span><span class="sxs-lookup"><span data-stu-id="5be61-136">An unchanged row.</span></span>|

<span data-ttu-id="5be61-137">Dans l’exemple suivant, l’objet **DataSet** est filtré afin que vous n’utilisiez que des lignes dont **DataViewRowState** a la valeur **CurrentRows**.</span><span class="sxs-lookup"><span data-stu-id="5be61-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>

```vb
Dim column As DataColumn
Dim row As DataRow

Dim currentRows() As DataRow = _
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)

If (currentRows.Length < 1 ) Then
  Console.WriteLine("No Current Rows Found")
Else
  For Each column in workTable.Columns
    Console.Write(vbTab & column.ColumnName)
  Next

  Console.WriteLine(vbTab & "RowState")

  For Each row In currentRows
    For Each column In workTable.Columns
      Console.Write(vbTab & row(column).ToString())
    Next

    Dim rowState As String = _
        System.Enum.GetName(row.RowState.GetType(), row.RowState)
    Console.WriteLine(vbTab & rowState)
  Next
End If
```

```csharp
DataRow[] currentRows = workTable.Select(
    null, null, DataViewRowState.CurrentRows);

if (currentRows.Length < 1 )
  Console.WriteLine("No Current Rows Found");
else
{
  foreach (DataColumn column in workTable.Columns)
    Console.Write("\t{0}", column.ColumnName);

  Console.WriteLine("\tRowState");

  foreach (DataRow row in currentRows)
  {
    foreach (DataColumn column in workTable.Columns)
      Console.Write("\t{0}", row[column]);

    Console.WriteLine("\t" + row.RowState);
  }
}
```

<span data-ttu-id="5be61-138">La méthode **Select** peut être utilisée pour retourner des lignes avec des valeurs **RowState** ou Field différentes.</span><span class="sxs-lookup"><span data-stu-id="5be61-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="5be61-139">L’exemple suivant retourne un tableau **DataRow** qui référence toutes les lignes qui ont été supprimées, et retourne un autre tableau **DataRow** qui référence toutes les lignes, classées par **CustLName**, où la colonne **CustID** est supérieure à 5.</span><span class="sxs-lookup"><span data-stu-id="5be61-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="5be61-140">Pour plus d’informations sur l’affichage des informations dans la ligne supprimée, consultez [États des lignes et versions de ligne](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="5be61-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>

```vb
' Retrieve all deleted rows.
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)

' Retrieve rows where CustID > 5, and order by CustLName.
Dim custRows() As DataRow = workTable.Select( _
    "CustID > 5", "CustLName ASC")
```

```csharp
// Retrieve all deleted rows.
DataRow[] deletedRows = workTable.Select(
    null, null, DataViewRowState.Deleted);

// Retrieve rows where CustID > 5, and order by CustLName.
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");
```

## <a name="see-also"></a><span data-ttu-id="5be61-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5be61-141">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [<span data-ttu-id="5be61-142">Manipulation des données dans un DataTable</span><span class="sxs-lookup"><span data-stu-id="5be61-142">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="5be61-143">États des lignes et versions des lignes</span><span class="sxs-lookup"><span data-stu-id="5be61-143">Row States and Row Versions</span></span>](row-states-and-row-versions.md)
- [<span data-ttu-id="5be61-144">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="5be61-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
