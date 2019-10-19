---
title: Instruction Imports-espace de noms XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 0fca0caecfd69580510a539317856209108e5a32
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581768"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="26e09-102">Imports, instruction (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="26e09-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="26e09-103">Importe les préfixes d’espaces de noms XML à utiliser dans les littéraux XML et les propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="26e09-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="26e09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26e09-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="26e09-105">Composants</span><span class="sxs-lookup"><span data-stu-id="26e09-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="26e09-106">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="26e09-106">Optional.</span></span> <span data-ttu-id="26e09-107">Chaîne par laquelle les éléments et attributs XML peuvent faire référence à `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="26e09-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="26e09-108">Si aucun `xmlNamespacePrefix` n’est fourni, l’espace de noms XML importé est l’espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="26e09-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="26e09-109">Doit être un identificateur XML valide.</span><span class="sxs-lookup"><span data-stu-id="26e09-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="26e09-110">Pour plus d’informations, consultez [noms des éléments et attributs XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="26e09-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="26e09-111">Requis.</span><span class="sxs-lookup"><span data-stu-id="26e09-111">Required.</span></span> <span data-ttu-id="26e09-112">Chaîne identifiant l’espace de noms XML importé.</span><span class="sxs-lookup"><span data-stu-id="26e09-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="26e09-113">Notes</span><span class="sxs-lookup"><span data-stu-id="26e09-113">Remarks</span></span>

<span data-ttu-id="26e09-114">Vous pouvez utiliser l’instruction `Imports` pour définir des espaces de noms XML globaux que vous pouvez utiliser avec des littéraux XML et des propriétés d’axe XML, ou en tant que paramètres passés à l’opérateur `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="26e09-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="26e09-115">(Pour plus d’informations sur l’utilisation de l’instruction `Imports` pour importer un alias qui peut être utilisé lorsque des noms de types sont utilisés dans votre code, consultez [instructions Imports (espace de noms et type .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) La syntaxe permettant de déclarer un espace de noms XML à l’aide de l’instruction `Imports` est identique à la syntaxe utilisée dans XML.</span><span class="sxs-lookup"><span data-stu-id="26e09-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="26e09-116">Par conséquent, vous pouvez copier une déclaration d’espace de noms à partir d’un fichier XML et l’utiliser dans une instruction `Imports`.</span><span class="sxs-lookup"><span data-stu-id="26e09-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="26e09-117">Les préfixes d’espaces de noms XML sont utiles lorsque vous souhaitez créer plusieurs éléments XML à partir du même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="26e09-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="26e09-118">Le préfixe d’espace de noms XML déclaré avec l’instruction `Imports` est global dans le sens où il est disponible pour l’ensemble du code du fichier.</span><span class="sxs-lookup"><span data-stu-id="26e09-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="26e09-119">Vous pouvez l’utiliser lorsque vous créez des littéraux d’élément XML et lorsque vous accédez à des propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="26e09-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="26e09-120">Pour plus d’informations, consultez [littéraux d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="26e09-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>

<span data-ttu-id="26e09-121">Si vous définissez un espace de noms XML global sans préfixe d’espace de noms (par exemple, `Imports <xmlns="http://SomeNameSpace>"`), cet espace de noms est considéré comme l’espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="26e09-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="26e09-122">L’espace de noms XML par défaut est utilisé pour les littéraux d’élément XML ou les propriétés d’axe d’attribut XML qui ne spécifient pas explicitement un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="26e09-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="26e09-123">L’espace de noms par défaut est également utilisé si l’espace de noms spécifié est l’espace de noms vide (autrement dit, `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="26e09-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="26e09-124">L’espace de noms XML par défaut ne s’applique pas aux attributs XML des littéraux XML ou aux propriétés d’axe d’attribut XML qui n’ont pas d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="26e09-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="26e09-125">Les espaces de noms XML définis dans un littéral XML, appelés espaces de *noms XML locaux*, ont la priorité sur les espaces de noms XML définis par l’instruction `Imports` comme global.</span><span class="sxs-lookup"><span data-stu-id="26e09-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="26e09-126">Les espaces de noms XML définis par l’instruction `Imports` sont prioritaires sur les espaces de noms XML importés pour un projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="26e09-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="26e09-127">Si un littéral XML définit un espace de noms XML, cet espace de noms local ne s’applique pas aux expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="26e09-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="26e09-128">Les espaces de noms XML globaux suivent les mêmes règles d’étendue et de définition que les espaces de noms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="26e09-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="26e09-129">Par conséquent, vous pouvez inclure une instruction `Imports` pour définir un espace de noms XML global partout où vous pouvez importer un espace de noms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="26e09-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="26e09-130">Cela comprend à la fois les fichiers de code et les espaces de noms importés au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="26e09-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="26e09-131">Pour plus d’informations sur les espaces de noms importés au niveau du projet, consultez la [page références, concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="26e09-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="26e09-132">Chaque fichier source peut contenir un nombre quelconque d’instructions `Imports`.</span><span class="sxs-lookup"><span data-stu-id="26e09-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="26e09-133">Celles-ci doivent suivre les déclarations d’option, telles que l’instruction `Option Strict`, et elles doivent précéder les déclarations d’éléments de programmation, telles que les instructions `Module` ou `Class`.</span><span class="sxs-lookup"><span data-stu-id="26e09-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="26e09-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="26e09-134">Example</span></span>

<span data-ttu-id="26e09-135">L’exemple suivant importe un espace de noms XML par défaut et un espace de noms XML identifié par le préfixe `ns`.</span><span class="sxs-lookup"><span data-stu-id="26e09-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="26e09-136">Il crée ensuite des littéraux XML qui utilisent les deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="26e09-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="26e09-137">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="26e09-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="26e09-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="26e09-138">Example</span></span>

<span data-ttu-id="26e09-139">L’exemple suivant importe le préfixe d’espace de noms XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="26e09-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="26e09-140">Il crée ensuite un littéral XML qui utilise le préfixe d’espace de noms et affiche le formulaire final de l’élément.</span><span class="sxs-lookup"><span data-stu-id="26e09-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="26e09-141">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="26e09-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="26e09-142">Notez que le compilateur a converti le préfixe d’espace de noms XML d’un préfixe global en définition de préfixe local.</span><span class="sxs-lookup"><span data-stu-id="26e09-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="26e09-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="26e09-143">Example</span></span>

<span data-ttu-id="26e09-144">L’exemple suivant importe le préfixe d’espace de noms XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="26e09-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="26e09-145">Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="26e09-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="26e09-146">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="26e09-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="26e09-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26e09-147">See also</span></span>

- [<span data-ttu-id="26e09-148">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="26e09-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="26e09-149">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="26e09-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="26e09-150">Nom des attributs et des éléments XML déclarés</span><span class="sxs-lookup"><span data-stu-id="26e09-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="26e09-151">GetXmlNamespace (opérateur)</span><span class="sxs-lookup"><span data-stu-id="26e09-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
