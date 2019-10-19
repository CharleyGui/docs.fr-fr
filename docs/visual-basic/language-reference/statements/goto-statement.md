---
title: GoTo, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 4b7a5cce56dfdd2bdc7e068aadbc18b92bba269d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581817"
---
# <a name="goto-statement"></a><span data-ttu-id="a3cb5-102">GoTo, instruction</span><span class="sxs-lookup"><span data-stu-id="a3cb5-102">GoTo Statement</span></span>
<span data-ttu-id="a3cb5-103">Rebranche de manière inconditionnelle vers une ligne spécifiée dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3cb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3cb5-104">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="a3cb5-105">Élément</span><span class="sxs-lookup"><span data-stu-id="a3cb5-105">Part</span></span>  
 `line`  
 <span data-ttu-id="a3cb5-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-106">Required.</span></span> <span data-ttu-id="a3cb5-107">Toute étiquette de ligne.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3cb5-108">Notes</span><span class="sxs-lookup"><span data-stu-id="a3cb5-108">Remarks</span></span>  
 <span data-ttu-id="a3cb5-109">L’instruction `GoTo` peut créer une branche uniquement vers les lignes de la procédure dans laquelle elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="a3cb5-110">La ligne doit avoir une étiquette de ligne à laquelle `GoTo` peut faire référence.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="a3cb5-111">Pour plus d’informations, consultez [Comment : étiqueter des instructions](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="a3cb5-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3cb5-112">les instructions `GoTo` peuvent rendre le code difficile à lire et à gérer.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="a3cb5-113">Dans la mesure du possible, utilisez une structure de contrôle à la place.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="a3cb5-114">Pour plus d’informations, consultez [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="a3cb5-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="a3cb5-115">Vous ne pouvez pas utiliser une instruction `GoTo` pour créer une branche à partir de l’extérieur d’un `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, 0... 1 ou 2... 3 construction à une étiquette à l’intérieur de.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="a3cb5-116">Création de branche et d’essai</span><span class="sxs-lookup"><span data-stu-id="a3cb5-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="a3cb5-117">Au sein d’un `Try`... `Catch`... `Finally` construction, les règles suivantes s’appliquent à la création de branche avec l’instruction `GoTo`.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="a3cb5-118">Bloc ou région</span><span class="sxs-lookup"><span data-stu-id="a3cb5-118">Block or region</span></span>|<span data-ttu-id="a3cb5-119">Créer une branche à partir de l’extérieur</span><span class="sxs-lookup"><span data-stu-id="a3cb5-119">Branching in from outside</span></span>|<span data-ttu-id="a3cb5-120">Branchement hors de l’intérieur</span><span class="sxs-lookup"><span data-stu-id="a3cb5-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="a3cb5-121">bloc `Try`</span><span class="sxs-lookup"><span data-stu-id="a3cb5-121">`Try` block</span></span>|<span data-ttu-id="a3cb5-122">Uniquement à partir d’un bloc `Catch` de la même construction <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a3cb5-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="a3cb5-123">Uniquement vers l’extérieur de la construction entière</span><span class="sxs-lookup"><span data-stu-id="a3cb5-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="a3cb5-124">bloc `Catch`</span><span class="sxs-lookup"><span data-stu-id="a3cb5-124">`Catch` block</span></span>|<span data-ttu-id="a3cb5-125">Jamais autorisé</span><span class="sxs-lookup"><span data-stu-id="a3cb5-125">Never allowed</span></span>|<span data-ttu-id="a3cb5-126">Uniquement à l’extérieur de la construction entière ou au bloc `Try` de la même construction <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a3cb5-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="a3cb5-127">bloc `Finally`</span><span class="sxs-lookup"><span data-stu-id="a3cb5-127">`Finally` block</span></span>|<span data-ttu-id="a3cb5-128">Jamais autorisé</span><span class="sxs-lookup"><span data-stu-id="a3cb5-128">Never allowed</span></span>|<span data-ttu-id="a3cb5-129">Jamais autorisé</span><span class="sxs-lookup"><span data-stu-id="a3cb5-129">Never allowed</span></span>|  
  
 <span data-ttu-id="a3cb5-130"><sup>1</sup> si une `Try`... `Catch`... `Finally` construction est imbriquée dans une autre, un bloc `Catch` peut créer une branche dans le bloc `Try` à son propre niveau d’imbrication, mais pas dans un autre bloc `Try`.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="a3cb5-131">Une `Try` imbriquée... `Catch`... `Finally` construction doit être entièrement contenue dans un bloc `Try` ou `Catch` de la construction dans laquelle elle est imbriquée.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="a3cb5-132">L’illustration suivante montre une construction `Try` imbriquée dans une autre.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="a3cb5-133">Plusieurs branches parmi les blocs des deux constructions sont indiquées comme valides ou non valides.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Diagramme graphique de branchement dans des constructions Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="a3cb5-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3cb5-135">Example</span></span>  
 <span data-ttu-id="a3cb5-136">L’exemple suivant utilise l’instruction `GoTo` pour créer une branche vers les étiquettes de ligne dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="a3cb5-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="a3cb5-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3cb5-137">See also</span></span>

- [<span data-ttu-id="a3cb5-138">Do...Loop (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3cb5-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="a3cb5-139">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3cb5-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="a3cb5-140">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3cb5-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="a3cb5-141">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3cb5-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="a3cb5-142">Select...Case (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3cb5-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="a3cb5-143">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3cb5-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="a3cb5-144">While...End While (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3cb5-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="a3cb5-145">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="a3cb5-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
