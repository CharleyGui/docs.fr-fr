---
title: Propriété d’indexeur d’extension
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 5f91dc8a6b1a0d82daa4891cf826c16e2716839f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352698"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="816be-102">Propriété d’indexeur d’extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="816be-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="816be-103">Fournit un accès aux différents éléments d'une collection.</span><span class="sxs-lookup"><span data-stu-id="816be-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="816be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="816be-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="816be-105">Composants</span><span class="sxs-lookup"><span data-stu-id="816be-105">Parts</span></span>  
  
|<span data-ttu-id="816be-106">Terme</span><span class="sxs-lookup"><span data-stu-id="816be-106">Term</span></span>|<span data-ttu-id="816be-107">Définition</span><span class="sxs-lookup"><span data-stu-id="816be-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="816be-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="816be-108">Required.</span></span> <span data-ttu-id="816be-109">Collection interrogeable.</span><span class="sxs-lookup"><span data-stu-id="816be-109">A queryable collection.</span></span> <span data-ttu-id="816be-110">Autrement dit, une collection qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="816be-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="816be-111">(</span><span class="sxs-lookup"><span data-stu-id="816be-111">(</span></span>|<span data-ttu-id="816be-112">Requis.</span><span class="sxs-lookup"><span data-stu-id="816be-112">Required.</span></span> <span data-ttu-id="816be-113">Indique le début de la propriété de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="816be-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="816be-114">Requis.</span><span class="sxs-lookup"><span data-stu-id="816be-114">Required.</span></span> <span data-ttu-id="816be-115">Expression entière qui spécifie la position de base zéro d’un élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="816be-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="816be-116">)</span><span class="sxs-lookup"><span data-stu-id="816be-116">)</span></span>|<span data-ttu-id="816be-117">Requis.</span><span class="sxs-lookup"><span data-stu-id="816be-117">Required.</span></span> <span data-ttu-id="816be-118">Indique la fin de la propriété de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="816be-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="816be-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="816be-119">Return Value</span></span>  
 <span data-ttu-id="816be-120">Objet à partir de l’emplacement spécifié dans la collection, ou `Nothing` si l’index est hors limites.</span><span class="sxs-lookup"><span data-stu-id="816be-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="816be-121">Notes</span><span class="sxs-lookup"><span data-stu-id="816be-121">Remarks</span></span>  
 <span data-ttu-id="816be-122">Vous pouvez utiliser la propriété d’indexeur d’extension pour accéder à des éléments individuels dans une collection.</span><span class="sxs-lookup"><span data-stu-id="816be-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="816be-123">Cette propriété d’indexeur est généralement utilisée sur la sortie des propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="816be-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="816be-124">Les propriétés de l’axe de descendant XML et de l’enfant XML retournent des collections d’objets <xref:System.Xml.Linq.XElement> ou une valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="816be-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="816be-125">Le compilateur Visual Basic convertit les propriétés d’indexeur d’extension en appels à la méthode `ElementAtOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="816be-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="816be-126">Contrairement à un indexeur de tableau, la méthode `ElementAtOrDefault` retourne `Nothing` si l’index est hors limites.</span><span class="sxs-lookup"><span data-stu-id="816be-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="816be-127">Ce comportement est utile lorsque vous ne pouvez pas déterminer facilement le nombre d’éléments d’une collection.</span><span class="sxs-lookup"><span data-stu-id="816be-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="816be-128">Cette propriété d’indexeur est semblable à une propriété d’extension pour les collections qui implémentent <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>: elle est utilisée uniquement si la collection n’a pas d’indexeur ou de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="816be-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="816be-129">Pour accéder à la valeur du premier élément d’une collection d’objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous pouvez utiliser la propriété XML `Value`.</span><span class="sxs-lookup"><span data-stu-id="816be-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="816be-130">Pour plus d’informations, consultez [propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="816be-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="816be-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="816be-131">Example</span></span>  
 <span data-ttu-id="816be-132">L’exemple suivant montre comment utiliser l’indexeur d’extension pour accéder au deuxième nœud enfant d’une collection d’objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="816be-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="816be-133">La collection est accessible à l’aide de la propriété d’axe enfant, qui obtient tous les éléments enfants nommés `phone` dans l’objet `contact`.</span><span class="sxs-lookup"><span data-stu-id="816be-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="816be-134">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="816be-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="816be-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="816be-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="816be-136">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="816be-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="816be-137">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="816be-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="816be-138">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="816be-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="816be-139">Propriété de valeur XML</span><span class="sxs-lookup"><span data-stu-id="816be-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
