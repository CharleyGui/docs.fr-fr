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
ms.openlocfilehash: 7d76e2e7398c2f954ff4274f77ffa350efbd3617
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410745"
---
# <a name="shadowing-in-visual-basic"></a>Occultation dans Visual Basic
Lorsque deux éléments de programmation partagent le même nom, l’un d’eux peut masquer ou *occulter*l’autre. Dans ce cas, l’élément occulté n’est pas disponible à des fins de référence ; au lieu de cela, lorsque votre code utilise le nom d’élément, le compilateur Visual Basic le résout en l’élément d’occultation.  
  
## <a name="purpose"></a>Objectif  
 L’objectif principal de l’occultation est de protéger la définition de vos membres de classe. La classe de base peut subir une modification qui crée un élément avec le même nom que celui que vous avez déjà défini. Dans ce cas, le `Shadows` modificateur force les références via votre classe à être résolues vers le membre que vous avez défini, et non vers le nouvel élément de la classe de base.  
  
## <a name="types-of-shadowing"></a>Types d’occultation  
 Un élément peut occulter un autre élément de deux façons différentes. L’élément d’occultation peut être déclaré à l’intérieur d’une sous-région de la région contenant l’élément occulté, auquel cas l’occultation s’effectue *par le biais*de l’étendue. Ou une classe dérivée peut redéfinir un membre d’une classe de base, auquel cas l’occultation s’effectue *par le biais*de l’héritage.  
  
### <a name="shadowing-through-scope"></a>Occultation par portée  
 Il est possible que des éléments de programmation dans le même module, la même classe ou la même structure aient le même nom mais une portée différente. Lorsque deux éléments sont déclarés de cette manière et que le code fait référence au nom qu’ils partagent, l’élément avec la portée plus étroite occulte l’autre élément (la portée de bloc est la plus étroite).  
  
 Par exemple, un module peut définir une `Public` variable nommée `temp` , et une procédure dans le module peut déclarer une variable locale également nommée `temp` . Les références à à `temp` partir de la procédure accèdent à la variable locale, tandis que les références à `temp` depuis l’extérieur de la procédure accèdent à la `Public` variable. Dans ce cas, la variable de procédure `temp` occulte la variable de module `temp` .  
  
 L’illustration suivante montre deux variables, toutes deux nommées `temp` . La variable locale `temp` occulte la variable membre lorsqu’elle est `temp` accessible à partir de sa propre procédure `p` . Toutefois, le `MyClass` mot clé contourne l’occultation et accède à la variable membre.  
  
 ![Graphique illustrant l’occultation par le biais de l’étendue.](./media/shadowing/shadow-scope-diagram.gif)
  
 Pour obtenir un exemple d’occultation par le biais de l’étendue, consultez [Comment : masquer une variable portant le même nom que votre variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Occultation par héritage  
 Si une classe dérivée redéfinit un élément de programmation hérité d’une classe de base, l’élément redéfinissant occulte l’élément d’origine. Vous pouvez occulter tout type d’élément déclaré, ou un ensemble d’éléments surchargés, avec n’importe quel autre type. Par exemple, une `Integer` variable peut masquer une `Function` procédure. Si vous occultez une procédure à l’aide d’une autre procédure, vous pouvez utiliser une liste de paramètres différente et un type de retour différent.  
  
 L’illustration suivante montre une classe de base `b` et une classe dérivée `d` qui hérite de `b` . La classe de base définit une procédure nommée `proc` , et la classe dérivée l’occulte avec une autre procédure portant le même nom. La première `Call` instruction accède à l’occultation `proc` dans la classe dérivée. Toutefois, le `MyBase` mot clé contourne l’occultation et accède à la procédure occultée dans la classe de base.  
  
 ![Diagramme graphique d'une occultation par héritage](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Pour obtenir un exemple d’occultation par héritage, consultez [Comment : masquer une variable portant le même nom que votre variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) et [Comment : masquer une variable héritée](how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Cliché instantané et niveau d’accès  
 L’élément d’occultation n’est pas toujours accessible à partir du code à l’aide de la classe dérivée. Par exemple, il peut être déclaré `Private` . Dans ce cas, l’occultation est invalidée et le compilateur résout toute référence au même élément qu’il aurait si aucune occultation n’avait été apportée. Cet élément est l’élément accessible le moins d’étapes de dérivation à partir de la classe d’occultation. Si l’élément occulté est une procédure, la résolution est la version la plus proche accessible avec le même nom, la même liste de paramètres et le même type de retour.  
  
 L’exemple suivant montre une hiérarchie d’héritage de trois classes. Chaque classe définit une `Sub` procédure `display` , et chaque classe dérivée occulte la `display` procédure dans sa classe de base.  
  
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
  
 Dans l’exemple précédent, la classe dérivée `secondClass` occulte `display` avec une `Private` procédure. Quand `callDisplay` le module appelle `display` dans `secondClass` , le code appelant est en dehors `secondClass` de et, par conséquent, ne peut pas accéder à la procédure privée `display` . L’occultation est invalidée et le compilateur résout la référence à la procédure de classe de base `display` .  
  
 Toutefois, la classe dérivée supplémentaire `thirdClass` déclare `display` comme `Public` , donc le code de `callDisplay` peut y accéder.  
  
## <a name="shadowing-and-overriding"></a>Occultation et substitution  
 Ne confondez pas l’occultation et la substitution. Les deux sont utilisés lorsqu’une classe dérivée hérite d’une classe de base, et redéfinissent tous deux un élément déclaré avec un autre. Mais il existe des différences significatives entre les deux. Pour obtenir une comparaison, consultez [différences entre l’occultation et la substitution](differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Occultation et surcharge  
 Si vous occultez le même élément de classe de base avec plusieurs éléments dans votre classe dérivée, les éléments d’occultation deviennent des versions surchargées de cet élément. Pour plus d'informations, consultez [Procedure Overloading](../procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Accès à un élément occulté  
 Lorsque vous accédez à un élément à partir d’une classe dérivée, vous le faites normalement via l’instance actuelle de cette classe dérivée, en qualifiant le nom de l’élément avec le `Me` mot clé. Si votre classe dérivée occulte l’élément dans la classe de base, vous pouvez accéder à l’élément de classe de base en le qualifiant avec le `MyBase` mot clé.  
  
 Pour obtenir un exemple d’accès à un élément occulté, consultez [Comment : accéder à une variable masquée par une classe dérivée](how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Déclaration de la variable objet  
 La façon dont vous créez la variable objet peut également affecter si la classe dérivée accède à un élément occultant ou à l’élément occulté. L’exemple suivant crée deux objets à partir d’une classe dérivée, mais un objet est déclaré comme classe de base et l’autre comme classe dérivée.  
  
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
  
 Dans l’exemple précédent, la variable `basObj` est déclarée en tant que classe de base. L’assignation `dervCls` d’un objet à celle-ci constitue une conversion étendue et est donc valide. Toutefois, la classe de base ne peut pas accéder à la version occultante de la variable `z` dans la classe dérivée, de sorte que le compilateur se résout `basObj.z` en la valeur de la classe de base d’origine.  
  
## <a name="see-also"></a>Voir aussi

- [References to Declared Elements](references-to-declared-elements.md)
- [Portée dans Visual Basic](scope.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Remplacements](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase et MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Éléments fondamentaux de l’héritage](../objects-and-classes/inheritance-basics.md)
