---
title: Continue, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005107"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="a3d07-102">Continue, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3d07-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="a3d07-103">Transfère immédiatement le contrôle à l’itération suivante d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="a3d07-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3d07-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3d07-105">Notes</span><span class="sxs-lookup"><span data-stu-id="a3d07-105">Remarks</span></span>  
 <span data-ttu-id="a3d07-106">Vous pouvez transférer de l’intérieur d’une boucle `Do`, `For` ou `While` vers l’itération suivante de cette boucle.</span><span class="sxs-lookup"><span data-stu-id="a3d07-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="a3d07-107">Le contrôle est immédiatement passé au test de condition de boucle, ce qui équivaut à transférer vers l’instruction `For` ou `While`, ou à l’instruction `Do` ou `Loop` qui contient la clause `Until` ou `While`.</span><span class="sxs-lookup"><span data-stu-id="a3d07-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="a3d07-108">Vous pouvez utiliser `Continue` à n’importe quel emplacement de la boucle qui autorise les transferts.</span><span class="sxs-lookup"><span data-stu-id="a3d07-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="a3d07-109">Les règles autorisant le transfert de contrôle sont les mêmes que celles de l' [instruction goto](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3d07-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="a3d07-110">Par exemple, si une boucle est entièrement contenue dans un bloc `Try`, un bloc `Catch` ou un bloc `Finally`, vous pouvez utiliser `Continue` pour transférer en dehors de la boucle.</span><span class="sxs-lookup"><span data-stu-id="a3d07-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="a3d07-111">Si, en revanche, la structure `Try`... `End Try` est contenue dans la boucle, vous ne pouvez pas utiliser `Continue` pour transférer le contrôle en dehors du bloc `Finally`, et vous pouvez l’utiliser pour le transfert en dehors d’un bloc `Try` ou `Catch` uniquement si vous transférez complètement en dehors du @no_ _ t-6... `End Try`.</span><span class="sxs-lookup"><span data-stu-id="a3d07-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="a3d07-112">Si vous avez des boucles imbriquées du même type, par exemple une boucle `Do` dans une autre boucle `Do`, une instruction `Continue Do` passe à l’itération suivante de la boucle `Do` la plus profonde qui la contient.</span><span class="sxs-lookup"><span data-stu-id="a3d07-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="a3d07-113">Vous ne pouvez pas utiliser `Continue` pour passer à l’itération suivante d’une boucle conteneur du même type.</span><span class="sxs-lookup"><span data-stu-id="a3d07-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="a3d07-114">Si vous avez des boucles imbriquées de types différents, par exemple une boucle `Do` dans une boucle `For`, vous pouvez passer à l’itération suivante de l’une ou l’autre boucle à l’aide de `Continue Do` ou de `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="a3d07-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3d07-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3d07-115">Example</span></span>  
 <span data-ttu-id="a3d07-116">L’exemple de code suivant utilise l’instruction `Continue While` pour passer à la colonne suivante d’un tableau si un diviseur est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="a3d07-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="a3d07-117">La `Continue While` se trouve à l’intérieur d’une boucle `For`.</span><span class="sxs-lookup"><span data-stu-id="a3d07-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="a3d07-118">Elle est transférée à l’instruction `While col < lastcol`, qui est l’itération suivante de la boucle `While` la plus profonde qui contient la boucle `For`.</span><span class="sxs-lookup"><span data-stu-id="a3d07-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="a3d07-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3d07-119">See also</span></span>

- [<span data-ttu-id="a3d07-120">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3d07-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="a3d07-121">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3d07-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="a3d07-122">While...End While (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3d07-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="a3d07-123">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3d07-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
