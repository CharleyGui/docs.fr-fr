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
# <a name="query-typed-datasets"></a>Interroger des DataSets typés

Si le schéma du est <xref:System.Data.DataSet> connu au moment de la conception de l’application, nous vous recommandons d' <xref:System.Data.DataSet> utiliser un typé lors de l’utilisation de LINQ to DataSet. Un typé <xref:System.Data.DataSet> est une classe qui dérive <xref:System.Data.DataSet>de. De ce fait, il hérite de l'ensemble des méthodes, événements et propriétés d'un <xref:System.Data.DataSet>. En outre, un typé <xref:System.Data.DataSet> fournit des méthodes, des événements et des propriétés fortement typés. Cela signifie que vous pouvez accéder à des tables et à des colonnes par leur nom au lieu d’utiliser les méthodes associées à des collections. Cela rend les requêtes plus simples et plus lisibles. Pour plus d’informations, consultez [DataSets typés](./dataset-datatable-dataview/typed-datasets.md).

LINQ to DataSet prend également en charge l’interrogation <xref:System.Data.DataSet>d’un typé. Avec un typé <xref:System.Data.DataSet>, il n’est pas nécessaire d’utiliser la <xref:System.Data.DataRowExtensions.Field%2A> méthode ou <xref:System.Data.DataRowExtensions.SetField%2A> méthode générique pour accéder aux données de la colonne. Les noms de propriété sont disponibles au moment de la compilation, car les informations <xref:System.Data.DataSet>de type sont incluses dans le. LINQ to DataSet permet d’accéder aux valeurs de colonne comme type correct, afin que les erreurs d’incompatibilité de type soient interceptées lorsque le code est compilé au lieu de au moment de l’exécution.

Avant de pouvoir commencer à interroger un <xref:System.Data.DataSet>typé, vous devez générer la classe à l’aide du **Concepteur de DataSet** dans Visual Studio. Pour plus d’informations, consultez [créer et configurer des datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Exemples

L'exemple suivant montre une requête sur un <xref:System.Data.DataSet> typé :

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

## <a name="see-also"></a>Voir aussi

- [Interrogation de DataSets](querying-datasets-linq-to-dataset.md)
- [Requêtes de table croisée](cross-table-queries-linq-to-dataset.md)
- [Requêtes de table unique](single-table-queries-linq-to-dataset.md)
