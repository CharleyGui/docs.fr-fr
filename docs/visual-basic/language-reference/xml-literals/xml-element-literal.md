---
title: Littéral d'élément XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347025"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="5659e-102">Littéral d'élément XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5659e-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="5659e-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span><span class="sxs-lookup"><span data-stu-id="5659e-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="5659e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5659e-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="5659e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="5659e-105">Parts</span></span>

- `<`

  <span data-ttu-id="5659e-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="5659e-106">Required.</span></span> <span data-ttu-id="5659e-107">Opens the starting element tag.</span><span class="sxs-lookup"><span data-stu-id="5659e-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="5659e-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="5659e-108">Required.</span></span> <span data-ttu-id="5659e-109">Nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="5659e-109">Name of the element.</span></span> <span data-ttu-id="5659e-110">The format is one of the following:</span><span class="sxs-lookup"><span data-stu-id="5659e-110">The format is one of the following:</span></span>

  - <span data-ttu-id="5659e-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span><span class="sxs-lookup"><span data-stu-id="5659e-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="5659e-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5659e-112">Part</span></span>|<span data-ttu-id="5659e-113">Description</span><span class="sxs-lookup"><span data-stu-id="5659e-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="5659e-114">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5659e-114">Optional.</span></span> <span data-ttu-id="5659e-115">XML namespace prefix for the element.</span><span class="sxs-lookup"><span data-stu-id="5659e-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="5659e-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span><span class="sxs-lookup"><span data-stu-id="5659e-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="5659e-117">Requis.</span><span class="sxs-lookup"><span data-stu-id="5659e-117">Required.</span></span> <span data-ttu-id="5659e-118">Nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="5659e-118">Name of the element.</span></span> <span data-ttu-id="5659e-119">The format is one of the following:</span><span class="sxs-lookup"><span data-stu-id="5659e-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5659e-120">- Literal text.</span><span class="sxs-lookup"><span data-stu-id="5659e-120">- Literal text.</span></span> <span data-ttu-id="5659e-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5659e-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="5659e-122">- Embedded expression of the form `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5659e-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="5659e-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5659e-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="5659e-124">Embedded expression of the form `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5659e-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="5659e-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5659e-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="5659e-126">An embedded expression is not allowed in a closing tag of an element.</span><span class="sxs-lookup"><span data-stu-id="5659e-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="5659e-127">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5659e-127">Optional.</span></span> <span data-ttu-id="5659e-128">List of attributes declared in the literal.</span><span class="sxs-lookup"><span data-stu-id="5659e-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="5659e-129">Each `attribute` has one of the following syntaxes:</span><span class="sxs-lookup"><span data-stu-id="5659e-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="5659e-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span><span class="sxs-lookup"><span data-stu-id="5659e-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="5659e-131">Élément</span><span class="sxs-lookup"><span data-stu-id="5659e-131">Part</span></span>|<span data-ttu-id="5659e-132">Description</span><span class="sxs-lookup"><span data-stu-id="5659e-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="5659e-133">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5659e-133">Optional.</span></span> <span data-ttu-id="5659e-134">XML namespace prefix for the attribute.</span><span class="sxs-lookup"><span data-stu-id="5659e-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="5659e-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span><span class="sxs-lookup"><span data-stu-id="5659e-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="5659e-136">Requis.</span><span class="sxs-lookup"><span data-stu-id="5659e-136">Required.</span></span> <span data-ttu-id="5659e-137">Nom de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="5659e-137">Name of the attribute.</span></span> <span data-ttu-id="5659e-138">The format is one of the following:</span><span class="sxs-lookup"><span data-stu-id="5659e-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5659e-139">- Literal text.</span><span class="sxs-lookup"><span data-stu-id="5659e-139">- Literal text.</span></span> <span data-ttu-id="5659e-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5659e-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="5659e-141">- Embedded expression of the form `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5659e-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="5659e-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5659e-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="5659e-143">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5659e-143">Optional.</span></span> <span data-ttu-id="5659e-144">Value of the attribute.</span><span class="sxs-lookup"><span data-stu-id="5659e-144">Value of the attribute.</span></span> <span data-ttu-id="5659e-145">The format is one of the following:</span><span class="sxs-lookup"><span data-stu-id="5659e-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="5659e-146">- Literal text, enclosed in quotation marks.</span><span class="sxs-lookup"><span data-stu-id="5659e-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="5659e-147">- Embedded expression of the form `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5659e-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="5659e-148">Any type is allowed.</span><span class="sxs-lookup"><span data-stu-id="5659e-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="5659e-149">Embedded expression of the form `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5659e-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="5659e-150">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5659e-150">Optional.</span></span> <span data-ttu-id="5659e-151">Indicates that the element is an empty element, without content.</span><span class="sxs-lookup"><span data-stu-id="5659e-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="5659e-152">Requis.</span><span class="sxs-lookup"><span data-stu-id="5659e-152">Required.</span></span> <span data-ttu-id="5659e-153">Ends the beginning or empty element tag.</span><span class="sxs-lookup"><span data-stu-id="5659e-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="5659e-154">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5659e-154">Optional.</span></span> <span data-ttu-id="5659e-155">Content of the element.</span><span class="sxs-lookup"><span data-stu-id="5659e-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="5659e-156">Each `content` can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="5659e-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="5659e-157">Literal text.</span><span class="sxs-lookup"><span data-stu-id="5659e-157">Literal text.</span></span> <span data-ttu-id="5659e-158">All the white space in `elementContents` becomes significant if there is any literal text.</span><span class="sxs-lookup"><span data-stu-id="5659e-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="5659e-159">Embedded expression of the form `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="5659e-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="5659e-160">XML element literal.</span><span class="sxs-lookup"><span data-stu-id="5659e-160">XML element literal.</span></span>

  - <span data-ttu-id="5659e-161">XML comment literal.</span><span class="sxs-lookup"><span data-stu-id="5659e-161">XML comment literal.</span></span> <span data-ttu-id="5659e-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5659e-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>

  - <span data-ttu-id="5659e-163">XML processing instruction literal.</span><span class="sxs-lookup"><span data-stu-id="5659e-163">XML processing instruction literal.</span></span> <span data-ttu-id="5659e-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5659e-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="5659e-165">XML CDATA literal.</span><span class="sxs-lookup"><span data-stu-id="5659e-165">XML CDATA literal.</span></span> <span data-ttu-id="5659e-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="5659e-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="5659e-167">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="5659e-167">Optional.</span></span> <span data-ttu-id="5659e-168">Represents the closing tag for the element.</span><span class="sxs-lookup"><span data-stu-id="5659e-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="5659e-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span><span class="sxs-lookup"><span data-stu-id="5659e-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="5659e-170">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5659e-170">Return Value</span></span>

