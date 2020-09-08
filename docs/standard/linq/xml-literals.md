---
title: Littéraux XML dans Visual Basic LINQ to XML
description: Vous pouvez créer une arborescence XML dans Visual Basic à l’aide de littéraux XML et d’expressions incorporées. Les expressions incorporées vous permettent d’évaluer une expression et d’insérer les résultats de l’expression dans l’arborescence XML.
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553207"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a><span data-ttu-id="1e36c-104">Littéraux XML dans Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1e36c-104">XML Literals in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="1e36c-105">Cet article fournit des informations sur la création d’arborescences XML dans Visual Basic à l’aide de littéraux XML et d’expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="1e36c-105">This article provides information about creating XML trees in Visual Basic using XML literals and embedded expressions.</span></span>

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a><span data-ttu-id="1e36c-106">Exemple : utilisation de littéraux XML pour créer une arborescence XML</span><span class="sxs-lookup"><span data-stu-id="1e36c-106">Example: Use XML literals to create an XML tree</span></span>

<span data-ttu-id="1e36c-107">L’exemple suivant montre comment créer un <xref:System.Xml.Linq.XElement> , dans ce cas `contacts` , avec des littéraux XML :</span><span class="sxs-lookup"><span data-stu-id="1e36c-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`, with XML literals:</span></span>

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

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a><span data-ttu-id="1e36c-108">Exemple : utilisation de littéraux XML pour créer un XElement avec un contenu simple</span><span class="sxs-lookup"><span data-stu-id="1e36c-108">Example: Use XML literals to create an XElement with simple content</span></span>

<span data-ttu-id="1e36c-109">Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> qui contient du contenu simple, comme suit :</span><span class="sxs-lookup"><span data-stu-id="1e36c-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

<span data-ttu-id="1e36c-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1e36c-110">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a><span data-ttu-id="1e36c-111">Exemple : utiliser un littéral XML pour créer un élément vide</span><span class="sxs-lookup"><span data-stu-id="1e36c-111">Example: Use an XML literal to create an empty element</span></span>

<span data-ttu-id="1e36c-112">Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> vide comme suit :</span><span class="sxs-lookup"><span data-stu-id="1e36c-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

<span data-ttu-id="1e36c-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1e36c-113">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a><span data-ttu-id="1e36c-114">Utiliser des expressions incorporées pour créer du contenu</span><span class="sxs-lookup"><span data-stu-id="1e36c-114">Use embedded expressions to create content</span></span>

<span data-ttu-id="1e36c-115">L’une des fonctionnalités importantes des littéraux XML est qu’ils autorisent la présence d’expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="1e36c-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="1e36c-116">Les expressions incorporées vous permettent d’évaluer une expression et d’insérer les résultats de l’expression dans l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="1e36c-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="1e36c-117">Si l'expression est évaluée à un type de <xref:System.Xml.Linq.XElement>, un élément est inséré dans l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="1e36c-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="1e36c-118">Si l’expression est évaluée à un type de <xref:System.Xml.Linq.XAttribute>, un attribut est inséré dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="1e36c-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="1e36c-119">Vous pouvez insérer des éléments et des attributs dans l’arborescence uniquement là où ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="1e36c-119">You can insert elements and attributes into the tree only where they're valid.</span></span>

<span data-ttu-id="1e36c-120">Il est important de noter qu’une seule expression peut être insérée dans une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="1e36c-120">it's important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="1e36c-121">Vous ne pouvez pas incorporer plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="1e36c-121">You can't embed multiple statements.</span></span> <span data-ttu-id="1e36c-122">Si une expression s'étend au-delà d'une seule ligne, vous devez utiliser le caractère de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="1e36c-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>

<span data-ttu-id="1e36c-123">Si vous utilisez une expression incorporée pour ajouter des nœuds (y compris des éléments) et des attributs existants à une nouvelle arborescence XML et si les nœuds existants sont déjà apparentés, les nœuds sont clonés.</span><span class="sxs-lookup"><span data-stu-id="1e36c-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="1e36c-124">Les nœuds nouvellement clonés sont attachés à la nouvelle arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="1e36c-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="1e36c-125">Si les nœuds existants ne sont pas apparentés, les nœuds sont simplement attachés à la nouvelle arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="1e36c-125">If the existing nodes aren't parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="1e36c-126">Le dernier exemple de cet article illustre cela.</span><span class="sxs-lookup"><span data-stu-id="1e36c-126">The last example in this article demonstrates this.</span></span>

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a><span data-ttu-id="1e36c-127">Exemple : utilisation d’une expression incorporée pour insérer un élément</span><span class="sxs-lookup"><span data-stu-id="1e36c-127">Example: Use an embedded expression to insert an element</span></span>

