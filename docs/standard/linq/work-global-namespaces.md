---
title: Utiliser des espaces de noms globaux dans Visual Basic LINQ to XML
description: Vous déclarez un espace de noms dans Visual Basic à l’aide de l’instruction Imports, que l’espace de noms soit un espace de noms par défaut ou un préfixe. Cet article traite des instructions d’importation et d’autres aspects de l’utilisation des espaces de noms.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: f05fcab6788388e36e2b68a2d4f022ea63e74280
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553821"
---
# <a name="work-with-global-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="3c972-104">Utiliser des espaces de noms globaux dans Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3c972-104">Work with global namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="3c972-105">L’une des principales fonctionnalités des littéraux XML dans Visual Basic est la possibilité de déclarer des espaces de noms XML à l’aide de l' `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="3c972-105">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="3c972-106">Grâce à cette fonctionnalité, vous pouvez déclarer un espace de noms XML qui utilise un préfixe ou déclarer un espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="3c972-106">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>

<span data-ttu-id="3c972-107">Cette fonctionnalité est utile dans deux situations :</span><span class="sxs-lookup"><span data-stu-id="3c972-107">This capability is useful in two situations:</span></span>

- <span data-ttu-id="3c972-108">Les espaces de noms déclarés dans les littéraux XML ne sont pas reportés dans les expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="3c972-108">Namespaces declared in XML literals don't carry over into embedded expressions.</span></span> <span data-ttu-id="3c972-109">La déclaration d’espaces de noms globaux réduit la quantité de travail nécessaire à l’utilisation d’expressions incorporées avec des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="3c972-109">Declaring global namespaces reduces the amount of work needed to use embedded expressions with namespaces.</span></span>
- <span data-ttu-id="3c972-110">Vous devez déclarer des espaces de noms globaux afin d’utiliser des espaces de noms avec des propriétés XML.</span><span class="sxs-lookup"><span data-stu-id="3c972-110">You must declare global namespaces in order to use namespaces with XML properties.</span></span>

<span data-ttu-id="3c972-111">Vous pouvez déclarer des espaces de noms globaux au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="3c972-111">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="3c972-112">Vous pouvez également déclarer des espaces de noms globaux au niveau du module, ce qui substitue les espaces de noms globaux au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="3c972-112">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="3c972-113">Pour finir, vous pouvez substituer des espaces de noms globaux dans un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="3c972-113">Finally, you can override global namespaces in an XML literal.</span></span>

<span data-ttu-id="3c972-114">Lorsque vous utilisez des littéraux XML ou des propriétés XML qui se trouvent dans des espaces de noms déclarés globalement, vous pouvez afficher le nom développé des littéraux ou des propriétés XML en pointant dessus dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3c972-114">When using XML literals or XML properties that are in globally declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="3c972-115">Le nom développé s’affiche alors dans une info-bulle.</span><span class="sxs-lookup"><span data-stu-id="3c972-115">You will see the expanded name in a tooltip.</span></span>

<span data-ttu-id="3c972-116">Vous pouvez obtenir un objet <xref:System.Xml.Linq.XNamespace> qui correspond à un espace de noms global à l'aide de la méthode `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="3c972-116">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>

## <a name="example-use-imports-to-declare-a-global-namespace"></a><span data-ttu-id="3c972-117">Exemple : utilisation `Imports` pour déclarer un espace de noms global</span><span class="sxs-lookup"><span data-stu-id="3c972-117">Example: Use `Imports` to declare a global namespace</span></span>

<span data-ttu-id="3c972-118">L’exemple suivant déclare un espace de noms global par défaut avec l' `Imports` instruction, puis initialise un <xref:System.Xml.Linq.XElement> objet dans cet espace de noms avec un littéral XML :</span><span class="sxs-lookup"><span data-stu-id="3c972-118">The following example declares a default global namespace with the `Imports` statement, and then initializes an <xref:System.Xml.Linq.XElement> object in that namespace with an XML literal:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="3c972-119">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3c972-119">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" />
```

## <a name="example-declare-a-global-namespace-that-has-a-prefix"></a><span data-ttu-id="3c972-120">Exemple : déclarer un espace de noms global qui a un préfixe</span><span class="sxs-lookup"><span data-stu-id="3c972-120">Example: Declare a global namespace that has a prefix</span></span>

<span data-ttu-id="3c972-121">L’exemple suivant déclare un espace de noms global avec un préfixe et initialise un élément avec un littéral XML :</span><span class="sxs-lookup"><span data-stu-id="3c972-121">The next example declares a global namespace with a prefix, and initializes an element with an XML literal:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="3c972-122">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3c972-122">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" />
```

## <a name="example-declare-a-default-namespace-and-use-an-embedded-expression-for-the-child-element"></a><span data-ttu-id="3c972-123">Exemple : déclarer un espace de noms par défaut et utiliser une expression incorporée pour l' `Child` élément</span><span class="sxs-lookup"><span data-stu-id="3c972-123">Example: Declare a default namespace and use an embedded expression for the `Child` element</span></span>

