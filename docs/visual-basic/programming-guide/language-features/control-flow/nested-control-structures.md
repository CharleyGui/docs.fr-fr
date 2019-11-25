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
ms.openlocfilehash: 5818b13661fb4415c6f531b741b8a963a80bd2b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348152"
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="75b73-102">Structures de contrôle imbriquées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b73-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="75b73-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span><span class="sxs-lookup"><span data-stu-id="75b73-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="75b73-104">A control statement placed inside another control statement is said to be *nested*.</span><span class="sxs-lookup"><span data-stu-id="75b73-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="75b73-105">Nesting Levels</span><span class="sxs-lookup"><span data-stu-id="75b73-105">Nesting Levels</span></span>  
 <span data-ttu-id="75b73-106">Control structures in Visual Basic can be nested to as many levels as you want.</span><span class="sxs-lookup"><span data-stu-id="75b73-106">Control structures in Visual Basic can be nested to as many levels as you want.</span></span> <span data-ttu-id="75b73-107">It is common practice to make nested structures more readable by indenting the body of each one.</span><span class="sxs-lookup"><span data-stu-id="75b73-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="75b73-108">The integrated development environment (IDE) editor automatically does this.</span><span class="sxs-lookup"><span data-stu-id="75b73-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="75b73-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span><span class="sxs-lookup"><span data-stu-id="75b73-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
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
  
 <span data-ttu-id="75b73-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span><span class="sxs-lookup"><span data-stu-id="75b73-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="75b73-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span><span class="sxs-lookup"><span data-stu-id="75b73-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="75b73-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span><span class="sxs-lookup"><span data-stu-id="75b73-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75b73-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span><span class="sxs-lookup"><span data-stu-id="75b73-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="75b73-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span><span class="sxs-lookup"><span data-stu-id="75b73-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="75b73-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span><span class="sxs-lookup"><span data-stu-id="75b73-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="75b73-116">Nesting Different Kinds of Control Structures</span><span class="sxs-lookup"><span data-stu-id="75b73-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="75b73-117">You can nest one kind of control structure within another kind.</span><span class="sxs-lookup"><span data-stu-id="75b73-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="75b73-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span><span class="sxs-lookup"><span data-stu-id="75b73-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
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
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="75b73-119">Overlapping Control Structures</span><span class="sxs-lookup"><span data-stu-id="75b73-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="75b73-120">You cannot overlap control structures.</span><span class="sxs-lookup"><span data-stu-id="75b73-120">You cannot overlap control structures.</span></span> <span data-ttu-id="75b73-121">This means that any nested structure must be completely contained within the next innermost structure.</span><span class="sxs-lookup"><span data-stu-id="75b73-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="75b73-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span><span class="sxs-lookup"><span data-stu-id="75b73-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 ![Diagram that shows an example of invalid nesting.](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 <span data-ttu-id="75b73-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span><span class="sxs-lookup"><span data-stu-id="75b73-124">The Visual Basic compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b73-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75b73-125">See also</span></span>

- [<span data-ttu-id="75b73-126">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="75b73-126">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="75b73-127">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="75b73-127">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="75b73-128">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="75b73-128">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="75b73-129">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="75b73-129">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
