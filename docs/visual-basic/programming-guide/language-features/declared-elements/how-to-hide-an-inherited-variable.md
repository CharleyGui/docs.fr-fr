---
title: 'Procédure : Masquer une variable héritée (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: f575830df44076f694c1dfb2f68379594240fb80
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004848"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Procédure : Masquer une variable héritée (Visual Basic)

Une classe dérivée hérite de toutes les définitions de sa classe de base. Si vous souhaitez définir une variable à l’aide du même nom qu’un élément de la classe de base, vous pouvez masquer ou *occulter*cet élément de classe de base lorsque vous définissez votre variable dans la classe dérivée. Dans ce cas, le code dans la classe dérivée accède à votre variable, sauf si elle ignore explicitement le mécanisme d’occultation.

Une autre raison pour laquelle vous pouvez souhaiter masquer une variable héritée est la protection contre la révision de la classe de base. La classe de base peut subir une modification qui modifie l’élément que vous héritez. Dans ce cas, le modificateur `Shadows` force les références de la classe dérivée à être résolues vers votre variable, plutôt que vers l’élément de classe de base.

## <a name="to-hide-an-inherited-variable"></a>Pour masquer une variable héritée

1. Assurez-vous que la variable que vous souhaitez masquer est déclarée au niveau de la classe (en dehors de toute procédure). Dans le cas contraire, vous n’avez pas besoin de la masquer.
  
2. À l’intérieur de votre classe dérivée, écrivez une [instruction Dim](../../../language-reference/statements/dim-statement.md) qui déclare votre variable. Utilisez le même nom que celui de la variable héritée.

3. Incluez le mot clé [Shadows](../../../language-reference/modifiers/shadows.md) dans la déclaration.

     Lorsque le code dans la classe dérivée fait référence au nom de la variable, le compilateur résout la référence à votre variable.

     L’exemple suivant illustre l’occultation d’une variable héritée :
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     L’exemple précédent déclare la variable `shadowString` dans la classe de base et l’occulte dans la classe dérivée. La procédure `ShowStrings` dans la classe dérivée affiche la version de l’occultation de la chaîne lorsque le nom `shadowString` n’est pas qualifié. Il affiche ensuite la version occultée lorsque `shadowString` est qualifié avec le mot clé `MyBase`.  
  
## <a name="robust-programming"></a>Programmation fiable

L’occultation introduit plusieurs versions d’une variable portant le même nom. Lorsqu’une instruction de code fait référence au nom de la variable, la version vers laquelle le compilateur résout la référence dépend de facteurs tels que l’emplacement de l’instruction de code et la présence d’une chaîne qualifiante. Cela peut augmenter le risque de faire référence à une version inattendue d’une variable masquée. Vous pouvez réduire ce risque en qualifiant entièrement toutes les références à une variable ombrée.

## <a name="see-also"></a>Voir aussi

- [Références aux éléments déclarés](references-to-declared-elements.md)
- [Occultation dans Visual Basic](shadowing.md)
- [Différences entre l'occultation et la substitution](differences-between-shadowing-and-overriding.md)
- [Guide pratique pour Masquer une variable portant le même nom que la variable @ no__t-0
- [Guide pratique pour Accéder à une variable masquée par une classe dérivée @ no__t-0
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase et MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Éléments fondamentaux de l’héritage](../objects-and-classes/inheritance-basics.md)
