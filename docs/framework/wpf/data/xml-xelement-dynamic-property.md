---
title: Xml (propriété dynamique XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Xml
ms.openlocfilehash: 9bac9797f397a0bea1dda36bf864f88293061893
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920719"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (propriété dynamique XElement)

Obtient le contenu XML sans mise en forme de l'élément.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

<xref:System.String> qui représente le contenu XML sans mise en forme de l'élément.

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> de la classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, avec le paramètre `SaveOptions` défini à la valeur <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Voir aussi

- [Propriétés dynamiques de la classe XElement](attribute-xelement-dynamic-property.md)
- [Valeur](value-xelement-dynamic-property.md)
