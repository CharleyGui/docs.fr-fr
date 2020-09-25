---
title: Création d'un DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 539e9763c8aa4affdb6f3bd219a99dbca50cee01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202341"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="440f6-102">Création d'un DataView</span><span class="sxs-lookup"><span data-stu-id="440f6-102">Creating a DataView</span></span>

<span data-ttu-id="440f6-103">Il existe deux façons de créer un objet <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="440f6-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="440f6-104">Vous pouvez utiliser le constructeur **DataView** , ou vous pouvez créer une référence à la <xref:System.Data.DataTable.DefaultView%2A> propriété de <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="440f6-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="440f6-105">Le constructeur **DataView** peut être vide, ou il peut accepter soit un **DataTable** comme argument unique, soit un **DataTable** avec des critères de filtre, des critères de tri et un filtre d’état de ligne.</span><span class="sxs-lookup"><span data-stu-id="440f6-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="440f6-106">Pour plus d’informations sur les arguments supplémentaires disponibles pour une utilisation avec le **DataView**, consultez [Tri et filtrage des données](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="440f6-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="440f6-107">Étant donné que l’index d’un **DataView** est construit à la fois lors de la création du **DataView** et lorsque l’une des propriétés **sort**, **RowFilter**ou **RowStateFilter** est modifiée, vous obtenez des performances optimales en fournissant des critères d’ordre de tri ou de filtrage initiaux comme arguments de constructeur lorsque vous créez le **DataView**.</span><span class="sxs-lookup"><span data-stu-id="440f6-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="440f6-108">La création d’un **DataView** sans spécifier de critère de tri ou de filtre et la définition ultérieure des propriétés **sort**, **RowFilter**ou **RowStateFilter** entraînent la génération ultérieure de l’index au moins deux fois : une fois lors de la création du **DataView** , et à nouveau lorsque l’une des propriétés de tri ou de filtre est modifiée.</span><span class="sxs-lookup"><span data-stu-id="440f6-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="440f6-109">Notez que si vous créez un **DataView** à l’aide du constructeur qui ne prend aucun argument, vous ne pourrez pas utiliser le **DataView** tant que vous n’aurez pas défini la propriété de **table** .</span><span class="sxs-lookup"><span data-stu-id="440f6-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="440f6-110">L’exemple de code suivant montre comment créer un **DataView** à l’aide du constructeur **DataView** .</span><span class="sxs-lookup"><span data-stu-id="440f6-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="440f6-111">Un **RowFilter**, une colonne de **Tri** et un **DataViewRowState** sont fournis avec le **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="440f6-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="440f6-112">L’exemple de code suivant montre comment obtenir une référence au **DataView** par défaut d’un **DataTable** à l’aide de la propriété **DefaultView** de la table.</span><span class="sxs-lookup"><span data-stu-id="440f6-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="440f6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="440f6-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="440f6-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="440f6-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="440f6-115">Tri et filtre de données</span><span class="sxs-lookup"><span data-stu-id="440f6-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="440f6-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="440f6-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="440f6-117">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="440f6-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