<span data-ttu-id="1e36c-128">L’exemple suivant utilise une expression incorporée pour insérer un élément dans l’arborescence :</span><span class="sxs-lookup"><span data-stu-id="1e36c-128">The following example uses an embedded expression to insert an element into the tree:</span></span>

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

<span data-ttu-id="1e36c-129">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1e36c-129">This example produces the following output:</span></span>

```xml
<Root>
  <Child>Contents</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-for-content"></a><span data-ttu-id="1e36c-130">Exemple : utilisation d’une expression incorporée pour le contenu</span><span class="sxs-lookup"><span data-stu-id="1e36c-130">Example: Use an embedded expression for content</span></span>

<span data-ttu-id="1e36c-131">Vous pouvez utiliser une expression incorporée pour fournir le contenu d'un élément :</span><span class="sxs-lookup"><span data-stu-id="1e36c-131">You can use an embedded expression to supply the content of an element:</span></span>

```vb
Dim str As String
str = "Some content"
Dim root As XElement = <Root><%= str %></Root>
Console.WriteLine(root)
```

<span data-ttu-id="1e36c-132">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1e36c-132">This example produces the following output:</span></span>

```xml
<Root>Some content</Root>
```

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="1e36c-133">Exemple : utilisation d’une requête LINQ dans une expression incorporée</span><span class="sxs-lookup"><span data-stu-id="1e36c-133">Example: Use a LINQ query in an embedded expression</span></span>

<span data-ttu-id="1e36c-134">Vous pouvez utiliser les résultats d’une requête LINQ pour fournir le contenu d’un élément :</span><span class="sxs-lookup"><span data-stu-id="1e36c-134">You can use the results of a LINQ query to provide the content of an element:</span></span>

```vb
Dim arr As Integer() = {1, 2, 3}

Dim n As XElement = _
    <Root>
        <%= From i In arr Select <Child><%= i %></Child> %>
    </Root>

Console.WriteLine(n)
```

<span data-ttu-id="1e36c-135">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1e36c-135">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Child>3</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a><span data-ttu-id="1e36c-136">Exemple : utilisation d’une expression incorporée pour fournir des noms de nœud</span><span class="sxs-lookup"><span data-stu-id="1e36c-136">Example: Use an embedded expression to provide node names</span></span>

<span data-ttu-id="1e36c-137">Vous pouvez également utiliser une expression incorporée pour calculer les noms d’attribut, les valeurs d’attribut, les noms d’éléments et les valeurs d’élément :</span><span class="sxs-lookup"><span data-stu-id="1e36c-137">You can also use an embedded expression to calculate attribute names, attribute values, element names, and element values:</span></span>

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

<span data-ttu-id="1e36c-138">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1e36c-138">This example produces the following output:</span></span>

```xml
<Root att="aValue">
  <ele>eValue</ele>
</Root>
```

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a><span data-ttu-id="1e36c-139">Exemple : utilisation d’une expression incorporée pour cloner et attacher des nœuds</span><span class="sxs-lookup"><span data-stu-id="1e36c-139">Example: Use an embedded expression to clone and attach nodes</span></span>

<span data-ttu-id="1e36c-140">Comme mentionné précédemment, si vous utilisez une expression incorporée pour ajouter des nœuds existants (y compris des éléments) et des attributs à une nouvelle arborescence XML, et si les nœuds ajoutés sont déjà apparentés, les nœuds sont clonés et les clones sont attachés à la nouvelle arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="1e36c-140">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, and if the nodes being added nodes are already parented, the nodes are cloned and the clones are attached to the new XML tree.</span></span> <span data-ttu-id="1e36c-141">Si les nœuds existants ne sont pas apparentés, ils sont simplement attachés à la nouvelle arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="1e36c-141">If the existing nodes aren't parented, they're simply attached to the new XML tree.</span></span>

<span data-ttu-id="1e36c-142">Le code suivant illustre le comportement lorsque vous ajoutez un élément apparenté à une arborescence et lorsque vous ajoutez un élément non apparenté à une arborescence.</span><span class="sxs-lookup"><span data-stu-id="1e36c-142">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
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

<span data-ttu-id="1e36c-143">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1e36c-143">This example produces the following output:</span></span>

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="1e36c-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e36c-144">See also</span></span>

- [<span data-ttu-id="1e36c-145">Construction fonctionnelle</span><span class="sxs-lookup"><span data-stu-id="1e36c-145">Functional construction</span></span>](functional-construction.md)