<span data-ttu-id="5659e-171">Objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5659e-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="5659e-172">Notes</span><span class="sxs-lookup"><span data-stu-id="5659e-172">Remarks</span></span>

<span data-ttu-id="5659e-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span><span class="sxs-lookup"><span data-stu-id="5659e-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="5659e-174">An XML literal can span multiple lines without using line continuation characters.</span><span class="sxs-lookup"><span data-stu-id="5659e-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="5659e-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span><span class="sxs-lookup"><span data-stu-id="5659e-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="5659e-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span><span class="sxs-lookup"><span data-stu-id="5659e-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="5659e-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5659e-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="5659e-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span><span class="sxs-lookup"><span data-stu-id="5659e-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="5659e-179">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="5659e-179">XML Namespaces</span></span>

<span data-ttu-id="5659e-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span><span class="sxs-lookup"><span data-stu-id="5659e-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="5659e-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span><span class="sxs-lookup"><span data-stu-id="5659e-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="5659e-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5659e-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="5659e-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span><span class="sxs-lookup"><span data-stu-id="5659e-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="5659e-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span><span class="sxs-lookup"><span data-stu-id="5659e-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="5659e-185">The embedded expression can access only the global XML namespace.</span><span class="sxs-lookup"><span data-stu-id="5659e-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="5659e-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span><span class="sxs-lookup"><span data-stu-id="5659e-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="5659e-187">Global XML namespaces that are not used do not appear in the generated code.</span><span class="sxs-lookup"><span data-stu-id="5659e-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="5659e-188">Exemple</span><span class="sxs-lookup"><span data-stu-id="5659e-188">Example</span></span>

<span data-ttu-id="5659e-189">The following example shows how to create a simple XML element that has two nested empty elements.</span><span class="sxs-lookup"><span data-stu-id="5659e-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="5659e-190">The example displays the following text.</span><span class="sxs-lookup"><span data-stu-id="5659e-190">The example displays the following text.</span></span> <span data-ttu-id="5659e-191">Notice that the literal preserves the structure of the empty elements.</span><span class="sxs-lookup"><span data-stu-id="5659e-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="5659e-192">Exemple</span><span class="sxs-lookup"><span data-stu-id="5659e-192">Example</span></span>

<span data-ttu-id="5659e-193">The following example shows how to use embedded expressions to name an element and create attributes.</span><span class="sxs-lookup"><span data-stu-id="5659e-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="5659e-194">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="5659e-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="5659e-195">Exemple</span><span class="sxs-lookup"><span data-stu-id="5659e-195">Example</span></span>

<span data-ttu-id="5659e-196">L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="5659e-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5659e-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span><span class="sxs-lookup"><span data-stu-id="5659e-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="5659e-198">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="5659e-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="5659e-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span><span class="sxs-lookup"><span data-stu-id="5659e-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="5659e-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span><span class="sxs-lookup"><span data-stu-id="5659e-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="5659e-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="5659e-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="5659e-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5659e-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="5659e-203">Nom des attributs et des éléments XML déclarés</span><span class="sxs-lookup"><span data-stu-id="5659e-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="5659e-204">Littéraux de commentaires XML</span><span class="sxs-lookup"><span data-stu-id="5659e-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="5659e-205">Littéral CDATA XML</span><span class="sxs-lookup"><span data-stu-id="5659e-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="5659e-206">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="5659e-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="5659e-207">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5659e-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="5659e-208">Expressions incorporées en XML</span><span class="sxs-lookup"><span data-stu-id="5659e-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="5659e-209">Imports (instruction) (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="5659e-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
