---
title: 'Comment : masquer une variable portant le même nom que votre variable'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: c1f4c2fbf339358be77e76468b1db94616bf04a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357230"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Comment : masquer une variable portant le même nom que votre variable (Visual Basic)

Vous pouvez masquer une variable en l' *occultant* , c’est-à-dire en la redéfinissant avec une variable du même nom. Vous pouvez occulter la variable que vous souhaitez masquer de deux manières :

- **Occultation par le biais de l’étendue.** Vous pouvez l’occulter par le biais de la portée en le redéclarant dans une sous-région de la région contenant la variable que vous souhaitez masquer.

- **Occultation par héritage.** Si la variable que vous souhaitez masquer est définie au niveau de la classe, vous pouvez l’occulter via l’héritage en la redéclarant avec le mot clé [Shadows](../../../language-reference/modifiers/shadows.md) dans une classe dérivée.

## <a name="two-ways-to-hide-a-variable"></a>Deux façons de masquer une variable

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Pour masquer une variable en l’occultant par l’intermédiaire de la portée

1. Déterminez la région définissant la variable que vous souhaitez masquer et déterminez une sous-région dans laquelle la redéfinir avec votre variable.

    |Région de la variable|Sous-région autorisée pour la redéfinition|
    |-----------------------|-------------------------------------------|
    |Module|Une classe dans le module|
    |Class|Une sous-classe dans la classe<br /><br /> Une procédure dans la classe|

    Vous ne pouvez pas redéfinir une variable de procédure dans un bloc au sein de cette procédure, par exemple dans une `If` construction... `End If` ou une `For` boucle.

2. Créez la sous-région si elle n’existe pas déjà.

3. Dans la sous-région, écrivez une [instruction Dim](../../../language-reference/statements/dim-statement.md) qui déclare la variable d’occultation.

    Lorsque le code à l’intérieur de la sous-région fait référence au nom de la variable, le compilateur résout la référence à la variable d’occultation.

    L’exemple suivant illustre l’occultation par le biais de l’étendue, ainsi qu’une référence qui contourne l’occultation.

    ```vb
    Module shadowByScope
        ' The following statement declares num as a module-level variable.
        Public num As Integer
        Sub show()
            ' The following statement declares num as a local variable.
            Dim num As Integer
            ' The following statement sets the value of the local variable.
            num = 2
            ' The following statement displays the module-level variable.
            MsgBox(CStr(shadowByScope.num))
        End Sub
        Sub useModuleLevelNum()
            ' The following statement sets the value of the module-level variable.
            num = 1
            show()
        End Sub
    End Module
    ```

    L’exemple précédent déclare la variable `num` à la fois au niveau du module et au niveau de la procédure (dans la procédure `show` ). La variable locale `num` occulte la variable au niveau du module `num` dans `show` , donc la variable locale a la valeur 2. Toutefois, il n’y a aucune variable locale à occulter `num` dans la `useModuleLevelNum` procédure. Par conséquent, `useModuleLevelNum` affecte la valeur 1 à la variable au niveau du module.

    L' `MsgBox` appel à l’intérieur `show` contourne le mécanisme d’occultation en qualifiant `num` le nom du module. Par conséquent, elle affiche la variable au niveau du module au lieu de la variable locale.

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Pour masquer une variable en l’occultant à l’aide de l’héritage

1. Assurez-vous que la variable que vous souhaitez masquer est déclarée dans une classe et au niveau de la classe (en dehors de toute procédure). Dans le cas contraire, vous ne pouvez pas l’occulter via l’héritage.

2. Définissez une classe dérivée de la classe de la variable si celle-ci n’existe pas déjà.

3. À l’intérieur de la classe dérivée, écrivez une `Dim` instruction qui déclare votre variable. Incluez le mot clé [Shadows](../../../language-reference/modifiers/shadows.md) dans la déclaration.

    Lorsque le code dans la classe dérivée fait référence au nom de la variable, le compilateur résout la référence à votre variable.

    L’exemple suivant illustre l’occultation par héritage. Il crée deux références, une qui accède à la variable de masquage et une qui ignore l’occultation.

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    L’exemple précédent déclare la variable `shadowString` dans la classe de base et l’occulte dans la classe dérivée. La procédure `showStrings` dans la classe dérivée affiche la version de l’occultation de la chaîne lorsque le nom `shadowString` n’est pas qualifié. Il affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le `MyBase` mot clé.

## <a name="robust-programming"></a>Programmation fiable

L’occultation introduit plusieurs versions d’une variable portant le même nom. Lorsqu’une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de facteurs tels que l’emplacement de l’instruction de code et la présence d’une chaîne qualifiante. Cela peut augmenter le risque de faire référence à une version inattendue d’une variable masquée. Vous pouvez réduire ce risque en qualifiant entièrement toutes les références à une variable ombrée.

## <a name="see-also"></a>Voir aussi

- [References to Declared Elements](references-to-declared-elements.md)
- [Occultation dans Visual Basic](shadowing.md)
- [Différences entre l'occultation et la substitution](differences-between-shadowing-and-overriding.md)
- [Comment : masquer une variable héritée](how-to-hide-an-inherited-variable.md)
- [Comment : accéder à une variable masquée par une classe dérivée](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Remplacements](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase et MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Éléments fondamentaux de l’héritage](../objects-and-classes/inheritance-basics.md)
