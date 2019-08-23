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
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="59bf3-102">Structures de contrôle imbriquées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59bf3-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="59bf3-103">Vous pouvez placer des instructions de contrôle dans d’autres instructions de contrôle `If...Then...Else` , par exemple `For...Next` un bloc dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="59bf3-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="59bf3-104">Une instruction de contrôle placée à l’intérieur d’une autre instructionde contrôle est dite imbriquée.</span><span class="sxs-lookup"><span data-stu-id="59bf3-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="59bf3-105">Niveaux d’imbrication</span><span class="sxs-lookup"><span data-stu-id="59bf3-105">Nesting Levels</span></span>  
 <span data-ttu-id="59bf3-106">Les structures de contrôle dans Visual Basic peuvent être imbriquées à autant de niveaux que vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="59bf3-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="59bf3-107">Il est courant de rendre les structures imbriquées plus lisibles en mettant en retrait le corps de chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="59bf3-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="59bf3-108">L’éditeur de l’environnement de développement intégré (IDE) effectue automatiquement cette procédure.</span><span class="sxs-lookup"><span data-stu-id="59bf3-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="59bf3-109">Dans l’exemple suivant, la procédure `sumRows` ajoute les éléments positifs de chaque ligne de la matrice.</span><span class="sxs-lookup"><span data-stu-id="59bf3-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="59bf3-110">Dans l’exemple précédent, la première `Next` instruction ferme la boucle `For` interne et la dernière `Next` instruction ferme la boucle `For` externe.</span><span class="sxs-lookup"><span data-stu-id="59bf3-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="59bf3-111">De même, dans les `If` instructions imbriquées `End If` , les instructions s’appliquent automatiquement à `If` l’instruction précédente la plus proche.</span><span class="sxs-lookup"><span data-stu-id="59bf3-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="59bf3-112">Les boucles imbriquées fonctionnent de la même manière, avec `Do` l' instructionlaplusprofondequicorrespondàl’instructionlaplusprofonde.`Loop` `Do`</span><span class="sxs-lookup"><span data-stu-id="59bf3-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59bf3-113">Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="59bf3-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="59bf3-114">Par exemple, lorsque vous cliquez `If` dans une `If...Then...Else` construction, `ElseIf`toutes les `Else`instances `If`de `Then`,,, et `End If` de la construction sont mises en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="59bf3-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="59bf3-115">Pour passer au mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + haut.</span><span class="sxs-lookup"><span data-stu-id="59bf3-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="59bf3-116">Imbrication de différents genres de structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="59bf3-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="59bf3-117">Vous pouvez imbriquer un type de structure de contrôle à l’intérieur d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="59bf3-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="59bf3-118">L’exemple suivant utilise un `With` bloc à l' `For Each` intérieur d’une boucle `If` et des blocs `With` imbriqués à l’intérieur du bloc.</span><span class="sxs-lookup"><span data-stu-id="59bf3-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="59bf3-119">Superposition de structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="59bf3-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="59bf3-120">Vous ne pouvez pas chevaucher les structures de contrôle.</span><span class="sxs-lookup"><span data-stu-id="59bf3-120">You cannot overlap control structures.</span></span> <span data-ttu-id="59bf3-121">Cela signifie que toute structure imbriquée doit être entièrement contenue dans la structure la plus profonde suivante.</span><span class="sxs-lookup"><span data-stu-id="59bf3-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="59bf3-122">Par exemple, la disposition suivante n’est pas valide `For` , car la boucle se termine avant la fin du bloc interne. `With`</span><span class="sxs-lookup"><span data-stu-id="59bf3-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagramme qui montre un exemple d’imbrication non valide.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 <span data-ttu-id="59bf3-124">Le compilateur de Visual Basic détecte ces structures de contrôle qui se chevauchent et signale une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="59bf3-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bf3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59bf3-125">See also</span></span>

- [<span data-ttu-id="59bf3-126">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="59bf3-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="59bf3-127">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="59bf3-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="59bf3-128">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="59bf3-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="59bf3-129">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="59bf3-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
