---
title: construction fonctionnelle (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635754"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="0724d-102">construction fonctionnelle (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0724d-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="0724d-103">offre un moyen puissant de créer des éléments XML appelé *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="0724d-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="0724d-104">La construction fonctionnelle est la capacité à créer une arborescence XML en une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="0724d-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="0724d-105">Plusieurs fonctionnalités clés de l'interface de programmation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] autorisent la construction fonctionnelle :</span><span class="sxs-lookup"><span data-stu-id="0724d-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="0724d-106">Le constructeur <xref:System.Xml.Linq.XElement> prend différents types d'arguments comme contenu.</span><span class="sxs-lookup"><span data-stu-id="0724d-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="0724d-107">Par exemple, vous pouvez passer un autre objet <xref:System.Xml.Linq.XElement>, qui devient un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="0724d-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="0724d-108">Vous pouvez passer un objet <xref:System.Xml.Linq.XAttribute>, qui devient un attribut de l'élément.</span><span class="sxs-lookup"><span data-stu-id="0724d-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="0724d-109">Ou vous pouvez passer tout autre type d'objet, qui est converti en chaîne et devient le contenu texte de l'élément.</span><span class="sxs-lookup"><span data-stu-id="0724d-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="0724d-110">Le constructeur <xref:System.Xml.Linq.XElement> prend un tableau `params` de type <xref:System.Object>, de sorte que vous puissiez passer toute quantité d'objets au constructeur.</span><span class="sxs-lookup"><span data-stu-id="0724d-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="0724d-111">Cela vous permet de créer un élément dont le contenu est complexe.</span><span class="sxs-lookup"><span data-stu-id="0724d-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="0724d-112">Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="0724d-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="0724d-113">Si la collection contient des objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément.</span><span class="sxs-lookup"><span data-stu-id="0724d-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="0724d-114">C’est important parce qu’il vous permet de transmettre les résultats d’une requête LINQ au constructeur.</span><span class="sxs-lookup"><span data-stu-id="0724d-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="0724d-115">Ces fonctionnalités vous permettent d’écrire du code pour créer une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="0724d-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="0724d-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0724d-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="0724d-117">Ces fonctionnalités vous permettent également d’écrire du code qui utilise les résultats des requêtes LINQ lorsque vous créez un arbre XML, comme suit :</span><span class="sxs-lookup"><span data-stu-id="0724d-117">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="0724d-118">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0724d-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  