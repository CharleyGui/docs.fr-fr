---
title: Comment projeter un nouveau type (LINQ to XML) (C#)
description: Apprenez à créer des requêtes en LINQ to XML en C# qui retournent IEnumerable <T> de types, en plus de XElement, String ou int, qui sont décrits dans d’autres exemples.
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104649"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="04e3c-103">Comment projeter un nouveau type (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="04e3c-103">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="04e3c-104">Les autres exemples de cette section ont illustré des requêtes qui retournent des résultats comme <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string` et <xref:System.Collections.Generic.IEnumerable%601> de `int`.</span><span class="sxs-lookup"><span data-stu-id="04e3c-104">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="04e3c-105">Il s'agit de types de résultats courants, mais ils ne conviennent pas à chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="04e3c-105">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="04e3c-106">Dans de nombreux cas, vous souhaiterez que vos requêtes retournent un objet <xref:System.Collections.Generic.IEnumerable%601> d'un autre type.</span><span class="sxs-lookup"><span data-stu-id="04e3c-106">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="04e3c-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="04e3c-107">Example</span></span>

<span data-ttu-id="04e3c-108">Cet exemple montre comment instancier des objets dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="04e3c-108">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="04e3c-109">Le code définit tout d'abord une nouvelle classe avec un constructeur, puis modifie l'instruction `select` de sorte que l'expression soit une nouvelle instance de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="04e3c-109">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="04e3c-110">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="04e3c-110">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="04e3c-111">Cet exemple utilise la <xref:System.Xml.Linq.XContainer.Element%2A> méthode introduite dans la rubrique [Comment récupérer un seul élément enfant (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="04e3c-111">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="04e3c-112">Il utilise également des casts pour récupérer les valeurs des éléments retournés par la méthode <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="04e3c-112">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="04e3c-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="04e3c-113">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
