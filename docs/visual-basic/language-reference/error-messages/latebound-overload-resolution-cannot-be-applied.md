---
title: La résolution de surcharge à liaison tardive ne peut pas être appliquée à '<procedurename>', car l'instance d'accès est un type interface
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 4500a177c7a4729fe5131af1b007fd38e77afe07
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397335"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>La résolution de surcharge à liaison tardive ne peut pas être appliquée à '\<procedurename>', car l'instance d'accès est un type interface

Le compilateur tente de résoudre une référence à une propriété ou une procédure surchargée, mais la référence échoue parce qu’un argument est de type `Object` et que l’objet de référence a le type de données d’une interface. L' `Object` argument force le compilateur à résoudre la référence comme étant à liaison tardive.

Dans ces circonstances, le compilateur résout la surcharge par le biais de la classe d’implémentation plutôt que par le biais de l’interface sous-jacente. Si la classe renomme une des versions surchargées, le compilateur ne considère pas cette version comme étant une surcharge, car son nom est différent. Cela indique à son tour que le compilateur ignore la version renommée lorsqu’il peut être le bon choix pour résoudre la référence.

**ID d’erreur :** BC30933

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Utilisez `CType` pour effectuer un cast de l’argument de `Object` vers le type spécifié par la signature de la surcharge que vous souhaitez appeler.

  Notez qu’il ne permet pas d’effectuer un cast de l’objet de référence en interface sous-jacente. Vous devez effectuer un cast de l’argument pour éviter cette erreur.

## <a name="example"></a>Exemple

L’exemple suivant montre un appel à une procédure surchargée `Sub` qui provoque cette erreur au moment de la compilation.

```vb
Module m1
    Interface i1
        Sub s1(ByVal p1 As Integer)
        Sub s1(ByVal p1 As Double)
    End Interface
    Class c1
        Implements i1
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1
        End Sub
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1
        End Sub
    End Class
    Sub Main()
        Dim refer As i1 = New c1
        Dim o1 As Object = 3.1415
        ' The following reference is INVALID and causes a compiler error.
        refer.s1(o1)
    End Sub
End Module
```

Dans l’exemple précédent, si le compilateur a autorisé l’appel à `s1` comme étant écrit, la résolution a lieu via la classe `c1` au lieu de l’interface `i1` . Cela signifie que le compilateur ne tient pas compte du `s2` fait que son nom est différent dans `c1` , même s’il s’agit du bon choix, tel que défini par `i1` .

Vous pouvez corriger l’erreur en modifiant l’appel à l’une ou l’autre des lignes de code suivantes :

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

Chacune des lignes précédentes de code convertit explicitement la `Object` variable `o1` en l’un des types de paramètres définis pour les surcharges.

## <a name="see-also"></a>Voir aussi

- [Surcharge de procédure](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Résolution de surcharge](../../programming-guide/language-features/procedures/overload-resolution.md)
- [CType Function](../functions/ctype-function.md)
