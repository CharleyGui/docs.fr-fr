---
title: Structures de contrôle imbriquées (Visual Basic)
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
ms.openlocfilehash: f559bf603605873f1b9155e9a96cb367e5420343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941688"
---
# <a name="nested-control-structures-visual-basic"></a>Structures de contrôle imbriquées (Visual Basic)
Vous pouvez placer des instructions de contrôle dans d’autres instructions de contrôle `If...Then...Else` , par exemple `For...Next` un bloc dans une boucle. Une instruction de contrôle placée à l’intérieur d’une autre instructionde contrôle est dite imbriquée.  
  
## <a name="nesting-levels"></a>Niveaux d’imbrication  
 Les structures de contrôle dans Visual Basic peuvent être imbriquées à autant de niveaux que vous le souhaitez. Il est courant de rendre les structures imbriquées plus lisibles en mettant en retrait le corps de chacune d’elles. L’éditeur de l’environnement de développement intégré (IDE) effectue automatiquement cette procédure.  
  
 Dans l’exemple suivant, la procédure `sumRows` ajoute les éléments positifs de chaque ligne de la matrice.  
  
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
  
 Dans l’exemple précédent, la première `Next` instruction ferme la boucle `For` interne et la dernière `Next` instruction ferme la boucle `For` externe.  
  
 De même, dans les `If` instructions imbriquées `End If` , les instructions s’appliquent automatiquement à `If` l’instruction précédente la plus proche. Les boucles imbriquées fonctionnent de la même manière, avec `Do` l' instructionlaplusprofondequicorrespondàl’instructionlaplusprofonde.`Loop` `Do`  
  
> [!NOTE]
> Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance. Par exemple, lorsque vous cliquez `If` dans une `If...Then...Else` construction, `ElseIf`toutes les `Else`instances `If`de `Then`,,, et `End If` de la construction sont mises en surbrillance. Pour passer au mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + haut.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Imbrication de différents genres de structures de contrôle  
 Vous pouvez imbriquer un type de structure de contrôle à l’intérieur d’un autre type. L’exemple suivant utilise un `With` bloc à l' `For Each` intérieur d’une boucle `If` et des blocs `With` imbriqués à l’intérieur du bloc.  
  
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
  
## <a name="overlapping-control-structures"></a>Superposition de structures de contrôle  
 Vous ne pouvez pas chevaucher les structures de contrôle. Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus profonde suivante. Par exemple, la disposition suivante n’est pas valide `For` , car la boucle se termine avant la fin du bloc interne. `With`  
  
 ![Diagramme qui montre un exemple d’imbrication non valide.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Le compilateur de Visual Basic détecte ces structures de contrôle qui se chevauchent et signale une erreur de compilation.  
  
## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Autres structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
