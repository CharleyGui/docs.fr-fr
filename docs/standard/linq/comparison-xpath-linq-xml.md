---
title: Comparaison entre XPath et LINQ to XML-LINQ to XML
description: Les requêtes XPath et LINQ to XML peuvent interroger des arborescences XML. Cet article compare les deux options et recherche LINQ to XML les requêtes sont, sur l’ensemble, le plus puissant, polyvalent, plus rapide, plus sûr et plus pratique.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553399"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="c2b1d-104">Comparaison de XPath et LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="c2b1d-104">Comparison of XPath and LINQ to XML</span></span>

<span data-ttu-id="c2b1d-105">XPath et LINQ to XML sont similaires d’une certaine manière.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-105">XPath and LINQ to XML are similar in some ways.</span></span> <span data-ttu-id="c2b1d-106">Tous deux peuvent être utilisés pour interroger une arborescence XML et retourner des résultats tels qu'une collection d'élément, une collection d'attributs, une collection de nœuds ou la valeur d'un élément ou attribut.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="c2b1d-107">Toutefois, il existe des différences significatives entre les deux options.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-107">However, there are significant differences between the two options.</span></span>

## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="c2b1d-108">Différences entre XPath et LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="c2b1d-108">Differences between XPath and LINQ to XML</span></span>

<span data-ttu-id="c2b1d-109">XPath n’autorise pas la projection de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-109">XPath doesn't allow projection of new types.</span></span> <span data-ttu-id="c2b1d-110">Il peut uniquement retourner des collections de nœuds de l’arborescence, tandis que LINQ to XML peut exécuter une requête et projeter un graphique d’objet ou une arborescence XML dans une nouvelle forme.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="c2b1d-111">LINQ to XML requêtes peuvent faire bien plus que des expressions XPath.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-111">LINQ to XML queries can do much more than XPath expressions.</span></span>

<span data-ttu-id="c2b1d-112">Les expressions XPath existent de manière isolée dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="c2b1d-113">Le compilateur C# ne peut pas aider à analyser l’expression XPath au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-113">The C# compiler can't help parse the XPath expression at compile time.</span></span> <span data-ttu-id="c2b1d-114">En revanche, c’est lui qui analyse et compile les requêtes LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="c2b1d-115">Le compilateur peut intercepter de nombreuses erreurs de requête.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-115">The compiler can catch many query errors.</span></span>

<span data-ttu-id="c2b1d-116">Les résultats XPath ne sont pas fortement typés.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-116">XPath results aren't strongly typed.</span></span> <span data-ttu-id="c2b1d-117">Dans plusieurs cas, le résultat de l’évaluation d’une expression XPath est un objet, et c’est au développeur de déterminer le type approprié et de convertir le résultat si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it's up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="c2b1d-118">En revanche, les projections à partir d’une requête LINQ to XML sont fortement typées.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>

## <a name="result-ordering"></a><span data-ttu-id="c2b1d-119">Classement des résultats</span><span class="sxs-lookup"><span data-stu-id="c2b1d-119">Result ordering</span></span>

<span data-ttu-id="c2b1d-120">La recommandation XPath 1,0 stipule qu’une collection qui est le résultat de l’évaluation d’une expression XPath n’est pas ordonnée.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-120">The XPath 1.0 Recommendation states that a collection that's the result of evaluating an XPath expression is unordered.</span></span>

