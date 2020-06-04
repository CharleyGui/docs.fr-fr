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
ms.openlocfilehash: 539ad639320615c1e53176fe47e5468864aa21d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414387"
---
# <a name="nested-control-structures-visual-basic"></a>Structures de contrôle imbriquées (Visual Basic)
Vous pouvez placer des instructions de contrôle dans d’autres instructions de contrôle, par exemple un `If...Then...Else` bloc dans une `For...Next` boucle. Une instruction de contrôle placée à l’intérieur d’une autre instruction de contrôle est dite *imbriquée*.  
  
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
  
 Dans l’exemple précédent, la première `Next` instruction ferme la `For` boucle interne et la dernière `Next` instruction ferme la `For` boucle externe.  
  
 De même, dans `If` les instructions imbriquées, les `End If` instructions s’appliquent automatiquement à l’instruction précédente la plus proche `If` . `Do`Les boucles imbriquées fonctionnent de la même manière, avec l’instruction la plus profonde qui `Loop` correspond à l’instruction la plus profonde `Do` .  
  
> [!NOTE]
> Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance. Par exemple, lorsque vous cliquez `If` dans une `If...Then...Else` construction, toutes les instances de,,, `If` `Then` `ElseIf` `Else` et `End If` de la construction sont mises en surbrillance. Pour passer au mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + haut.  
  
## <a name="nesting-different-kinds-of-control-structures"></a>Imbrication de différents genres de structures de contrôle  
 Vous pouvez imbriquer un type de structure de contrôle à l’intérieur d’un autre type. L’exemple suivant utilise un `With` bloc à l’intérieur d’une `For Each` boucle et des blocs imbriqués `If` à l’intérieur du `With` bloc.  
  
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
 Vous ne pouvez pas chevaucher les structures de contrôle. Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus profonde suivante. Par exemple, la disposition suivante n’est pas valide, car la `For` boucle se termine avant la `With` fin du bloc interne.  
  
 ![Diagramme qui montre un exemple d’imbrication non valide.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Le compilateur de Visual Basic détecte ces structures de contrôle qui se chevauchent et signale une erreur de compilation.  
  
## <a name="see-also"></a>Voir aussi

- [Workflow de contrôle](index.md)
- [Structures de décision](decision-structures.md)
- [Structures de boucle](loop-structures.md)
- [Autres structures de contrôle](other-control-structures.md)
