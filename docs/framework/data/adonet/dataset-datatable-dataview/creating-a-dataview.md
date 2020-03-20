---
title: Création d'un DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151336"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="4d0e1-102">Création d'un DataView</span><span class="sxs-lookup"><span data-stu-id="4d0e1-102">Creating a DataView</span></span>
<span data-ttu-id="4d0e1-103">Il existe deux façons de créer un objet <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="4d0e1-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="4d0e1-104">Vous pouvez utiliser le constructeur **DataView,** ou vous <xref:System.Data.DataTable.DefaultView%2A> pouvez <xref:System.Data.DataTable>créer une référence à la propriété de la .</span><span class="sxs-lookup"><span data-stu-id="4d0e1-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="4d0e1-105">Le constructeur **DataView** peut être vide, soit il peut prendre soit un **DataTable** comme un seul argument, ou un **DataTable** avec des critères de filtre, des critères de tri, et un filtre d’état de ligne.</span><span class="sxs-lookup"><span data-stu-id="4d0e1-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="4d0e1-106">Pour plus d’informations sur les arguments supplémentaires disponibles pour une utilisation avec le **DataView**, voir [Les données de tri et de filtrage](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="4d0e1-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="4d0e1-107">Parce que l’index d’un **DataView** est construit à la fois lorsque le **DataView** est créé, et lorsque l’une des propriétés **Sort**, **RowFilter**, ou **RowStateFilter** sont modifiées, vous obtenez les meilleures performances en fournissant n’importe quel ordre de tri initial ou des critères de filtrage comme arguments constructeurs lorsque vous créez le **DataView**.</span><span class="sxs-lookup"><span data-stu-id="4d0e1-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="4d0e1-108">La création **d’un DataView** sans spécifier les critères de tri ou de filtre, puis la définition des propriétés **Sort,** **RowFilter**, ou **RowStateFilter** provoque plus tard l’index à être construit au moins deux fois: une fois lorsque le **DataView** est créé, et encore une fois lorsque l’une des propriétés de type ou de filtre sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="4d0e1-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="4d0e1-109">Notez que si vous créez un **DataView** à l’aide du constructeur qui ne prend aucun argument, vous ne serez pas en mesure d’utiliser le **DataView** jusqu’à ce que vous avez défini la propriété **Table.**</span><span class="sxs-lookup"><span data-stu-id="4d0e1-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="4d0e1-110">L’exemple de code suivant montre comment créer un **DataView** à l’aide du constructeur **DataView.**</span><span class="sxs-lookup"><span data-stu-id="4d0e1-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="4d0e1-111">A **RowFilter**, **Sort** column, et **DataViewRowState** sont fournis avec le **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="4d0e1-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],
    "Country = 'USA'",
    "ContactName",
    DataViewRowState.CurrentRows);  
```  
  
 <span data-ttu-id="4d0e1-112">L’exemple de code suivant montre comment obtenir une référence à la **DataView** par défaut d’un **DataTable** utilisant la propriété **DefaultView** de la table.</span><span class="sxs-lookup"><span data-stu-id="4d0e1-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d0e1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d0e1-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="4d0e1-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="4d0e1-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="4d0e1-115">Tri et filtre de données</span><span class="sxs-lookup"><span data-stu-id="4d0e1-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="4d0e1-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="4d0e1-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="4d0e1-117">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4d0e1-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