<span data-ttu-id="c2b1d-121">Toutefois, lors de l’itération d’une collection retournée par une méthode d’axe XPath LINQ to XML, les nœuds de la collection sont retournés dans l’ordre du document.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="c2b1d-122">Cela est valable même lors de l'accès à des axes XPath où les prédicats sont exprimés dans l'ordre inverse du document, par exemple `preceding` et `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>

<span data-ttu-id="c2b1d-123">En revanche, la plupart des LINQ to XML axes retournent les collections dans l’ordre du document.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-123">By contrast, most of the LINQ to XML axes return collections in document order.</span></span> <span data-ttu-id="c2b1d-124">Toutefois, deux d’entre eux, <xref:System.Xml.Linq.XNode.Ancestors%2A> et <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> , retournent des collections dans l’ordre inverse du document.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-124">However, two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="c2b1d-125">Le tableau suivant énumère les axes et indique l’ordre de collection pour chacun d’eux :</span><span class="sxs-lookup"><span data-stu-id="c2b1d-125">The following table enumerates the axes, and indicates the collection order for each:</span></span>

|<span data-ttu-id="c2b1d-126">Axe LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="c2b1d-126">LINQ to XML axis</span></span>|<span data-ttu-id="c2b1d-127">Classement</span><span class="sxs-lookup"><span data-stu-id="c2b1d-127">Ordering</span></span>|
|----------------------|--------------|
|<span data-ttu-id="c2b1d-128">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="c2b1d-128">XContainer.DescendantNodes</span></span>|<span data-ttu-id="c2b1d-129">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-129">Document order</span></span>|
|<span data-ttu-id="c2b1d-130">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="c2b1d-130">XContainer.Descendants</span></span>|<span data-ttu-id="c2b1d-131">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-131">Document order</span></span>|
|<span data-ttu-id="c2b1d-132">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="c2b1d-132">XContainer.Elements</span></span>|<span data-ttu-id="c2b1d-133">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-133">Document order</span></span>|
|<span data-ttu-id="c2b1d-134">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="c2b1d-134">XContainer.Nodes</span></span>|<span data-ttu-id="c2b1d-135">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-135">Document order</span></span>|
|<span data-ttu-id="c2b1d-136">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-136">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="c2b1d-137">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-137">Document order</span></span>|
|<span data-ttu-id="c2b1d-138">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-138">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="c2b1d-139">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-139">Document order</span></span>|
|<span data-ttu-id="c2b1d-140">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-140">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="c2b1d-141">Ordre inverse du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-141">Reverse document order</span></span>|
|<span data-ttu-id="c2b1d-142">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="c2b1d-142">XElement.Attributes</span></span>|<span data-ttu-id="c2b1d-143">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-143">Document order</span></span>|
|<span data-ttu-id="c2b1d-144">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-144">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="c2b1d-145">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-145">Document order</span></span>|
|<span data-ttu-id="c2b1d-146">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-146">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="c2b1d-147">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-147">Document order</span></span>|
|<span data-ttu-id="c2b1d-148">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="c2b1d-148">XNode.Ancestors</span></span>|<span data-ttu-id="c2b1d-149">Ordre inverse du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-149">Reverse document order</span></span>|
|<span data-ttu-id="c2b1d-150">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-150">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="c2b1d-151">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-151">Document order</span></span>|
|<span data-ttu-id="c2b1d-152">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-152">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="c2b1d-153">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-153">Document order</span></span>|
|<span data-ttu-id="c2b1d-154">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-154">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="c2b1d-155">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-155">Document order</span></span>|
|<span data-ttu-id="c2b1d-156">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="c2b1d-156">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="c2b1d-157">Ordre du document</span><span class="sxs-lookup"><span data-stu-id="c2b1d-157">Document order</span></span>|

## <a name="positional-predicates"></a><span data-ttu-id="c2b1d-158">Prédicats positionnels</span><span class="sxs-lookup"><span data-stu-id="c2b1d-158">Positional predicates</span></span>

<span data-ttu-id="c2b1d-159">Dans une expression XPath, les prédicats positionnels sont exprimés en termes d’ordre des documents pour de nombreux axes, mais sont exprimés dans l’ordre inverse des documents pour les axes inversés.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-159">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes.</span></span> <span data-ttu-id="c2b1d-160">Les axes inversé sont les suivants : `preceding` , `preceding-sibling` , `ancestor` et `ancestor-or-self` .</span><span class="sxs-lookup"><span data-stu-id="c2b1d-160">The reverse axes are: `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="c2b1d-161">Par exemple, l'expression XPath `preceding-sibling::*[1]` retourne le frère qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-161">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="c2b1d-162">C'est le cas même si le jeu de résultats final est présenté dans l'ordre du document.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-162">This is the case even though the final result set is presented in document order.</span></span>

<span data-ttu-id="c2b1d-163">Par contraste, tous les prédicats de position dans LINQ to XML sont toujours exprimés dans l'ordre de l'axe.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-163">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="c2b1d-164">Par exemple, `anElement.ElementsBeforeSelf().ElementAt(0)` retourne le premier élément enfant du parent de l'élément interrogé, mais pas l'enfant qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-164">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="c2b1d-165">Autre exemple : `anElement.Ancestors().ElementAt(0)` retourne l'élément parent.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-165">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>

