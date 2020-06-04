---
title: XML Descendant Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400251"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="84d77-102">Propriété d'axe descendant XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84d77-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="84d77-103">Fournit l’accès aux descendants des éléments suivants : un <xref:System.Xml.Linq.XElement> objet, un <xref:System.Xml.Linq.XDocument> objet, une collection d' <xref:System.Xml.Linq.XElement> objets ou une collection d' <xref:System.Xml.Linq.XDocument> objets.</span><span class="sxs-lookup"><span data-stu-id="84d77-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="84d77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84d77-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="84d77-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="84d77-105">Parts</span></span>

<span data-ttu-id="84d77-106">`object` Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="84d77-106">`object` Required.</span></span> <span data-ttu-id="84d77-107">Un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d’objets <xref:System.Xml.Linq.XElement> ou une collection d’objets <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="84d77-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="84d77-108">`...<` Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="84d77-108">`...<` Required.</span></span> <span data-ttu-id="84d77-109">Indique le début d’une propriété d’axe descendant.</span><span class="sxs-lookup"><span data-stu-id="84d77-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="84d77-110">`descendant` Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="84d77-110">`descendant` Required.</span></span> <span data-ttu-id="84d77-111">Nom des nœuds descendants auxquels accéder, sous la forme [ `prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="84d77-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="84d77-112">Élément</span><span class="sxs-lookup"><span data-stu-id="84d77-112">Part</span></span>|<span data-ttu-id="84d77-113">Description</span><span class="sxs-lookup"><span data-stu-id="84d77-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="84d77-114">facultatif.</span><span class="sxs-lookup"><span data-stu-id="84d77-114">Optional.</span></span> <span data-ttu-id="84d77-115">Préfixe d’espace de noms XML pour le nœud descendant.</span><span class="sxs-lookup"><span data-stu-id="84d77-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="84d77-116">Doit être un espace de noms XML global défini à l’aide d’une `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="84d77-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="84d77-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="84d77-117">Required.</span></span> <span data-ttu-id="84d77-118">Nom local du nœud descendant.</span><span class="sxs-lookup"><span data-stu-id="84d77-118">Local name of the descendant node.</span></span> <span data-ttu-id="84d77-119">Consultez [les noms des éléments et attributs XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="84d77-119">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="84d77-120">`>` Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="84d77-120">`>` Required.</span></span> <span data-ttu-id="84d77-121">Indique la fin d’une propriété d’axe descendant.</span><span class="sxs-lookup"><span data-stu-id="84d77-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="84d77-122">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="84d77-122">Return Value</span></span>

<span data-ttu-id="84d77-123">Collection d’objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="84d77-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="84d77-124">Notes</span><span class="sxs-lookup"><span data-stu-id="84d77-124">Remarks</span></span>

<span data-ttu-id="84d77-125">Vous pouvez utiliser une propriété d’axe descendant XML pour accéder aux nœuds descendants par nom à partir d’un <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objet ou, ou d’une collection d' <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objets ou.</span><span class="sxs-lookup"><span data-stu-id="84d77-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="84d77-126">Utilisez la `Value` propriété XML pour accéder à la valeur du premier nœud descendant dans la collection retournée.</span><span class="sxs-lookup"><span data-stu-id="84d77-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="84d77-127">Pour plus d’informations, consultez [propriété de valeur XML](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="84d77-127">For more information, see [XML Value Property](xml-value-property.md).</span></span>

<span data-ttu-id="84d77-128">Le compilateur Visual Basic convertit les propriétés de l’axe descendant en appels à la <xref:System.Xml.Linq.XContainer.Descendants%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="84d77-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="84d77-129">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="84d77-129">XML Namespaces</span></span>

<span data-ttu-id="84d77-130">Le nom dans une propriété d’axe descendante ne peut utiliser que des espaces de noms XML déclarés globalement avec l' `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="84d77-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="84d77-131">Elle ne peut pas utiliser les espaces de noms XML déclarés localement dans des littéraux d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="84d77-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="84d77-132">Pour plus d’informations, consultez [instructions Imports (espace de noms XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="84d77-132">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="84d77-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="84d77-133">Example</span></span>

<span data-ttu-id="84d77-134">L’exemple suivant montre comment accéder à la valeur du premier nœud descendant nommé `name` et aux valeurs de tous les nœuds descendants nommés `phone` à partir de l' `contacts` objet.</span><span class="sxs-lookup"><span data-stu-id="84d77-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="84d77-135">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="84d77-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="84d77-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="84d77-136">Example</span></span>

<span data-ttu-id="84d77-137">L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="84d77-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="84d77-138">Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder à la valeur du premier nœud enfant avec le nom qualifié `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="84d77-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="84d77-139">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="84d77-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="84d77-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84d77-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="84d77-141">Propriétés d'axe XML</span><span class="sxs-lookup"><span data-stu-id="84d77-141">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="84d77-142">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="84d77-142">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="84d77-143">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84d77-143">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="84d77-144">Nom des attributs et des éléments XML déclarés</span><span class="sxs-lookup"><span data-stu-id="84d77-144">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
