---
title: Copie shadow
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266883"
---
# <a name="shadowing-in-visual-basic"></a>Occultation dans Visual Basic
Lorsque deux éléments de programmation partagent le même nom, l’un d’eux peut se cacher, ou *l’ombre*, l’autre. Dans une telle situation, l’élément ombragé n’est pas disponible pour référence; au lieu de cela, lorsque votre code utilise le nom de l’élément, le compilateur Visual Basic le résout à l’élément d’observation.  
  
## <a name="purpose"></a>Objectif  
 Le but principal de l’ombre est de protéger la définition des membres de votre classe. La classe de base peut subir un changement qui crée un élément avec le même nom que celui que vous avez déjà défini. Si cela se `Shadows` produit, le modificateur force les références à travers votre classe à être résolues au membre que vous avez défini, au lieu du nouvel élément de classe de base.  
  
## <a name="types-of-shadowing"></a>Types d’ombre  
 Un élément peut ombrer un autre élément de deux façons différentes. L’élément d’ombre peut être déclaré à l’intérieur d’une sous-région de la région contenant l’élément ombragé, auquel cas l’ombre est accomplie *par la portée*. Ou une classe de dériving peut redéfinir un membre d’une classe de base, auquel cas l’ombre se fait *par l’héritage*.  
  
### <a name="shadowing-through-scope"></a>Ombre à travers la portée  
 Il est possible que les éléments de programmation d’un même module, d’une même classe ou d’une même structure aient le même nom mais une portée différente. Lorsque deux éléments sont déclarés de cette manière et que le code fait référence au nom qu’ils partagent, l’élément avec la portée plus étroite ombre l’autre élément (la portée de bloc est la plus étroite).  
  
 Par exemple, un module `Public` peut `temp`définir une variable nommée , et une `temp`procédure au sein du module peut déclarer une variable locale également nommée . Les `temp` références à partir de l’intérieur `temp` de la procédure `Public` accèdent à la variable locale, tandis que les références à partir de l’extérieur de la procédure accèdent à la variable. Dans ce cas, `temp` la variable de `temp`procédure ombres de la variable du module .  
  
 L’illustration suivante montre deux `temp`variables, toutes deux nommées . La variable `temp` locale ombre `temp` la variable du membre `p`lorsqu’elle est accessible à partir de sa propre procédure . Cependant, `MyClass` le mot clé contourne l’ombre et accède à la variable du membre.  
  
 ![Graphique qui montre l’ombre à travers la portée.](./media/shadowing/shadow-scope-diagram.gif)
  
 Pour un exemple d’ombre à travers la portée, voir [Comment: Cacher une variable avec le même nom que votre variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Ombre par l’héritage  
 Si une classe dérivée redéfinit un élément de programmation hérité d’une classe de base, l’élément de redéfinition ombre l’élément original. Vous pouvez suivre n’importe quel type d’élément déclaré, ou ensemble d’éléments surchargés, avec n’importe quel autre type. Par exemple, `Integer` une variable `Function` peut ombrer une procédure. Si vous faites de l’ombre à une procédure avec une autre procédure, vous pouvez utiliser une liste de paramètres différente et un type de retour différent.  
  
 L’illustration suivante montre `b` une classe `d` de base `b`et une classe dérivée qui hérite de . La classe de base `proc`définit une procédure nommée , et la classe dérivée l’ombre avec une autre procédure du même nom. La `Call` première déclaration accède `proc` à l’ombre dans la classe dérivée. Cependant, `MyBase` le mot clé contourne l’ombre et accède à la procédure ombragée dans la classe de base.  
  
 ![Diagramme graphique d'une occultation par héritage](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Par exemple de l’ombre à travers l’héritage, voir [Comment: Cacher une variable avec le même nom que votre variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) et [comment: Cacher une variable héritée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Niveau d’ombre et d’accès  
 L’élément d’ombre n’est pas toujours accessible à partir du code à l’aide de la classe dérivée. Par exemple, il `Private`peut être déclaré . Dans un tel cas, l’ombre est vaincue et le compilateur résout toute référence au même élément qu’il aurait si il n’y avait pas eu d’ombre. Cet élément est l’élément accessible le moins de pas dérivationnels en arrière de la classe d’ombre. Si l’élément ombragé est une procédure, la résolution est à la version la plus proche accessible avec le même nom, la liste de paramètres, et le type de retour.  
  
 L’exemple suivant montre une hiérarchie successorale de trois classes. Chaque classe définit `Sub` `display`une procédure, et chaque `display` classe dérivée ombre la procédure dans sa classe de base.  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 Dans l’exemple précédent, `secondClass` la `display` classe `Private` dérivée s’ombre à une procédure. Lorsque `callDisplay` le `display` `secondClass`module appelle, le `secondClass` code d’appel `display` est à l’extérieur et ne peut donc pas accéder à la procédure privée. L’ombre est vaincue, et le compilateur `display` résout la référence à la procédure de classe de base.  
  
 Cependant, la classe `thirdClass` dérivée `Public`plus loin `callDisplay` déclare `display` comme , de sorte que le code dans peut y accéder.  
  
## <a name="shadowing-and-overriding"></a>Ombre et prépondérer  
 Ne confondez pas l’ombre avec le prépondérer. Les deux sont utilisés lorsqu’une classe dérivée d’une classe de base, et les deux redéfinissent un élément déclaré avec un autre. Mais il y a des différences significatives entre les deux. Pour une comparaison, voir [Différences entre l’ombre et l’avant](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Ombre et surcharge  
 Si vous ombrez le même élément de classe de base avec plus d’un élément dans votre classe dérivée, les éléments d’ombre deviennent des versions surchargées de cet élément. Pour plus d'informations, consultez [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Accès à un élément ombragé  
 Lorsque vous accédez à un élément d’une classe dérivée, vous le faites normalement `Me` à travers l’instance actuelle de cette catégorie dérivée, en qualifiant le nom de l’élément avec le mot clé. Si votre classe dérivée ombre l’élément dans la classe de base, `MyBase` vous pouvez accéder à l’élément de classe de base en le qualifiant avec le mot clé.  
  
 Par exemple d’accès à un élément ombragé, voir [Comment : Accéder à une variable cachée par une classe dérivée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Déclaration de la variable d’objet  
 La façon dont vous créez la variable d’objet peut également affecter si la classe dérivée accède à un élément d’ombre ou à l’élément ombragé. L’exemple suivant crée deux objets d’une classe dérivée, mais un objet est déclaré comme la classe de base et l’autre comme la classe dérivée.  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 Dans l’exemple précédent, la variable `basObj` est déclarée classe de base. L’attribution `dervCls` d’un objet constitue une conversion croissante et est donc valide. Cependant, la classe de base ne peut `z` pas accéder à la version d’ombre de la variable dans la classe dérivée, de sorte que le compilateur se résout `basObj.z` à la valeur de la classe de base d’origine.  
  
## <a name="see-also"></a>Voir aussi

- [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Remplace](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Éléments fondamentaux de l’héritage](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