<span data-ttu-id="c2b1d-166">Si vous souhaitez rechercher l’élément qui précède dans LINQ to XML, vous devez écrire l’expression suivante :</span><span class="sxs-lookup"><span data-stu-id="c2b1d-166">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a><span data-ttu-id="c2b1d-167">Différences de performances</span><span class="sxs-lookup"><span data-stu-id="c2b1d-167">Performance differences</span></span>

<span data-ttu-id="c2b1d-168">Les requêtes XPath qui utilisent la fonctionnalité XPath dans LINQ to XML seront plus lentes que les requêtes LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-168">XPath queries that use the XPath functionality in LINQ to XML will be slower than LINQ to XML queries.</span></span>

## <a name="comparison-of-composition"></a><span data-ttu-id="c2b1d-169">Comparaison de la composition</span><span class="sxs-lookup"><span data-stu-id="c2b1d-169">Comparison of composition</span></span>

<span data-ttu-id="c2b1d-170">La composition d’une requête LINQ to XML est semblable à la composition d’une expression XPath, mais la syntaxe est très différente.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-170">Composition of a LINQ to XML query is similar to composition of an XPath expression, but the syntax is very different.</span></span>

<span data-ttu-id="c2b1d-171">Par exemple, si vous avez un élément dans une variable nommée `customers` et que vous souhaitez trouver un élément petit-enfant nommé `CompanyName` sous tous les éléments enfants nommés `Customer` , vous devez écrire l’expression XPath suivante :</span><span class="sxs-lookup"><span data-stu-id="c2b1d-171">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write this XPath expression:</span></span>

```csharp
customers.XPathSelectElements("./Customer/CompanyName")
```

```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

<span data-ttu-id="c2b1d-172">La requête LINQ to XML équivalente est :</span><span class="sxs-lookup"><span data-stu-id="c2b1d-172">The equivalent LINQ to XML query is:</span></span>

```csharp
customers.Elements("Customer").Elements("CompanyName")
```

```vb
customers.Elements("Customer").Elements("CompanyName")
```

<span data-ttu-id="c2b1d-173">Il existe des parallèles similaires pour chacun des axes XPath.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-173">There are similar parallels for each of the XPath axes.</span></span>

|<span data-ttu-id="c2b1d-174">Axe XPath</span><span class="sxs-lookup"><span data-stu-id="c2b1d-174">XPath axis</span></span>|<span data-ttu-id="c2b1d-175">Axe LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="c2b1d-175">LINQ to XML axis</span></span>|
|----------------|----------------------|
|<span data-ttu-id="c2b1d-176">enfant (l'axe par défaut)</span><span class="sxs-lookup"><span data-stu-id="c2b1d-176">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-177">Parent (..)</span><span class="sxs-lookup"><span data-stu-id="c2b1d-177">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-178">axe des attributs (@)</span><span class="sxs-lookup"><span data-stu-id="c2b1d-178">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="c2b1d-179">or</span><span class="sxs-lookup"><span data-stu-id="c2b1d-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-180">axe des ancêtres</span><span class="sxs-lookup"><span data-stu-id="c2b1d-180">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-181">axe ancestor-or-self</span><span class="sxs-lookup"><span data-stu-id="c2b1d-181">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-182">axe des descendants (//)</span><span class="sxs-lookup"><span data-stu-id="c2b1d-182">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="c2b1d-183">or</span><span class="sxs-lookup"><span data-stu-id="c2b1d-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-184">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="c2b1d-184">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="c2b1d-185">or</span><span class="sxs-lookup"><span data-stu-id="c2b1d-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-186">frère suivant</span><span class="sxs-lookup"><span data-stu-id="c2b1d-186">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="c2b1d-187">or</span><span class="sxs-lookup"><span data-stu-id="c2b1d-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-188">frère précédent</span><span class="sxs-lookup"><span data-stu-id="c2b1d-188">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="c2b1d-189">or</span><span class="sxs-lookup"><span data-stu-id="c2b1d-189">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="c2b1d-190">suivant</span><span class="sxs-lookup"><span data-stu-id="c2b1d-190">following</span></span>|<span data-ttu-id="c2b1d-191">Aucun équivalent direct.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-191">No direct equivalent.</span></span>|
|<span data-ttu-id="c2b1d-192">précédent</span><span class="sxs-lookup"><span data-stu-id="c2b1d-192">preceding</span></span>|<span data-ttu-id="c2b1d-193">Aucun équivalent direct.</span><span class="sxs-lookup"><span data-stu-id="c2b1d-193">No direct equivalent.</span></span>|
