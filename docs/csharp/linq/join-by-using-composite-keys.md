---
title: Effectuer des opérations de jointure à l'aide de clés composites (LINQ en C#)
description: Découvrez comment effectuer des opérations de jointure à l'aide de clés composites dans LINQ.
ms.date: 12/01/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: 460a52da7e0c0a47b77d4c64e76641bae9da7cd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659876"
---
# <a name="join-by-using-composite-keys"></a>Effectuer des jointures à l’aide de clés composites

Cet exemple montre comment effectuer des opérations de jointure où vous voulez utiliser plusieurs clés pour définir une correspondance. Ceci s’effectue à l’aide d’une clé composite. Vous créez une clé composite en tant que type anonyme ou typé nommé avec les valeurs que vous voulez comparer. Si la variable de requête doit être passée au-delà des limites de la méthode, utilisez un type nommé qui substitue <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> pour la clé. Les noms des propriétés et l’ordre dans lequel elles se trouvent doivent être identiques dans chaque clé.

## <a name="example"></a> Exemple

L’exemple suivant montre comment utiliser une clé composite pour joindre les données de trois tables :

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

L’inférence du type sur les clés composites dépend des noms des propriétés dans les clés et l’ordre dans lequel elles apparaissent. Si les propriétés dans les séquences sources n’ont pas les mêmes noms, vous devez affecter de nouveaux noms dans les clés. Par exemple, si la table `Orders` et la table `OrderDetails` utilisent chacune des noms différents pour leurs colonnes, vous pouvez créer des clés composites en affectant des noms identiques dans les types anonymes :

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

Vous pouvez aussi utiliser des clés composites dans une clause `group`.

## <a name="see-also"></a>Voir aussi

- [Requête intégrée linguistique (LINQ)](index.md)
- [clause d’adhésion](../language-reference/keywords/join-clause.md)
- [group, clause](../language-reference/keywords/group-clause.md)
