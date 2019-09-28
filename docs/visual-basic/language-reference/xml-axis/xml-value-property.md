---
title: Propriété de valeur XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 46f81e39686da30270cd67edeb4c9f2d43e048b3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592006"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="085fc-102">Propriété de valeur XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="085fc-102">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="085fc-103">Fournit l’accès à la valeur du premier élément d’une collection d’objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="085fc-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="085fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="085fc-104">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="085fc-105">Composants</span><span class="sxs-lookup"><span data-stu-id="085fc-105">Parts</span></span>

|<span data-ttu-id="085fc-106">Terme</span><span class="sxs-lookup"><span data-stu-id="085fc-106">Term</span></span>|<span data-ttu-id="085fc-107">Définition</span><span class="sxs-lookup"><span data-stu-id="085fc-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="085fc-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="085fc-108">Required.</span></span> <span data-ttu-id="085fc-109">Collection d'objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="085fc-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="085fc-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="085fc-110">Return Value</span></span>

 <span data-ttu-id="085fc-111">@No__t-0 qui contient la valeur du premier élément de la collection, ou `Nothing` si la collection est vide.</span><span class="sxs-lookup"><span data-stu-id="085fc-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="085fc-112">Notes</span><span class="sxs-lookup"><span data-stu-id="085fc-112">Remarks</span></span>

 <span data-ttu-id="085fc-113">La propriété <xref:System.Xml.Linq.XElement.Value%2A> facilite l’accès à la valeur du premier élément d’une collection d’objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="085fc-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="085fc-114">Cette propriété vérifie d’abord si la collection contient au moins un objet.</span><span class="sxs-lookup"><span data-stu-id="085fc-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="085fc-115">Si la collection est vide, cette propriété retourne `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="085fc-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="085fc-116">Sinon, cette propriété retourne la valeur de la propriété <xref:System.Xml.Linq.XElement.Value%2A> du premier élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="085fc-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="085fc-117">Lorsque vous accédez à la valeur d’un attribut XML à l’aide de l’identificateur « \@ », la valeur de l’attribut est retournée en tant que `String` et vous n’avez pas besoin de spécifier explicitement la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="085fc-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="085fc-118">Pour accéder à d’autres éléments dans une collection, vous pouvez utiliser la propriété d’indexeur d’extension XML.</span><span class="sxs-lookup"><span data-stu-id="085fc-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="085fc-119">Pour plus d’informations, consultez [propriété d’indexeur d’extension](extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="085fc-119">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="085fc-120">Héritage</span><span class="sxs-lookup"><span data-stu-id="085fc-120">Inheritance</span></span>

 <span data-ttu-id="085fc-121">La plupart des utilisateurs n’auront pas à implémenter <xref:System.Collections.Generic.IEnumerable%601> et peuvent donc ignorer cette section.</span><span class="sxs-lookup"><span data-stu-id="085fc-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="085fc-122">La propriété <xref:System.Xml.Linq.XElement.Value%2A> est une propriété d’extension pour les types qui implémentent `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="085fc-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="085fc-123">La liaison de cette propriété d’extension est semblable à la liaison de méthodes d’extension : si un type implémente l’une des interfaces et définit une propriété qui porte le nom « value », cette propriété a la priorité sur la propriété d’extension.</span><span class="sxs-lookup"><span data-stu-id="085fc-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="085fc-124">En d’autres termes, cette propriété <xref:System.Xml.Linq.XElement.Value%2A> peut être substituée en définissant une nouvelle propriété dans une classe qui implémente `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="085fc-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="085fc-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="085fc-125">Example</span></span>

 <span data-ttu-id="085fc-126">L’exemple suivant montre comment utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour accéder au premier nœud d’une collection d’objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="085fc-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="085fc-127">L’exemple utilise la propriété d’axe enfant pour récupérer la collection de tous les nœuds enfants nommés `phone` qui se trouvent dans l’objet `contact`.</span><span class="sxs-lookup"><span data-stu-id="085fc-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="085fc-128">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="085fc-128">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="085fc-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="085fc-129">Example</span></span>

 <span data-ttu-id="085fc-130">L’exemple suivant montre comment obtenir la valeur d’un attribut XML à partir d’une collection d’objets <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="085fc-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="085fc-131">L’exemple utilise la propriété d’axe d’attribut pour afficher la valeur de l’attribut `type` pour tous les éléments `phone`.</span><span class="sxs-lookup"><span data-stu-id="085fc-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="085fc-132">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="085fc-132">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="085fc-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="085fc-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="085fc-134">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="085fc-134">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="085fc-135">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="085fc-135">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="085fc-136">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="085fc-136">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="085fc-137">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="085fc-137">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="085fc-138">Propriété d’indexeur d’extension</span><span class="sxs-lookup"><span data-stu-id="085fc-138">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="085fc-139">Propriété d’axe enfant XML</span><span class="sxs-lookup"><span data-stu-id="085fc-139">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="085fc-140">Propriété d’axe d’attribut XML</span><span class="sxs-lookup"><span data-stu-id="085fc-140">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
