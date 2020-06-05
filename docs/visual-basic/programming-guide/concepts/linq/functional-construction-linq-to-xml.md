---
title: Construction fonctionnelle (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f42cd6f31134c5f4c7d6a75f38997b2be0c317f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398062"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="7014b-102">Construction fonctionnelle (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7014b-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="7014b-103">offre un moyen puissant de créer des éléments XML appelé *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="7014b-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="7014b-104">La construction fonctionnelle est la capacité à créer une arborescence XML en une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="7014b-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="7014b-105">Plusieurs fonctionnalités clés de l'interface de programmation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] autorisent la construction fonctionnelle :</span><span class="sxs-lookup"><span data-stu-id="7014b-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="7014b-106">Le constructeur <xref:System.Xml.Linq.XElement> prend différents types d'arguments comme contenu.</span><span class="sxs-lookup"><span data-stu-id="7014b-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="7014b-107">Par exemple, vous pouvez passer un autre objet <xref:System.Xml.Linq.XElement>, qui devient un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="7014b-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="7014b-108">Vous pouvez passer un objet <xref:System.Xml.Linq.XAttribute>, qui devient un attribut de l'élément.</span><span class="sxs-lookup"><span data-stu-id="7014b-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="7014b-109">Ou vous pouvez passer tout autre type d'objet, qui est converti en chaîne et devient le contenu texte de l'élément.</span><span class="sxs-lookup"><span data-stu-id="7014b-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="7014b-110">Le constructeur <xref:System.Xml.Linq.XElement> prend un tableau `params` de type <xref:System.Object>, de sorte que vous puissiez passer toute quantité d'objets au constructeur.</span><span class="sxs-lookup"><span data-stu-id="7014b-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="7014b-111">Cela vous permet de créer un élément dont le contenu est complexe.</span><span class="sxs-lookup"><span data-stu-id="7014b-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="7014b-112">Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="7014b-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="7014b-113">Si la collection contient des objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément.</span><span class="sxs-lookup"><span data-stu-id="7014b-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="7014b-114">Cela est important car il vous permet de passer les résultats d’une requête LINQ au constructeur.</span><span class="sxs-lookup"><span data-stu-id="7014b-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="7014b-115">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="7014b-115">The following is an example:</span></span>  
  
 <span data-ttu-id="7014b-116">Ces fonctionnalités vous permettent d’écrire du code à l’aide de littéraux XML pour créer une arborescence XML, ainsi que d’écrire du code qui utilise les résultats de requêtes LINQ lorsque vous créez une arborescence XML :</span><span class="sxs-lookup"><span data-stu-id="7014b-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of LINQ queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="7014b-117">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="7014b-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7014b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7014b-118">See also</span></span>

- [<span data-ttu-id="7014b-119">Création d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7014b-119">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
