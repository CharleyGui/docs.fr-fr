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
# <a name="element-xelement-dynamic-property"></a>Element (propriété dynamique XElement)

Obtient un indexeur utilisé pour récupérer l'instance d'élément enfant qui correspond au nom développé spécifié.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Indexeur de type `XElement Item(String expandedName)`. Cet indexeur prend un paramètre de nom développé et retourne l'objet <xref:System.Xml.Linq.XElement> correspondant ou `null` s'il n'existe aucun élément avec le nom spécifié.

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Element%2A> de la classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Propriétés dynamiques de la classe XElement](attribute-xelement-dynamic-property.md)
- [Élements](elements-xelement-dynamic-property.md)
