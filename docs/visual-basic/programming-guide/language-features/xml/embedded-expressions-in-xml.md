---
title: Expressions incorporées en XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 525fa04db86a299d88e1612aac76d014f35124eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922629"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="fe248-102">Expressions incorporées en XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe248-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="fe248-103">Les expressions incorporées vous permettent de créer des littéraux XML qui contiennent des expressions évaluées au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fe248-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="fe248-104">La syntaxe d’une expression incorporée `<%=` est `expression` `%>`, qui est identique à la syntaxe utilisée dans ASP.net.</span><span class="sxs-lookup"><span data-stu-id="fe248-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="fe248-105">Par exemple, vous pouvez créer un littéral d’élément XML, en combinant des expressions incorporées avec un contenu de texte littéral.</span><span class="sxs-lookup"><span data-stu-id="fe248-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="fe248-106">Si `isbnNumber` contient l’entier 12345 et `modifiedDate` contient la date 3/5/2006, lorsque ce code s’exécute, la valeur de `book` est:</span><span class="sxs-lookup"><span data-stu-id="fe248-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="fe248-107">Emplacement et validation de l’expression incorporée</span><span class="sxs-lookup"><span data-stu-id="fe248-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="fe248-108">Les expressions incorporées peuvent apparaître uniquement à certains emplacements dans des expressions de littéral XML.</span><span class="sxs-lookup"><span data-stu-id="fe248-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="fe248-109">L’emplacement de l’expression contrôle les types que l’expression peut `Nothing` retourner et la façon dont est géré.</span><span class="sxs-lookup"><span data-stu-id="fe248-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="fe248-110">Le tableau suivant décrit les emplacements et types d’expressions incorporés autorisés.</span><span class="sxs-lookup"><span data-stu-id="fe248-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="fe248-111">Emplacement dans le littéral</span><span class="sxs-lookup"><span data-stu-id="fe248-111">Location in literal</span></span>|<span data-ttu-id="fe248-112">Type d’expression</span><span class="sxs-lookup"><span data-stu-id="fe248-112">Type of expression</span></span>|<span data-ttu-id="fe248-113">Gestion de`Nothing`</span><span class="sxs-lookup"><span data-stu-id="fe248-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="fe248-114">Nom d’élément XML</span><span class="sxs-lookup"><span data-stu-id="fe248-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="fe248-115">Error</span><span class="sxs-lookup"><span data-stu-id="fe248-115">Error</span></span>|  
|<span data-ttu-id="fe248-116">Contenu de l’élément XML</span><span class="sxs-lookup"><span data-stu-id="fe248-116">XML element content</span></span>|<span data-ttu-id="fe248-117">`Object`ou tableau de`Object`</span><span class="sxs-lookup"><span data-stu-id="fe248-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="fe248-118">Ignoré</span><span class="sxs-lookup"><span data-stu-id="fe248-118">Ignored</span></span>|  
|<span data-ttu-id="fe248-119">Nom de l’attribut d’élément XML</span><span class="sxs-lookup"><span data-stu-id="fe248-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="fe248-120">Erreur, sauf si la valeur de l’attribut est également`Nothing`</span><span class="sxs-lookup"><span data-stu-id="fe248-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="fe248-121">Valeur de l’attribut d’élément XML</span><span class="sxs-lookup"><span data-stu-id="fe248-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="fe248-122">Déclaration d’attribut ignorée</span><span class="sxs-lookup"><span data-stu-id="fe248-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="fe248-123">Attribut d’élément XML</span><span class="sxs-lookup"><span data-stu-id="fe248-123">XML element attribute</span></span>|<span data-ttu-id="fe248-124"><xref:System.Xml.Linq.XAttribute>ou une collection de<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="fe248-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="fe248-125">Ignoré</span><span class="sxs-lookup"><span data-stu-id="fe248-125">Ignored</span></span>|  
|<span data-ttu-id="fe248-126">Élément racine du document XML</span><span class="sxs-lookup"><span data-stu-id="fe248-126">XML document root element</span></span>|<span data-ttu-id="fe248-127"><xref:System.Xml.Linq.XElement>ou une collection d’un <xref:System.Xml.Linq.XElement> objet et d’un nombre arbitraire <xref:System.Xml.Linq.XProcessingInstruction> d' <xref:System.Xml.Linq.XComment> objets et</span><span class="sxs-lookup"><span data-stu-id="fe248-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="fe248-128">Ignoré</span><span class="sxs-lookup"><span data-stu-id="fe248-128">Ignored</span></span>|  
  
