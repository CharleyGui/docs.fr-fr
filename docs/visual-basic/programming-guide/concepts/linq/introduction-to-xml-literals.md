---
title: Introduction aux littérales XML dans Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 9f5c54574e51c537d9ea58d307afda10736d0d88
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266948"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="fd0c6-102">Introduction aux littéraux XML en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd0c6-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="fd0c6-103">Cette section fournit des informations sur la création d’arbres XML dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="fd0c6-104">Pour plus d’informations sur l’utilisation des résultats des requêtes LINQ comme contenu d’un arbre XML, voir [Construction fonctionnelle (LINQ à XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fd0c6-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="fd0c6-105">Pour plus d’informations sur les littérals XML dans Visual Basic, voir [Aperçu de LINQ à XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fd0c6-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="fd0c6-106">Création d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="fd0c6-106">Creating XML Trees</span></span>  
 <span data-ttu-id="fd0c6-107">L'exemple suivant montre comment créer un objet <xref:System.Xml.Linq.XElement>, dans le cas présent `contacts` :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="fd0c6-108">Création d'un XElement avec du contenu simple</span><span class="sxs-lookup"><span data-stu-id="fd0c6-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="fd0c6-109">Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> qui contient du contenu simple, comme suit :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 <span data-ttu-id="fd0c6-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="fd0c6-111">Création d'un élément vide</span><span class="sxs-lookup"><span data-stu-id="fd0c6-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="fd0c6-112">Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> vide comme suit :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="fd0c6-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="fd0c6-114">Utilisation d'expressions incorporées</span><span class="sxs-lookup"><span data-stu-id="fd0c6-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="fd0c6-115">L’une des fonctionnalités importantes des littéraux XML est qu’ils autorisent la présence d’expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="fd0c6-116">Les expressions incorporées vous permettent d’évaluer une expression et d’insérer les résultats de l’expression dans l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="fd0c6-117">Si l'expression est évaluée à un type de <xref:System.Xml.Linq.XElement>, un élément est inséré dans l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="fd0c6-118">Si l’expression est évaluée à un type de <xref:System.Xml.Linq.XAttribute>, un attribut est inséré dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="fd0c6-119">Vous pouvez insérer des éléments et des attributs dans l'arborescence uniquement où ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="fd0c6-120">Il est important de noter que seule une expression unique peut aller dans une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="fd0c6-121">Vous ne pouvez pas incorporer plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="fd0c6-122">Si une expression s'étend au-delà d'une seule ligne, vous devez utiliser le caractère de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="fd0c6-123">Si vous utilisez une expression incorporée pour ajouter des nœuds (y compris des éléments) et des attributs existants à une nouvelle arborescence XML et si les nœuds existants sont déjà apparentés, les nœuds sont clonés.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="fd0c6-124">Les nœuds nouvellement clonés sont attachés à la nouvelle arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="fd0c6-125">Si les nœuds existants ne sont pas apparentés, ils sont simplement attachés à la nouvelle arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="fd0c6-126">Ceci est illustré dans le dernier exemple de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="fd0c6-127">L’exemple suivant utilise une expression incorporée pour insérer un élément dans l’arborescence :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 <span data-ttu-id="fd0c6-128">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="fd0c6-129">Utilisation d'expressions incorporées pour le contenu</span><span class="sxs-lookup"><span data-stu-id="fd0c6-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="fd0c6-130">Vous pouvez utiliser une expression incorporée pour fournir le contenu d'un élément :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="fd0c6-131">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="fd0c6-132">Utilisation d'une requête LINQ dans une expression incorporée</span><span class="sxs-lookup"><span data-stu-id="fd0c6-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="fd0c6-133">Vous pouvez utiliser les résultats d'une requête LINQ pour le contenu d'un élément :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="fd0c6-134">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="fd0c6-135">Utilisation d'expressions incorporées pour des noms de nœuds</span><span class="sxs-lookup"><span data-stu-id="fd0c6-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="fd0c6-136">Vous pouvez également utiliser des expressions incorporées pour calculer des noms d'attributs, des valeurs d'attributs, des noms d'éléments et des valeurs d'éléments :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="fd0c6-137">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="fd0c6-138">Clonage et attachement</span><span class="sxs-lookup"><span data-stu-id="fd0c6-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="fd0c6-139">Comme mentionné précédemment, si vous utilisez une expression incorporée pour ajouter des nœuds (y compris des éléments) et des attributs existants à une nouvelle arborescence XML et que les nœuds existants sont déjà apparentés, les nœuds sont clonés et les nœuds nouvellement clonés sont attachés à la nouvelle arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="fd0c6-140">Si les nœuds existants ne sont pas apparentés, ils sont simplement attachés à la nouvelle arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="fd0c6-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="fd0c6-141">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fd0c6-141">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd0c6-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd0c6-142">See also</span></span>

- [<span data-ttu-id="fd0c6-143">Création d’arbres XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd0c6-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
