---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61668716"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Détermine de quelle manière une classe d’attributs personnalisés peut être utilisée. <xref:System.AttributeUsageAttribute> est un attribut que vous appliquez à des définitions d’attribut personnalisé. L’attribut `AttributeUsage` vous permet de contrôler :

- À quels éléments de programme les attributs peuvent être appliqués. Sauf si vous en limitez l’utilisation, un attribut peut être appliqué aux éléments de programme suivants :
  - assembly
  - module
  - field
  - événement
  - method
  - param
  - propriété
  - return
  - type
- Si un attribut peut être appliqué plusieurs fois à un même élément de programme.
- Si les attributs sont hérités dans les classes dérivées.

L’exemple suivant montre des paramètres par défaut quand ils sont appliqués explicitement :

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

Dans cet exemple, la classe `NewAttribute` peut être appliquée à n’importe quel élément de programme pris en charge. Elle ne peut cependant être appliquée qu’une seule fois à chaque entité. L’attribut est hérité par les classes dérivées quand il est appliqué à une classe de base.

Les arguments <xref:System.AttributeUsageAttribute.AllowMultiple> et <xref:System.AttributeUsageAttribute.Inherited> étant facultatifs, le code suivant a le même effet :

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

Le premier argument <xref:System.AttributeUsageAttribute> doit correspondre à un ou plusieurs éléments de l’énumération <xref:System.AttributeTargets>. Vous pouvez lier ensemble plusieurs types de cibles avec l’opérateur OR, comme dans l’exemple suivant :

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

À compter de C# 7.3, les attributs peuvent être appliqués à la propriété ou au champ de stockage pour une propriété implémentée automatiquement. L’attribut s’applique à la propriété, sauf si vous spécifiez le spécificateur `field` sur l’attribut. Les deux cas sont illustrés dans l’exemple suivant :

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Si l’argument <xref:System.AttributeUsageAttribute.AllowMultiple> est défini sur `true`, l’attribut résultant peut être appliqué plusieurs fois à une même entité, comme illustré dans l’exemple suivant :

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

Dans ce cas, `MultiUseAttribute` peut être appliqué à plusieurs reprises, car `AllowMultiple` est défini sur `true`. Les deux formats indiqués pour appliquer plusieurs attributs sont valides.

Si <xref:System.AttributeUsageAttribute.Inherited> est `false`, l’attribut n’est pas hérité par les classes dérivées d’une classe avec attributs. Par exemple :

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

Dans ce cas, `NonInheritedAttribute` n’est pas appliqué à `DClass` via l’héritage.

## <a name="remarks"></a>Notes 

L’attribut `AttributeUsage` est un attribut à usage unique : il ne peut pas être appliqué plusieurs fois à la même classe. `AttributeUsage` est un alias pour <xref:System.AttributeUsageAttribute>.

Pour plus d’informations, consultez [Accès à des attributs à l’aide de la réflexion (C#)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a> Exemple

L’exemple suivant illustre l’effet des arguments <xref:System.AttributeUsageAttribute.Inherited> et <xref:System.AttributeUsageAttribute.AllowMultiple> sur l’attribut <xref:System.AttributeUsageAttribute>, et la manière dont les attributs personnalisés appliqués à une classe peuvent être énumérés.

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a>Exemple de sortie

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Guide de programmation C#](../..//index.md)
- [Attributs](../../../..//standard/attributes/index.md)
- [Réflexion (C#)](../reflection.md)
- [Attributs](index.md)
- [Création d’attributs personnalisés (C#)](creating-custom-attributes.md)
- [Accès à des attributs à l’aide de la réflexion (C#)](accessing-attributes-by-using-reflection.md)
