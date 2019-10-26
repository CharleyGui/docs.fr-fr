---
title: Attribute (propriété dynamique XElement)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 2b645575a5b6876ffbb52a999c4e05a2de037493
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920915"
---
# <a name="attribute-xelement-dynamic-property"></a><span data-ttu-id="9ca55-102">Attribute (propriété dynamique XElement)</span><span class="sxs-lookup"><span data-stu-id="9ca55-102">Attribute (XElement dynamic property)</span></span>

<span data-ttu-id="9ca55-103">Obtient un indexeur utilisé pour récupérer l'instance d'attribut qui correspond au nom développé spécifié.</span><span class="sxs-lookup"><span data-stu-id="9ca55-103">Gets an indexer used to retrieve the attribute instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ca55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ca55-104">Syntax</span></span>

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="9ca55-105">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9ca55-105">Property value/return value</span></span>

<span data-ttu-id="9ca55-106">Indexeur de type `XAttribute Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="9ca55-106">An indexer of the type `XAttribute Item(String expandedName)`.</span></span> <span data-ttu-id="9ca55-107">Cet indexeur prend le nom développé de l'attribut spécifié et retourne l'objet <xref:System.Xml.Linq.XAttribute> correspondant ou `null` s'il n'existe aucun attribut avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="9ca55-107">This indexer takes the expanded name of the specified attribute and returns the corresponding <xref:System.Xml.Linq.XAttribute>, or `null` if there is no attribute with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ca55-108">Notes</span><span class="sxs-lookup"><span data-stu-id="9ca55-108">Remarks</span></span>

<span data-ttu-id="9ca55-109">Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="9ca55-109">This property is equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ca55-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ca55-110">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [<span data-ttu-id="9ca55-111">Propriétés dynamiques de la classe XElement</span><span class="sxs-lookup"><span data-stu-id="9ca55-111">XElement Class Dynamic Properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="9ca55-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="9ca55-112">Value</span></span>](value-xattribute-dynamic-property.md)