- <span data-ttu-id="fe248-129">Exemple d’expression incorporée dans un nom d’élément XML:</span><span class="sxs-lookup"><span data-stu-id="fe248-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="fe248-130">Exemple d’expression incorporée dans le contenu d’un élément XML:</span><span class="sxs-lookup"><span data-stu-id="fe248-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="fe248-131">Exemple d’une expression incorporée dans un nom d’attribut d’élément XML:</span><span class="sxs-lookup"><span data-stu-id="fe248-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="fe248-132">Exemple d’une expression incorporée dans une valeur d’attribut d’élément XML:</span><span class="sxs-lookup"><span data-stu-id="fe248-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="fe248-133">Exemple d’expression incorporée dans un attribut d’élément XML:</span><span class="sxs-lookup"><span data-stu-id="fe248-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="fe248-134">Exemple d’expression incorporée dans un élément racine de document XML:</span><span class="sxs-lookup"><span data-stu-id="fe248-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="fe248-135">Si vous activez `Option Strict`, le compilateur vérifie que le type de chaque expression incorporée s’étend au type requis.</span><span class="sxs-lookup"><span data-stu-id="fe248-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="fe248-136">La seule exception concerne l’élément racine d’un document XML, qui est vérifié au moment de l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="fe248-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="fe248-137">Si vous compilez sans `Option Strict`, vous pouvez incorporer des expressions de type `Object` et leur type est vérifié au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fe248-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="fe248-138">Dans les emplacements où le contenu est facultatif, les expressions `Nothing` incorporées qui contiennent sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="fe248-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="fe248-139">Cela signifie que vous n’avez pas besoin de vérifier que le contenu de l’élément, les valeurs d' `Nothing` attribut et les éléments de tableau ne sont pas antérieurs à l’utilisation d’un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="fe248-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="fe248-140">Les valeurs requises, telles que les noms d’élément et d' `Nothing`attribut, ne peuvent pas être.</span><span class="sxs-lookup"><span data-stu-id="fe248-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="fe248-141">Pour plus d’informations sur l’utilisation d’une expression incorporée dans un type particulier de littéral, consultez [littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="fe248-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="fe248-142">Règles de portée</span><span class="sxs-lookup"><span data-stu-id="fe248-142">Scoping Rules</span></span>  
 <span data-ttu-id="fe248-143">Le compilateur convertit chaque littéral XML en un appel de constructeur pour le type de littéral approprié.</span><span class="sxs-lookup"><span data-stu-id="fe248-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="fe248-144">Le contenu littéral et les expressions incorporées dans un littéral XML sont passés comme arguments au constructeur.</span><span class="sxs-lookup"><span data-stu-id="fe248-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="fe248-145">Cela signifie que tous les éléments de programmation Visual Basic disponibles pour un littéral XML sont également disponibles pour ses expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="fe248-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="fe248-146">Dans un littéral XML, vous pouvez accéder aux préfixes d’espaces de noms `Imports` XML déclarés avec l’instruction.</span><span class="sxs-lookup"><span data-stu-id="fe248-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="fe248-147">Vous pouvez déclarer un nouveau préfixe d’espace de noms XML ou occulter un préfixe d’espace de noms XML `xmlns` existant dans un élément à l’aide de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="fe248-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="fe248-148">Le nouvel espace de noms est disponible pour les nœuds enfants de cet élément, mais pas pour les littéraux XML dans les expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="fe248-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe248-149">Lorsque vous déclarez un préfixe d’espace de `xmlns` noms XML à l’aide de l’attribut d’espace de noms, la valeur de l’attribut doit être une chaîne constante.</span><span class="sxs-lookup"><span data-stu-id="fe248-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="fe248-150">À cet égard, l’utilisation `xmlns` de l’attribut est semblable `Imports` à l’utilisation de l’instruction pour déclarer un espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="fe248-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="fe248-151">Vous ne pouvez pas utiliser une expression incorporée pour spécifier la valeur de l’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="fe248-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe248-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe248-152">See also</span></span>

- [<span data-ttu-id="fe248-153">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe248-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="fe248-154">Littéral de document XML</span><span class="sxs-lookup"><span data-stu-id="fe248-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="fe248-155">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="fe248-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="fe248-156">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="fe248-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="fe248-157">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="fe248-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="fe248-158">Vue d’ensemble des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="fe248-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
