---
title: Utilisation des espaces de noms globaux (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 80510e370e0a9c7ab27cb5177d9b547ead82715c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350995"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="e9573-102">Utilisation d'espaces de noms globaux (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e9573-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="e9573-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="e9573-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="e9573-104">Grâce à cette fonctionnalité, vous pouvez déclarer un espace de noms XML qui utilise un préfixe ou déclarer un espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9573-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="e9573-105">Cette fonctionnalité est utile dans deux situations.</span><span class="sxs-lookup"><span data-stu-id="e9573-105">This capability is useful in two situations.</span></span> <span data-ttu-id="e9573-106">Tout d'abord, les espaces de noms déclarés dans des littéraux XML ne sont pas reportés dans les expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="e9573-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="e9573-107">La déclaration d'espaces de noms globaux réduit la quantité de travail nécessaire pour utiliser des expressions incorporées avec des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="e9573-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="e9573-108">En second lieu, vous devez déclarer des espaces de noms globaux afin d'utiliser des espaces de noms avec des propriétés XML.</span><span class="sxs-lookup"><span data-stu-id="e9573-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="e9573-109">Vous pouvez déclarer des espaces de noms globaux au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="e9573-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="e9573-110">Vous pouvez également déclarer des espaces de noms globaux au niveau du module, ce qui substitue les espaces de noms globaux au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="e9573-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="e9573-111">Pour finir, vous pouvez substituer des espaces de noms globaux dans un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="e9573-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="e9573-112">Lors de l'utilisation de littéraux XML ou de propriétés XML qui se trouvent dans des espaces de noms déclarés globalement, vous pouvez afficher le nom développé des littéraux ou des propriétés XML en plaçant le curseur de souris au-dessus d'eux dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9573-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="e9573-113">Le nom développé s’affiche alors dans une info-bulle.</span><span class="sxs-lookup"><span data-stu-id="e9573-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="e9573-114">Vous pouvez obtenir un objet <xref:System.Xml.Linq.XNamespace> qui correspond à un espace de noms global à l'aide de la méthode `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="e9573-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="e9573-115">Exemples d'espaces de noms globaux</span><span class="sxs-lookup"><span data-stu-id="e9573-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="e9573-116">L'exemple suivant déclare un espace de noms global par défaut à l'aide de l'instruction `Imports`, puis il utilise un littéral XML pour initialiser un objet <xref:System.Xml.Linq.XElement> dans cet espace de noms :</span><span class="sxs-lookup"><span data-stu-id="e9573-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e9573-117">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e9573-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="e9573-118">L'exemple suivant déclare un espace de noms global avec un préfixe, puis il utilise un littéral XML pour initialiser un élément :</span><span class="sxs-lookup"><span data-stu-id="e9573-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e9573-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e9573-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="e9573-120">Espaces de noms globaux et expressions incorporées</span><span class="sxs-lookup"><span data-stu-id="e9573-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="e9573-121">Les espaces de noms déclarés dans des littéraux XML ne sont pas reportés dans les expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="e9573-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="e9573-122">L'exemple suivant déclare un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9573-122">The following example declares a default namespace.</span></span> <span data-ttu-id="e9573-123">Il utilise ensuite une expression incorporée pour l'élément `Child`.</span><span class="sxs-lookup"><span data-stu-id="e9573-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="e9573-124">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e9573-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="e9573-125">Comme vous pouvez le voir, le code XML résultant inclut une déclaration d'un espace de noms par défaut de sorte que l'élément `Child` ne se trouve dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e9573-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="e9573-126">Vous pourriez redéclarer l'espace de noms dans l'expression incorporée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="e9573-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="e9573-127">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e9573-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="e9573-128">Toutefois, ceci peut s'avérer plus laborieux que l'approche de l'espace de noms global par défaut, qui est préférable.</span><span class="sxs-lookup"><span data-stu-id="e9573-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="e9573-129">Avec l'espace de noms global par défaut, vous pouvez utiliser des littéraux XML sans déclarer d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="e9573-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="e9573-130">Le code XML résultant sera dans l'espace de noms par défaut déclaré globalement.</span><span class="sxs-lookup"><span data-stu-id="e9573-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
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
  
 <span data-ttu-id="e9573-131">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e9573-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="e9573-132">Utilisation d'espaces de noms avec des propriétés XML</span><span class="sxs-lookup"><span data-stu-id="e9573-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="e9573-133">Si vous travaillez avec une arborescence XML qui se trouve dans un espace de noms et que vous utilisez des propriétés XML, vous devez utiliser un espace de noms global de sorte que les propriétés XML se trouvent également dans l’espace de noms correct.</span><span class="sxs-lookup"><span data-stu-id="e9573-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="e9573-134">L’exemple suivant déclare une arborescence XML dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e9573-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="e9573-135">Il imprime ensuite le nombre d'éléments `Child`.</span><span class="sxs-lookup"><span data-stu-id="e9573-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="e9573-136">Cet exemple indique qu'il n'existe aucun élément `Child`.</span><span class="sxs-lookup"><span data-stu-id="e9573-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="e9573-137">Il génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e9573-137">It produces the following output:</span></span>  
  
```console  
0  
```  
  
 <span data-ttu-id="e9573-138">Si toutefois vous déclarez un espace de noms global par défaut, le littéral XML et la propriété XML sont tous deux dans l'espace de noms global par défaut :</span><span class="sxs-lookup"><span data-stu-id="e9573-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
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
  
 <span data-ttu-id="e9573-139">Cet exemple indique qu'il existe un élément `Child`.</span><span class="sxs-lookup"><span data-stu-id="e9573-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="e9573-140">Il génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e9573-140">It produces the following output:</span></span>  
  
```console  
1  
```  
  
 <span data-ttu-id="e9573-141">Si vous déclarez un espace de noms global qui a un préfixe, vous pouvez utiliser le préfixe à la fois pour les littéraux XML et les propriétés XML :</span><span class="sxs-lookup"><span data-stu-id="e9573-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="e9573-142">XNamespace et espaces de noms globaux</span><span class="sxs-lookup"><span data-stu-id="e9573-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="e9573-143">Vous pouvez obtenir un objet <xref:System.Xml.Linq.XNamespace> à l'aide de la méthode `GetXmlNamespace` :</span><span class="sxs-lookup"><span data-stu-id="e9573-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
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
  
 <span data-ttu-id="e9573-144">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e9573-144">This example produces the following output:</span></span>  
  
```console  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9573-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9573-145">See also</span></span>

- [<span data-ttu-id="e9573-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9573-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
