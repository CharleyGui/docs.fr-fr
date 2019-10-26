---
title: Element (propriété dynamique XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.openlocfilehash: fc0277d0dc38574696f01e6915e5382744345771
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920894"
---
# <a name="element-xelement-dynamic-property"></a><span data-ttu-id="b794a-102">Element (propriété dynamique XElement)</span><span class="sxs-lookup"><span data-stu-id="b794a-102">Element (XElement dynamic property)</span></span>

<span data-ttu-id="b794a-103">Obtient un indexeur utilisé pour récupérer l'instance d'élément enfant qui correspond au nom développé spécifié.</span><span class="sxs-lookup"><span data-stu-id="b794a-103">Gets an indexer used to retrieve the child element instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="b794a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b794a-104">Syntax</span></span>

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="b794a-105">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b794a-105">Property value/return value</span></span>

<span data-ttu-id="b794a-106">Indexeur de type `XElement Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="b794a-106">An indexer of the type `XElement Item(String expandedName)`.</span></span> <span data-ttu-id="b794a-107">Cet indexeur prend un paramètre de nom développé et retourne l'objet <xref:System.Xml.Linq.XElement> correspondant ou `null` s'il n'existe aucun élément avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="b794a-107">This indexer takes an expanded name parameter and returns the corresponding <xref:System.Xml.Linq.XElement>, or `null` if there is no element with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b794a-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b794a-108">Remarks</span></span>

<span data-ttu-id="b794a-109">Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Element%2A> de la classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b794a-109">This property is equivalent to <xref:System.Xml.Linq.XContainer.Element%2A> method of the <xref:System.Xml.Linq.XContainer?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b794a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b794a-110">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [<span data-ttu-id="b794a-111">Propriétés dynamiques de la classe XElement</span><span class="sxs-lookup"><span data-stu-id="b794a-111">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="b794a-112">Élements</span><span class="sxs-lookup"><span data-stu-id="b794a-112">Elements</span></span>](elements-xelement-dynamic-property.md)
