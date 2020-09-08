---
title: Construction fonctionnelle-LINQ to XML
description: LINQ to XML fournit une construction fonctionnelle, qui vous permet de créer une arborescence XML dans une instruction unique.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: bcdc153d7f60cfb165dcb741d62b6af5c07a148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552504"
---
# <a name="functional-construction-linq-to-xml"></a><span data-ttu-id="890b1-103">Construction fonctionnelle (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="890b1-103">Functional construction (LINQ to XML)</span></span>

<span data-ttu-id="890b1-104">LINQ to XML offre un moyen puissant de créer des éléments XML appelés *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="890b1-104">LINQ to XML provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="890b1-105">La construction fonctionnelle vous permet de créer une arborescence XML dans une instruction unique.</span><span class="sxs-lookup"><span data-stu-id="890b1-105">Functional construction enables you to create an XML tree in a single statement.</span></span>

<span data-ttu-id="890b1-106">Plusieurs fonctionnalités clés de l’interface de programmation LINQ to XML sont utilisées dans la construction fonctionnelle :</span><span class="sxs-lookup"><span data-stu-id="890b1-106">Several key features of the LINQ to XML programming interface are used in functional construction:</span></span>

- <span data-ttu-id="890b1-107">Le constructeur <xref:System.Xml.Linq.XElement> prend différents types d'arguments comme contenu.</span><span class="sxs-lookup"><span data-stu-id="890b1-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="890b1-108">Par exemple, vous pouvez passer un autre objet <xref:System.Xml.Linq.XElement>, qui devient un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="890b1-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="890b1-109">Vous pouvez passer un objet <xref:System.Xml.Linq.XAttribute>, qui devient un attribut de l'élément.</span><span class="sxs-lookup"><span data-stu-id="890b1-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="890b1-110">Ou vous pouvez passer tout autre type d'objet, qui est converti en chaîne et devient le contenu texte de l'élément.</span><span class="sxs-lookup"><span data-stu-id="890b1-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>
- <span data-ttu-id="890b1-111">Le constructeur <xref:System.Xml.Linq.XElement> prend un tableau `params` de type <xref:System.Object>, de sorte que vous puissiez passer toute quantité d'objets au constructeur.</span><span class="sxs-lookup"><span data-stu-id="890b1-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="890b1-112">Cela vous permet de créer un élément dont le contenu est complexe.</span><span class="sxs-lookup"><span data-stu-id="890b1-112">This enables you to create an element that has complex content.</span></span>
- <span data-ttu-id="890b1-113">Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="890b1-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="890b1-114">Si la collection contient des objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément.</span><span class="sxs-lookup"><span data-stu-id="890b1-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="890b1-115">Cela est important car il vous permet de passer les résultats d’une requête LINQ au constructeur.</span><span class="sxs-lookup"><span data-stu-id="890b1-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>

## <a name="example-create-an-xml-tree"></a><span data-ttu-id="890b1-116">Exemple : création d’une arborescence XML</span><span class="sxs-lookup"><span data-stu-id="890b1-116">Example: Create an XML tree</span></span>

<span data-ttu-id="890b1-117">Vous pouvez utiliser la construction fonctionnelle pour écrire du code afin de créer une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="890b1-117">You can use functional construction to write code to create an XML tree.</span></span> <span data-ttu-id="890b1-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="890b1-118">The following is an example:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

## <a name="example-create-an-xml-tree-using-linq-query-results"></a><span data-ttu-id="890b1-119">Exemple : créer une arborescence XML à l’aide des résultats de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="890b1-119">Example: Create an XML tree using LINQ query results</span></span>

<span data-ttu-id="890b1-120">Ces fonctionnalités vous permettent également d’écrire du code qui utilise les résultats de requêtes LINQ lorsque vous créez une arborescence XML, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="890b1-120">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

<span data-ttu-id="890b1-121">Dans Visual Basic, la même chose est accomplie avec des littéraux XML :</span><span class="sxs-lookup"><span data-stu-id="890b1-121">In Visual Basic, the same thing is accomplished with XML literals:</span></span>

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where CInt(el) > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="890b1-122">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="890b1-122">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="890b1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="890b1-123">See also</span></span>

- [<span data-ttu-id="890b1-124">Créer des arborescences XML en C #</span><span class="sxs-lookup"><span data-stu-id="890b1-124">Create XML Trees in C#</span></span>](create-xml-trees.md)
- [<span data-ttu-id="890b1-125">Littéraux XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="890b1-125">XML literals in Visual Basic</span></span>](xml-literals.md)
