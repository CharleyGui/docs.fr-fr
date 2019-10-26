---
title: Descendants (propriété dynamique XElement)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 8d14b0a94d1a2028a56f649a574f157264ba50fa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920887"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (propriété dynamique XElement)

Obtient un indexeur utilisé pour récupérer tous les éléments descendants de l’élément actif qui correspondent au nom développé spécifié.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Indexeur de type `IEnumerable<XElement> Item(String expandedName)`. Cet indexeur prend le nom développé des éléments descendants spécifiés et retourne les éléments enfants correspondants dans une collection <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> de la classe <xref:System.Xml.Linq.XContainer>.

Les éléments de la collection retournée sont spécifiés dans l’ordre du document source XML.

Cette propriété utilise l'exécution différée.

## <a name="see-also"></a>Voir aussi

- [Propriétés dynamiques de la classe XElement](attribute-xelement-dynamic-property.md)
- [Élements](elements-xelement-dynamic-property.md)
