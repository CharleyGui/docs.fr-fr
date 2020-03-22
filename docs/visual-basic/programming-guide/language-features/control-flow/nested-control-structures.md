---
title: Structures de contrôle imbriquées
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: b696c79cd3cada4416b3f4b6cdf96f00b89a5a0a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266922"
---
# <a name="nested-control-structures-visual-basic"></a>Structures de contrôle imbriquées (Visual Basic)
Vous pouvez placer des instructions de contrôle `If...Then...Else` à `For...Next` l’intérieur d’autres instructions de contrôle, par exemple un bloc dans une boucle. Une déclaration de contrôle placée à l’intérieur d’une autre déclaration de contrôle serait *imbriquée.*  
  
## <a name="nesting-levels"></a>Niveaux de nidification  
 Les structures de contrôle dans Visual Basic peuvent être imbriquées à autant de niveaux que vous le souhaitez. Il est courant de rendre les structures imbriquées plus lisibles en en enfermant le corps de chacun. C’est ce qu’effectue automatiquement l’éditeur intégré d’environnement de développement (IDE).  
  
 Dans l’exemple suivant, la procédure `sumRows` additionne les éléments positifs de chaque rangée de la matrice.  
  
```vb
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 Dans l’exemple précédent, la `Next` première `For` déclaration ferme `Next` la boucle `For` intérieure et la dernière déclaration ferme la boucle extérieure.  
  
 De même, `If` dans les `End If` relevés imbriqués, les déclarations s’appliquent automatiquement à l’instruction antérieure `If` la plus proche. Les `Do` boucles imbriquées fonctionnent de la `Loop` même manière, `Do` la déclaration la plus intime correspondant à la déclaration la plus intime.  
  
> [!NOTE]
> Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance. Par exemple, lorsque `If` vous `If...Then...Else` cliquez dans `If`une `Then` `ElseIf`construction, tous les cas de , , , `Else`et `End If` dans la construction sont mis en évidence. Pour passer au mot clé surlignée suivant ou précédent, appuyez sur CTRL-SHIFT-DOWN ARROW ou CTRL-SHIFT-UP ARROW.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Nidification de différents types de structures de contrôle  
 Vous pouvez nicher un type de structure de contrôle dans un autre type. L’exemple suivant `With` utilise `For Each` un bloc `If` à l’intérieur d’une boucle et des blocs imbriqués à l’intérieur du `With` bloc.  
  
```vb
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a>Structures de contrôle qui se chevauchent  
 Vous ne pouvez pas chevaucher les structures de contrôle. Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus intime suivante. Par exemple, l’arrangement suivant `For` est invalide `With` parce que la boucle se termine avant la fin du bloc intérieur.  
  
 ![Diagramme qui montre un exemple de nidification invalide.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Le compilateur Visual Basic détecte ces structures de contrôle qui se chevauchent et signale une erreur de compilation.  
  
## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Autres structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
