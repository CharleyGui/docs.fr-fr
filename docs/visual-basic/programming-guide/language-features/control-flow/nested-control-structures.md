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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="34b85-102">Structures de contrôle imbriquées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34b85-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="34b85-103">Vous pouvez placer des instructions de contrôle `If...Then...Else` à `For...Next` l’intérieur d’autres instructions de contrôle, par exemple un bloc dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="34b85-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="34b85-104">Une déclaration de contrôle placée à l’intérieur d’une autre déclaration de contrôle serait *imbriquée.*</span><span class="sxs-lookup"><span data-stu-id="34b85-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="34b85-105">Niveaux de nidification</span><span class="sxs-lookup"><span data-stu-id="34b85-105">Nesting Levels</span></span>  
 <span data-ttu-id="34b85-106">Les structures de contrôle dans Visual Basic peuvent être imbriquées à autant de niveaux que vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="34b85-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="34b85-107">Il est courant de rendre les structures imbriquées plus lisibles en en enfermant le corps de chacun.</span><span class="sxs-lookup"><span data-stu-id="34b85-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="34b85-108">C’est ce qu’effectue automatiquement l’éditeur intégré d’environnement de développement (IDE).</span><span class="sxs-lookup"><span data-stu-id="34b85-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="34b85-109">Dans l’exemple suivant, la procédure `sumRows` additionne les éléments positifs de chaque rangée de la matrice.</span><span class="sxs-lookup"><span data-stu-id="34b85-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="34b85-110">Dans l’exemple précédent, la `Next` première `For` déclaration ferme `Next` la boucle `For` intérieure et la dernière déclaration ferme la boucle extérieure.</span><span class="sxs-lookup"><span data-stu-id="34b85-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="34b85-111">De même, `If` dans les `End If` relevés imbriqués, les déclarations s’appliquent automatiquement à l’instruction antérieure `If` la plus proche.</span><span class="sxs-lookup"><span data-stu-id="34b85-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="34b85-112">Les `Do` boucles imbriquées fonctionnent de la `Loop` même manière, `Do` la déclaration la plus intime correspondant à la déclaration la plus intime.</span><span class="sxs-lookup"><span data-stu-id="34b85-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34b85-113">Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="34b85-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="34b85-114">Par exemple, lorsque `If` vous `If...Then...Else` cliquez dans `If`une `Then` `ElseIf`construction, tous les cas de , , , `Else`et `End If` dans la construction sont mis en évidence.</span><span class="sxs-lookup"><span data-stu-id="34b85-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="34b85-115">Pour passer au mot clé surlignée suivant ou précédent, appuyez sur CTRL-SHIFT-DOWN ARROW ou CTRL-SHIFT-UP ARROW.</span><span class="sxs-lookup"><span data-stu-id="34b85-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="34b85-116">Nidification de différents types de structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="34b85-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="34b85-117">Vous pouvez nicher un type de structure de contrôle dans un autre type.</span><span class="sxs-lookup"><span data-stu-id="34b85-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="34b85-118">L’exemple suivant `With` utilise `For Each` un bloc `If` à l’intérieur d’une boucle et des blocs imbriqués à l’intérieur du `With` bloc.</span><span class="sxs-lookup"><span data-stu-id="34b85-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="34b85-119">Structures de contrôle qui se chevauchent</span><span class="sxs-lookup"><span data-stu-id="34b85-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="34b85-120">Vous ne pouvez pas chevaucher les structures de contrôle.</span><span class="sxs-lookup"><span data-stu-id="34b85-120">You cannot overlap control structures.</span></span> <span data-ttu-id="34b85-121">Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus intime suivante.</span><span class="sxs-lookup"><span data-stu-id="34b85-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="34b85-122">Par exemple, l’arrangement suivant `For` est invalide `With` parce que la boucle se termine avant la fin du bloc intérieur.</span><span class="sxs-lookup"><span data-stu-id="34b85-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagramme qui montre un exemple de nidification invalide.](./media/nested-control-structures/example-invalid-nesting.gif)
  
 <span data-ttu-id="34b85-124">Le compilateur Visual Basic détecte ces structures de contrôle qui se chevauchent et signale une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="34b85-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b85-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34b85-125">See also</span></span>

- [<span data-ttu-id="34b85-126">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="34b85-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="34b85-127">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="34b85-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="34b85-128">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="34b85-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="34b85-129">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="34b85-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
