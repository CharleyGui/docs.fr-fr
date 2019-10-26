---
title: Elements (propriété dynamique XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.openlocfilehash: 812adabd3bfb01fd9313ce3f35e6cb0a5e23344e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920852"
---
# <a name="elements-xelement-dynamic-property"></a><span data-ttu-id="5b015-102">Elements (propriété dynamique XElement)</span><span class="sxs-lookup"><span data-stu-id="5b015-102">Elements (XElement dynamic property)</span></span>

<span data-ttu-id="5b015-103">Obtient un indexeur utilisé pour récupérer les éléments enfants de l’élément actif qui correspondent au nom développé spécifié.</span><span class="sxs-lookup"><span data-stu-id="5b015-103">Gets an indexer used to retrieve the child elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b015-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b015-104">Syntax</span></span>

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="5b015-105">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5b015-105">Property value/return value</span></span>

<span data-ttu-id="5b015-106">Indexeur de type `IEnumerable<XElement> Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="5b015-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="5b015-107">Cet indexeur prend le nom développé des éléments enfants souhaités et retourne les éléments enfants correspondants dans une collection <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.</span><span class="sxs-lookup"><span data-stu-id="5b015-107">This indexer takes the expanded name of the desired child elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b015-108">Notes</span><span class="sxs-lookup"><span data-stu-id="5b015-108">Remarks</span></span>

<span data-ttu-id="5b015-109">Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> de la classe <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="5b015-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="5b015-110">Les éléments de la collection retournée sont spécifiés dans l’ordre du document source XML.</span><span class="sxs-lookup"><span data-stu-id="5b015-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="5b015-111">Cette propriété utilise l'exécution différée.</span><span class="sxs-lookup"><span data-stu-id="5b015-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b015-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b015-112">See also</span></span>

- [<span data-ttu-id="5b015-113">Propriétés dynamiques de la classe XElement</span><span class="sxs-lookup"><span data-stu-id="5b015-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="5b015-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5b015-114">Element</span></span>](element-xelement-dynamic-property.md)
- [<span data-ttu-id="5b015-115">Descendants</span><span class="sxs-lookup"><span data-stu-id="5b015-115">Descendants</span></span>](descendants-xelement-dynamic-property.md)
