---
title: 'Procédure : Projeter un nouveau type (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: bec4e7c7d87dffb90b49b76aa00a5de093d68436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593045"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="cfa64-102">Procédure : Projeter un nouveau type (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cfa64-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="cfa64-103">Les autres exemples de cette section ont illustré des requêtes qui retournent des résultats comme <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string` et <xref:System.Collections.Generic.IEnumerable%601> de `int`.</span><span class="sxs-lookup"><span data-stu-id="cfa64-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="cfa64-104">Il s'agit de types de résultats courants, mais ils ne conviennent pas à chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="cfa64-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="cfa64-105">Dans de nombreux cas, vous souhaiterez que vos requêtes retournent un objet <xref:System.Collections.Generic.IEnumerable%601> d'un autre type.</span><span class="sxs-lookup"><span data-stu-id="cfa64-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="cfa64-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="cfa64-106">Example</span></span>

<span data-ttu-id="cfa64-107">Cet exemple montre comment instancier des objets dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="cfa64-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="cfa64-108">Le code définit tout d'abord une nouvelle classe avec un constructeur, puis modifie l'instruction `select` de sorte que l'expression soit une nouvelle instance de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="cfa64-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="cfa64-109">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Commande fournisseur standard (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="cfa64-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

```csharp
class NameQty 
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q; 
    }
};

class Program {
    public static void Main() 
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

<span data-ttu-id="cfa64-110">Cet exemple utilise la méthode <xref:System.Xml.Linq.XContainer.Element%2A> introduite dans la rubrique [Guide pratique pour récupérer un seul élément enfant (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cfa64-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="cfa64-111">Il utilise également des casts pour récupérer les valeurs des éléments retournés par la méthode <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="cfa64-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="cfa64-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cfa64-112">This example produces the following output:</span></span>

```console
Lawnmower:1
Baby Monitor:2
```
