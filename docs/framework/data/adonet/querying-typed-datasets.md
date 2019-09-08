---
title: Interrogation de DataSets typés
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782969"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="cc74a-102">Interroger des DataSets typés</span><span class="sxs-lookup"><span data-stu-id="cc74a-102">Query typed DataSets</span></span>

<span data-ttu-id="cc74a-103">Si le schéma du est <xref:System.Data.DataSet> connu au moment de la conception de l’application, nous vous recommandons d' <xref:System.Data.DataSet> utiliser un typé lors de l’utilisation de LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="cc74a-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="cc74a-104">Un typé <xref:System.Data.DataSet> est une classe qui dérive <xref:System.Data.DataSet>de.</span><span class="sxs-lookup"><span data-stu-id="cc74a-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cc74a-105">De ce fait, il hérite de l'ensemble des méthodes, événements et propriétés d'un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="cc74a-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cc74a-106">En outre, un typé <xref:System.Data.DataSet> fournit des méthodes, des événements et des propriétés fortement typés.</span><span class="sxs-lookup"><span data-stu-id="cc74a-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="cc74a-107">Cela signifie que vous pouvez accéder à des tables et à des colonnes par leur nom au lieu d’utiliser les méthodes associées à des collections.</span><span class="sxs-lookup"><span data-stu-id="cc74a-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="cc74a-108">Cela rend les requêtes plus simples et plus lisibles.</span><span class="sxs-lookup"><span data-stu-id="cc74a-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="cc74a-109">Pour plus d’informations, consultez [DataSets typés](./dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="cc74a-109">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="cc74a-110">LINQ to DataSet prend également en charge l’interrogation <xref:System.Data.DataSet>d’un typé.</span><span class="sxs-lookup"><span data-stu-id="cc74a-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cc74a-111">Avec un typé <xref:System.Data.DataSet>, il n’est pas nécessaire d’utiliser la <xref:System.Data.DataRowExtensions.Field%2A> méthode ou <xref:System.Data.DataRowExtensions.SetField%2A> méthode générique pour accéder aux données de la colonne.</span><span class="sxs-lookup"><span data-stu-id="cc74a-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="cc74a-112">Les noms de propriété sont disponibles au moment de la compilation, car les informations <xref:System.Data.DataSet>de type sont incluses dans le.</span><span class="sxs-lookup"><span data-stu-id="cc74a-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cc74a-113">LINQ to DataSet permet d’accéder aux valeurs de colonne comme type correct, afin que les erreurs d’incompatibilité de type soient interceptées lorsque le code est compilé au lieu de au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cc74a-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="cc74a-114">Avant de pouvoir commencer à interroger un <xref:System.Data.DataSet>typé, vous devez générer la classe à l’aide du **Concepteur de DataSet** dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cc74a-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="cc74a-115">Pour plus d’informations, consultez [créer et configurer des datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cc74a-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="cc74a-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="cc74a-116">Example</span></span>

<span data-ttu-id="cc74a-117">L'exemple suivant montre une requête sur un <xref:System.Data.DataSet> typé :</span><span class="sxs-lookup"><span data-stu-id="cc74a-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a><span data-ttu-id="cc74a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc74a-118">See also</span></span>

- [<span data-ttu-id="cc74a-119">Interrogation de DataSets</span><span class="sxs-lookup"><span data-stu-id="cc74a-119">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="cc74a-120">Requêtes de table croisée</span><span class="sxs-lookup"><span data-stu-id="cc74a-120">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="cc74a-121">Requêtes de table unique</span><span class="sxs-lookup"><span data-stu-id="cc74a-121">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
