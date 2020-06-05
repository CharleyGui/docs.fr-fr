---
title: 'Comment : accéder à une variable masquée par une classe dérivée'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392855"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Comment : accéder à une variable masquée par une classe dérivée (Visual Basic)

Lorsque le code d’une classe dérivée accède à une variable, le compilateur résout normalement la référence à la version accessible la plus proche, autrement dit, la version accessible, le plus petit des étapes de dérivation, en arrière de la classe d’accès. Si la variable est définie dans la classe dérivée, le code accède normalement à cette définition.

Si la variable de classe dérivée occulte une variable de la classe de base, elle masque la version de la classe de base. Toutefois, vous pouvez accéder à la variable de classe de base en la qualifiant avec le `MyBase` mot clé.

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Pour accéder à une variable de classe de base masquée par une classe dérivée

- Dans une expression ou une instruction d’assignation, faites précéder le nom de la variable du `MyBase` mot clé et d’un point ( `.` ).

    Le compilateur résout la référence à la version de la classe de base de la variable.

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

Pour réduire le risque de faire référence à une version inattendue d’une variable masquée, vous pouvez qualifier entièrement toutes les références à une variable ombrée. L’occultation introduit plusieurs versions d’une variable portant le même nom. Lorsqu’une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de facteurs tels que l’emplacement de l’instruction de code et la présence d’une chaîne qualifiante. Cela peut augmenter le risque de faire référence à la mauvaise version de la variable.

## <a name="see-also"></a>Voir aussi

- [References to Declared Elements](references-to-declared-elements.md)
- [Occultation dans Visual Basic](shadowing.md)
- [Différences entre l'occultation et la substitution](differences-between-shadowing-and-overriding.md)
- [Comment : masquer une variable portant le même nom que votre variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Comment : masquer une variable héritée](how-to-hide-an-inherited-variable.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Remplacements](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase et MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Éléments fondamentaux de l’héritage](../objects-and-classes/inheritance-basics.md)
