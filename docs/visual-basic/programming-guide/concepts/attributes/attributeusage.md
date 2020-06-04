---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 677d49aba38801f2adf42cc745983af30b3eddc5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400730"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)

Détermine de quelle manière une classe d’attributs personnalisés peut être utilisée. `AttributeUsage` est un attribut qui peut être appliqué à des définitions d’attributs personnalisés pour contrôler le mode d’application du nouvel attribut. Voici le code quand les paramètres par défaut sont appliqués de manière explicite :

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

Dans cet exemple, la classe `NewAttribute` peut être appliquée à toutes les entités de code acceptant un attribut, mais uniquement une fois par entité. Elle est héritée par les classes dérivées quand elle est appliquée à une classe de base.

Les arguments `AllowMultiple` et `Inherited` étant facultatifs, ce code produit le même résultat :

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

Le premier argument `AttributeUsage` doit correspondre à un ou plusieurs éléments de l’énumération <xref:System.AttributeTargets>. Plusieurs types de cibles peuvent être liés avec l’opérateur OR, comme suit :

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

Si l’argument `AllowMultiple` est défini sur `true`, l’attribut qui en résulte peut être appliqué plusieurs fois à une même entité, comme suit :

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

Dans ce cas, `MultiUseAttr` peut être appliqué à plusieurs reprises, car `AllowMultiple` est défini sur `true`. Les deux formats indiqués pour appliquer plusieurs attributs sont valides.

Si `Inherited` est défini sur `false`, l’attribut n’est pas hérité par les classes qui sont dérivées d’une classe avec attributs. Par exemple :

```vb
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>
Class Attr1
    Inherits Attribute
End Class

<Attr1()>
Class BClass

End Class

Class DClass
    Inherits BClass
End Class
```

Dans ce cas, `Attr1` n’est pas appliqué à `DClass` par héritage.

## <a name="remarks"></a>Notes

L’attribut `AttributeUsage` est un attribut à usage unique : il ne peut pas être appliqué plusieurs fois à la même classe. `AttributeUsage` est un alias pour <xref:System.AttributeUsageAttribute>.

Pour plus d’informations, consultez la page [Accéder à des attributs grâce à la réflexion (Visual Basic)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Exemple

L’exemple suivant illustre l’effet des arguments `Inherited` et `AllowMultiple` sur l’attribut `AttributeUsage`, et la manière dont les attributs personnalisés appliqués à une classe peuvent être énumérés.

```vb
' Create some custom attributes:
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>
Class A1
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class)>
Class A2
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>
Class A3
    Inherits System.Attribute
End Class

' Apply custom attributes to classes:
<A1(), A2()>
Class BaseClass

End Class

<A3(), A3()>
Class DerivedClass
    Inherits BaseClass
End Class

Public Class TestAttributeUsage
    Sub Main()
        Dim b As New BaseClass
        Dim d As New DerivedClass
        ' Display custom attributes for each class.
        Console.WriteLine("Attributes on Base Class:")
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)

        For Each attr In attrs
            Console.WriteLine(attr)
        Next

        Console.WriteLine("Attributes on Derived Class:")
        attrs = d.GetType().GetCustomAttributes(True)
        For Each attr In attrs
            Console.WriteLine(attr)
        Next
    End Sub
End Class
```

## <a name="sample-output"></a>Exemple de sortie

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Guide de programmation Visual Basic](../../index.md)
- [Attributs](../../../../standard/attributes/index.md)
- [Réflexion (Visual Basic)](../reflection.md)
- [Attributs (Visual Basic)](../../../language-reference/attributes.md)
- [Créer des attributs personnalisés (Visual Basic)](creating-custom-attributes.md)
- [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](accessing-attributes-by-using-reflection.md)
