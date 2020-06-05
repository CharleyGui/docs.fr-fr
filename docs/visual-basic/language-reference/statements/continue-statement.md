---
title: Continue (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382092"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="f95f3-102">Continue, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f95f3-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="f95f3-103">Transfère immédiatement le contrôle à l’itération suivante d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="f95f3-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f95f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f95f3-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="f95f3-105">Notes</span><span class="sxs-lookup"><span data-stu-id="f95f3-105">Remarks</span></span>  
 <span data-ttu-id="f95f3-106">Vous pouvez transférer de l’intérieur d’une `Do` `For` boucle, ou `While` vers l’itération suivante de cette boucle.</span><span class="sxs-lookup"><span data-stu-id="f95f3-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="f95f3-107">Le contrôle est immédiatement passé au test de condition de boucle, ce qui équivaut à effectuer un transfert vers l' `For` `While` instruction ou, ou à l' `Do` `Loop` instruction ou qui contient la `Until` `While` clause ou.</span><span class="sxs-lookup"><span data-stu-id="f95f3-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="f95f3-108">Vous pouvez utiliser `Continue` à n’importe quel emplacement de la boucle qui autorise les transferts.</span><span class="sxs-lookup"><span data-stu-id="f95f3-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="f95f3-109">Les règles autorisant le transfert de contrôle sont les mêmes que celles de l' [instruction goto](goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f95f3-109">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="f95f3-110">Par exemple, si une boucle est entièrement contenue dans un bloc `Try` , un `Catch` bloc ou un `Finally` bloc, vous pouvez utiliser `Continue` pour transférer en dehors de la boucle.</span><span class="sxs-lookup"><span data-stu-id="f95f3-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="f95f3-111">Si, en revanche, la `Try` structure... `End Try` est contenue dans la boucle, vous ne pouvez pas utiliser `Continue` pour transférer le contrôle hors du `Finally` bloc, et vous pouvez l’utiliser pour le transfert en dehors d’un `Try` `Catch` bloc ou uniquement si vous transférez complètement en dehors de la `Try` structure... `End Try` .</span><span class="sxs-lookup"><span data-stu-id="f95f3-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="f95f3-112">Si vous disposez de boucles imbriquées du même type, par exemple une `Do` boucle dans une autre `Do` boucle, une `Continue Do` instruction passe à l’itération suivante de la boucle la plus profonde `Do` qui la contient.</span><span class="sxs-lookup"><span data-stu-id="f95f3-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="f95f3-113">Vous ne pouvez pas utiliser `Continue` pour passer à l’itération suivante d’une boucle conteneur du même type.</span><span class="sxs-lookup"><span data-stu-id="f95f3-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="f95f3-114">Si vous avez des boucles imbriquées de types différents, par exemple une `Do` boucle dans une `For` boucle, vous pouvez passer à l’itération suivante de l’une ou l’autre boucle à l’aide de `Continue Do` ou de `Continue For` .</span><span class="sxs-lookup"><span data-stu-id="f95f3-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f95f3-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="f95f3-115">Example</span></span>  
 <span data-ttu-id="f95f3-116">L’exemple de code suivant utilise l' `Continue While` instruction pour passer à la colonne suivante d’un tableau si un diviseur est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="f95f3-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="f95f3-117">`Continue While`Est à l’intérieur d’une `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="f95f3-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="f95f3-118">Elle est transférée à l' `While col < lastcol` instruction, qui est l’itération suivante de la boucle la plus profonde `While` qui contient la `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="f95f3-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="f95f3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f95f3-119">See also</span></span>

- [<span data-ttu-id="f95f3-120">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="f95f3-120">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="f95f3-121">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="f95f3-121">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="f95f3-122">While...End While (instruction)</span><span class="sxs-lookup"><span data-stu-id="f95f3-122">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="f95f3-123">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="f95f3-123">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
