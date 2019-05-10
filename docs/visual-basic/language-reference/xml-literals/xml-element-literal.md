---
title: Littéral d'élément XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 3431ad32809e1f15eb8473d5af7660367cca04de
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751954"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="aa1b5-102">Littéral d'élément XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa1b5-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="aa1b5-103">Un littéral qui représente un <xref:System.Xml.Linq.XElement> objet.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa1b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa1b5-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="aa1b5-105">Composants</span><span class="sxs-lookup"><span data-stu-id="aa1b5-105">Parts</span></span>

- `<`

  <span data-ttu-id="aa1b5-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-106">Required.</span></span> <span data-ttu-id="aa1b5-107">Ouvre la balise d’élément initiale.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="aa1b5-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-108">Required.</span></span> <span data-ttu-id="aa1b5-109">Nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-109">Name of the element.</span></span> <span data-ttu-id="aa1b5-110">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-110">The format is one of the following:</span></span>

  - <span data-ttu-id="aa1b5-111">Texte littéral pour le nom d’élément, sous la forme `[ePrefix:]eName`, où :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="aa1b5-112">Élément</span><span class="sxs-lookup"><span data-stu-id="aa1b5-112">Part</span></span>|<span data-ttu-id="aa1b5-113">Description</span><span class="sxs-lookup"><span data-stu-id="aa1b5-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="aa1b5-114">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-114">Optional.</span></span> <span data-ttu-id="aa1b5-115">Préfixe d’espace de noms XML pour l’élément.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="aa1b5-116">Doit être un espace de noms XML global qui est défini avec un `Imports` instruction dans le fichier ou au niveau du projet, ou un espace de noms XML local qui est défini dans cet élément ou un élément parent.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="aa1b5-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-117">Required.</span></span> <span data-ttu-id="aa1b5-118">Nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-118">Name of the element.</span></span> <span data-ttu-id="aa1b5-119">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="aa1b5-120">-Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-120">- Literal text.</span></span> <span data-ttu-id="aa1b5-121">Consultez [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="aa1b5-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="aa1b5-122">-Incorporé expression sous la forme `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="aa1b5-123">Le type de `eNameExp` doit être `String` ou un type qui est implicitement convertible en <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="aa1b5-124">Expression sous la forme incorporée `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="aa1b5-125">Le type de `nameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="aa1b5-126">Une expression incorporée n’est pas autorisée dans une balise de fermeture d’un élément.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="aa1b5-127">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-127">Optional.</span></span> <span data-ttu-id="aa1b5-128">Liste des attributs déclarés dans le littéral.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="aa1b5-129">Chaque `attribute` a l’une des syntaxes suivantes :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="aa1b5-130">Assignation, sous la forme de l’attribut `[aPrefix:]aName=aValue`, où :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="aa1b5-131">Élément</span><span class="sxs-lookup"><span data-stu-id="aa1b5-131">Part</span></span>|<span data-ttu-id="aa1b5-132">Description</span><span class="sxs-lookup"><span data-stu-id="aa1b5-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="aa1b5-133">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-133">Optional.</span></span> <span data-ttu-id="aa1b5-134">Préfixe d’espace de noms XML pour l’attribut.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="aa1b5-135">Doit être un espace de noms XML global qui est défini avec un `Imports` instruction ou un espace de noms XML local qui est défini dans cet élément ou un élément parent.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="aa1b5-136">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-136">Required.</span></span> <span data-ttu-id="aa1b5-137">Nom de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-137">Name of the attribute.</span></span> <span data-ttu-id="aa1b5-138">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="aa1b5-139">-Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-139">- Literal text.</span></span> <span data-ttu-id="aa1b5-140">Consultez [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="aa1b5-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="aa1b5-141">-Incorporé expression sous la forme `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="aa1b5-142">Le type de `aNameExp` doit être `String` ou un type qui est implicitement convertible en <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="aa1b5-143">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-143">Optional.</span></span> <span data-ttu-id="aa1b5-144">Valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-144">Value of the attribute.</span></span> <span data-ttu-id="aa1b5-145">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="aa1b5-146">-Texte littéral, entourée de guillemets.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="aa1b5-147">-Incorporé expression sous la forme `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="aa1b5-148">N’importe quel type est autorisé.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="aa1b5-149">Expression sous la forme incorporée `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="aa1b5-150">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-150">Optional.</span></span> <span data-ttu-id="aa1b5-151">Indique que l’élément est un élément vide, sans contenu.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="aa1b5-152">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-152">Required.</span></span> <span data-ttu-id="aa1b5-153">Met fin à la balise d’élément initiale ou vide.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="aa1b5-154">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-154">Optional.</span></span> <span data-ttu-id="aa1b5-155">Contenu de l’élément.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="aa1b5-156">Chaque `content` peut prendre l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="aa1b5-157">Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-157">Literal text.</span></span> <span data-ttu-id="aa1b5-158">Tout l’espace blanc dans `elementContents` devient importante si n’importe quel texte littéral.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="aa1b5-159">Expression sous la forme incorporée `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="aa1b5-160">Littéral d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-160">XML element literal.</span></span>

  - <span data-ttu-id="aa1b5-161">Littéral de commentaire XML.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-161">XML comment literal.</span></span> <span data-ttu-id="aa1b5-162">Consultez [littéral de commentaire XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="aa1b5-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>

  - <span data-ttu-id="aa1b5-163">Instruction de traitement XML littéral.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-163">XML processing instruction literal.</span></span> <span data-ttu-id="aa1b5-164">Consultez [littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="aa1b5-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="aa1b5-165">Littéral CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-165">XML CDATA literal.</span></span> <span data-ttu-id="aa1b5-166">Consultez [littéral CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="aa1b5-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="aa1b5-167">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-167">Optional.</span></span> <span data-ttu-id="aa1b5-168">Représente la balise de fermeture de l’élément.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="aa1b5-169">Le paramètre facultatif `name` paramètre n’est pas autorisé lorsqu’il est le résultat d’une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="aa1b5-170">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="aa1b5-170">Return Value</span></span>

<span data-ttu-id="aa1b5-171">Objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa1b5-172">Notes</span><span class="sxs-lookup"><span data-stu-id="aa1b5-172">Remarks</span></span>

<span data-ttu-id="aa1b5-173">Vous pouvez utiliser la syntaxe de littéral d’élément XML pour créer <xref:System.Xml.Linq.XElement> objets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="aa1b5-174">Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="aa1b5-175">Cette fonctionnalité vous permet de copier le contenu d’un document XML et la coller directement dans un programme Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="aa1b5-176">Les expressions incorporées du formulaire `<%= exp %>` vous permettent d’ajouter des informations dynamiques à un littéral d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="aa1b5-177">Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="aa1b5-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="aa1b5-178">Le compilateur Visual Basic convertit le littéral d’élément XML en appels à la <xref:System.Xml.Linq.XElement.%23ctor%2A> constructeur et, si nécessaire, le <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="aa1b5-179">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="aa1b5-179">XML Namespaces</span></span>

<span data-ttu-id="aa1b5-180">Préfixes d’espace de noms XML sont utiles lorsque vous devez créer des littéraux XML avec des éléments à partir de l’espace de noms même plusieurs fois dans le code.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="aa1b5-181">Vous pouvez utiliser les préfixes d’espace de noms XML globaux, que vous définissez à l’aide de la `Imports` instruction, ou les préfixes locaux, que vous définissez à l’aide de la `xmlns:xmlPrefix="xmlNamespace"` syntaxe d’attribut.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="aa1b5-182">Pour plus d’informations, consultez [instruction Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="aa1b5-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="aa1b5-183">Conformément aux règles de portée pour les espaces de noms XML, les préfixes locaux sont prioritaires sur les préfixes globaux.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="aa1b5-184">Toutefois, si un littéral XML définit un espace de noms XML, cet espace de noms n’est pas disponible pour les expressions qui apparaissent dans une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="aa1b5-185">L’expression incorporée peut accéder uniquement l’espace de noms XML global.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="aa1b5-186">Le compilateur Visual Basic convertit chaque espace de noms XML global est utilisé par un littéral XML dans une définition d’espace de noms local dans le code généré.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="aa1b5-187">Espaces de noms XML globales qui ne sont pas utilisés n’apparaissent pas dans le code généré.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="aa1b5-188">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa1b5-188">Example</span></span>

<span data-ttu-id="aa1b5-189">L’exemple suivant montre comment créer un élément XML simple qui a deux éléments vides imbriqués.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="aa1b5-190">L’exemple affiche le texte suivant.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-190">The example displays the following text.</span></span> <span data-ttu-id="aa1b5-191">Notez que le littéral conserve la structure des éléments vides.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="aa1b5-192">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa1b5-192">Example</span></span>

<span data-ttu-id="aa1b5-193">L’exemple suivant montre comment utiliser des expressions incorporées pour nommer un élément et de créer des attributs.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="aa1b5-194">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="aa1b5-195">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa1b5-195">Example</span></span>

<span data-ttu-id="aa1b5-196">L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="aa1b5-197">Ensuite, il utilise le préfixe de l’espace de noms pour créer un littéral XML et affiche le formulaire final de l’élément.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="aa1b5-198">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="aa1b5-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="aa1b5-199">Notez que le compilateur a converti le préfixe d’espace de noms XML global dans une définition de préfixe pour l’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="aa1b5-200">Le \<ns:middle > élément redéfinit le préfixe d’espace de noms XML pour le \<ns:inner1 > élément.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="aa1b5-201">Toutefois, le \<ns:inner2 > élément utilise l’espace de noms défini par le `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="aa1b5-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa1b5-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa1b5-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="aa1b5-203">Nom des attributs et des éléments XML déclarés</span><span class="sxs-lookup"><span data-stu-id="aa1b5-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="aa1b5-204">Littéraux de commentaires XML</span><span class="sxs-lookup"><span data-stu-id="aa1b5-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="aa1b5-205">Littéral CDATA XML</span><span class="sxs-lookup"><span data-stu-id="aa1b5-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="aa1b5-206">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="aa1b5-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="aa1b5-207">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa1b5-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="aa1b5-208">Expressions incorporées en XML</span><span class="sxs-lookup"><span data-stu-id="aa1b5-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="aa1b5-209">Imports (instruction) (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="aa1b5-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