<span data-ttu-id="3c972-124">Les espaces de noms déclarés dans des littéraux XML ne sont pas reportés dans les expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="3c972-124">Namespaces that are declared in XML literals don't carry over into embedded expressions.</span></span> <span data-ttu-id="3c972-125">L’exemple suivant déclare un espace de noms par défaut, puis utilise une expression incorporée pour l' `Child` élément.</span><span class="sxs-lookup"><span data-stu-id="3c972-125">The following example declares a default namespace, and then uses an embedded expression for the `Child` element.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child/> %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="3c972-126">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3c972-126">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="" />
</Root>
```

<span data-ttu-id="3c972-127">Le XML obtenu comprend une déclaration d’un espace de noms par défaut, de sorte que l' `Child` élément ne se trouve pas dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3c972-127">The resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>

<span data-ttu-id="3c972-128">Vous pouvez déclarer un espace de noms différent dans l’expression incorporée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="3c972-128">You could declare a different namespace in the embedded expression, as follows:</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child xmlns="http://www.adventure-works.com"/> %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="3c972-129">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3c972-129">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="http://www.adventure-works.com" />
</Root>
```

<span data-ttu-id="3c972-130">Toutefois, avec l’espace de noms global par défaut, vous pouvez utiliser des littéraux XML sans déclarer d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="3c972-130">However, with the global default namespace you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="3c972-131">Le code XML résultant sera dans l’espace de noms par défaut déclaré globalement, comme dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="3c972-131">The resulting XML will be in the globally-declared default namespace, as in this example:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root>
                                   <%= <Child/> %>
                               </Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="3c972-132">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3c972-132">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child />
</Root>
```

## <a name="example-use-namespaces-with-xml-properties"></a><span data-ttu-id="3c972-133">Exemple : utiliser des espaces de noms avec des propriétés XML</span><span class="sxs-lookup"><span data-stu-id="3c972-133">Example: Use namespaces with XML properties</span></span>

<span data-ttu-id="3c972-134">Si vous travaillez avec une arborescence XML qui se trouve dans un espace de noms et que vous utilisez des propriétés XML, vous devez utiliser un espace de noms global afin que les propriétés XML se trouvent également dans l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="3c972-134">If you're working with an XML tree that's in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="3c972-135">L’exemple suivant déclare une arborescence XML dans un espace de noms, puis imprime le nombre d' `Child` éléments.</span><span class="sxs-lookup"><span data-stu-id="3c972-135">The following example declares an XML tree in a namespace, and then prints the count of `Child` elements.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <Child>content</Child>
    </Root>
Console.WriteLine(root.<Child>.Count())
```

<span data-ttu-id="3c972-136">Cet exemple indique qu'il n'existe aucun élément `Child`.</span><span class="sxs-lookup"><span data-stu-id="3c972-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="3c972-137">Il génère cette sortie :</span><span class="sxs-lookup"><span data-stu-id="3c972-137">It produces this output:</span></span>

```output
0
```

<span data-ttu-id="3c972-138">Si toutefois vous déclarez un espace de noms global par défaut, le littéral XML et la propriété XML sont tous deux dans l'espace de noms global par défaut :</span><span class="sxs-lookup"><span data-stu-id="3c972-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>content</Child>
            </Root>
        Console.WriteLine(root.<Child>.Count())
    End Sub
End Module
```

<span data-ttu-id="3c972-139">Cet exemple indique qu'il existe un élément `Child`.</span><span class="sxs-lookup"><span data-stu-id="3c972-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="3c972-140">Il génère cette sortie :</span><span class="sxs-lookup"><span data-stu-id="3c972-140">It produces this output:</span></span>

```output
1
```

<span data-ttu-id="3c972-141">Si vous déclarez un espace de noms global qui a un préfixe, vous pouvez utiliser le préfixe à la fois pour les littéraux XML et les propriétés XML :</span><span class="sxs-lookup"><span data-stu-id="3c972-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>content</aw:Child>
            </aw:Root>
        Console.WriteLine(root.<aw:Child>.Count())
    End Sub
End Module
```

## <a name="example-use-getxmlnamespace-to-get-an-xnamespace"></a><span data-ttu-id="3c972-142">Exemple : utilisez `GetXmlNamespace` pour récupérer un `XNamespace`</span><span class="sxs-lookup"><span data-stu-id="3c972-142">Example: Use `GetXmlNamespace` to get an `XNamespace`</span></span>

<span data-ttu-id="3c972-143">Vous pouvez obtenir un <xref:System.Xml.Linq.XNamespace> objet à l’aide de la `GetXmlNamespace` méthode :</span><span class="sxs-lookup"><span data-stu-id="3c972-143">You can obtain an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Dim xn As XNamespace = GetXmlNamespace(aw)
        Console.WriteLine(xn)
    End Sub
End Module
```

<span data-ttu-id="3c972-144">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3c972-144">This example produces the following output:</span></span>

```output
http://www.adventure-works.com
```

## <a name="see-also"></a><span data-ttu-id="3c972-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c972-145">See also</span></span>

- [<span data-ttu-id="3c972-146">Vue d’ensemble des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="3c972-146">Namespaces overview</span></span>](namespaces-overview.md)
