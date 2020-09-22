---
title: XML Attribute Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 9eddd132b2d4dd6ffbd935a0c8c57a03a3d65435
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869443"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="1b615-102">Propriété d'axe d'attribut XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b615-102">XML Attribute Axis Property (Visual Basic)</span></span>

<span data-ttu-id="1b615-103">Fournit l’accès à la valeur d’un attribut pour un <xref:System.Xml.Linq.XElement> objet ou au premier élément d’une collection d' <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="1b615-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b615-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b615-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="1b615-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="1b615-105">Parts</span></span>  

 `object`  
 <span data-ttu-id="1b615-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1b615-106">Required.</span></span> <span data-ttu-id="1b615-107">Un <xref:System.Xml.Linq.XElement> objet ou une collection d' <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="1b615-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="1b615-108">.@</span><span class="sxs-lookup"><span data-stu-id="1b615-108">.@</span></span>  
 <span data-ttu-id="1b615-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1b615-109">Required.</span></span> <span data-ttu-id="1b615-110">Indique le début d’une propriété d’axe d’attribut.</span><span class="sxs-lookup"><span data-stu-id="1b615-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="1b615-111">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="1b615-111">Optional.</span></span> <span data-ttu-id="1b615-112">Indique le début du nom de l’attribut lorsque `attribute` n’est pas un identificateur valide dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b615-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="1b615-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1b615-113">Required.</span></span> <span data-ttu-id="1b615-114">Nom de l’attribut auquel accéder, sous la forme [ `prefix` :] `name` .</span><span class="sxs-lookup"><span data-stu-id="1b615-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="1b615-115">Élément</span><span class="sxs-lookup"><span data-stu-id="1b615-115">Part</span></span>|<span data-ttu-id="1b615-116">Description</span><span class="sxs-lookup"><span data-stu-id="1b615-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="1b615-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="1b615-117">Optional.</span></span> <span data-ttu-id="1b615-118">Préfixe d’espace de noms XML pour l’attribut.</span><span class="sxs-lookup"><span data-stu-id="1b615-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="1b615-119">Doit être un espace de noms XML global défini avec une instruction `Imports`.</span><span class="sxs-lookup"><span data-stu-id="1b615-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="1b615-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1b615-120">Required.</span></span> <span data-ttu-id="1b615-121">Nom de l’attribut local.</span><span class="sxs-lookup"><span data-stu-id="1b615-121">Local attribute name.</span></span> <span data-ttu-id="1b615-122">Consultez [les noms des éléments et attributs XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1b615-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="1b615-123">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="1b615-123">Optional.</span></span> <span data-ttu-id="1b615-124">Indique la fin du nom de l’attribut lorsque `attribute` n’est pas un identificateur valide dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b615-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b615-125">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1b615-125">Return Value</span></span>  

 <span data-ttu-id="1b615-126">Chaîne qui contient la valeur de `attribute` .</span><span class="sxs-lookup"><span data-stu-id="1b615-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="1b615-127">Si le nom de l’attribut n’existe pas, `Nothing` est retourné.</span><span class="sxs-lookup"><span data-stu-id="1b615-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b615-128">Notes</span><span class="sxs-lookup"><span data-stu-id="1b615-128">Remarks</span></span>  

 <span data-ttu-id="1b615-129">Vous pouvez utiliser une propriété d’axe d’attribut XML pour accéder à la valeur d’un attribut par nom à partir d’un <xref:System.Xml.Linq.XElement> objet ou à partir du premier élément d’une collection d' <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="1b615-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="1b615-130">Vous pouvez récupérer une valeur d’attribut par nom ou ajouter un nouvel attribut à un élément en spécifiant un nouveau nom précédé de l’identificateur @.</span><span class="sxs-lookup"><span data-stu-id="1b615-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="1b615-131">Quand vous faites référence à un attribut XML à l’aide de l’identificateur @, la valeur de l’attribut est retournée sous forme de chaîne et vous n’avez pas besoin de spécifier explicitement la <xref:System.Xml.Linq.XAttribute.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="1b615-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="1b615-132">Les règles d’affectation de noms pour les attributs XML diffèrent des règles d’affectation de noms pour les identificateurs de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b615-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="1b615-133">Pour accéder à un attribut XML dont le nom n’est pas un identificateur de Visual Basic valide, mettez le nom entre crochets pointus ( \< and > ).</span><span class="sxs-lookup"><span data-stu-id="1b615-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="1b615-134">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="1b615-134">XML Namespaces</span></span>  

 <span data-ttu-id="1b615-135">Le nom dans une propriété d’axe d’attribut ne peut utiliser que des préfixes d’espaces de noms XML déclarés globalement à l’aide de l' `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="1b615-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="1b615-136">Il ne peut pas utiliser des préfixes d'espace de noms XML déclarés localement dans des littéraux d'éléments XML.</span><span class="sxs-lookup"><span data-stu-id="1b615-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="1b615-137">Pour plus d’informations, consultez [instructions Imports (espace de noms XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1b615-137">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b615-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b615-138">Example</span></span>  

 <span data-ttu-id="1b615-139">L’exemple suivant montre comment obtenir les valeurs des attributs XML nommés `type` à partir d’une collection d’éléments XML nommés `phone` .</span><span class="sxs-lookup"><span data-stu-id="1b615-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="1b615-140">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="1b615-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="1b615-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b615-141">Example</span></span>  

 <span data-ttu-id="1b615-142">L’exemple suivant montre comment créer des attributs pour un élément XML de manière déclarative, dans le cadre du XML, et de manière dynamique en ajoutant un attribut à une instance d’un <xref:System.Xml.Linq.XElement> objet.</span><span class="sxs-lookup"><span data-stu-id="1b615-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="1b615-143">L' `type` attribut est créé de manière déclarative et l' `owner` attribut est créé dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="1b615-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="1b615-144">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="1b615-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="1b615-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b615-145">Example</span></span>  

 <span data-ttu-id="1b615-146">L’exemple suivant utilise la syntaxe du Chevron pour obtenir la valeur de l’attribut XML nommé `number-type` , qui n’est pas un identificateur valide dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b615-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="1b615-147">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="1b615-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="1b615-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="1b615-148">Example</span></span>  

 <span data-ttu-id="1b615-149">L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="1b615-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="1b615-150">Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié « `ns:name` ».</span><span class="sxs-lookup"><span data-stu-id="1b615-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="1b615-151">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="1b615-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="1b615-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b615-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="1b615-153">Propriétés d'axe XML</span><span class="sxs-lookup"><span data-stu-id="1b615-153">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="1b615-154">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="1b615-154">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="1b615-155">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1b615-155">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="1b615-156">Nom des attributs et des éléments XML déclarés</span><span class="sxs-lookup"><span data-stu-id="1b615-156">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
