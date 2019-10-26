---
title: Value (propriété dynamique XAttribute)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.openlocfilehash: 32c15a89a976b5f9af12f040c43e724a25357ead
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920649"
---
# <a name="value-xattribute-dynamic-property"></a>Value (propriété dynamique XAttribute)

Obtient ou définit la valeur de l'attribut XML.

## <a name="syntax"></a>Syntaxe

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

<xref:System.String> contenant la valeur de cet attribut.

## <a name="exceptions"></a>Exceptions

|Type d'exception|Condition|
| - |---------------|
|<xref:System.ArgumentNullException>|Lors de la définition, `value` a la valeur `null`.|

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la propriété <xref:System.Xml.Linq.XAttribute.Value%2A> de la classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, mais cette propriété dynamique prend également en charge les notifications de changement.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Propriétés dynamiques de la classe XAttribute](value-xattribute-dynamic-property.md)
- [Attribut](attribute-xelement-dynamic-property.md)
