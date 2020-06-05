---
title: 'Comment : appeler une procédure qui retourne une valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: a110cf9f3b42c7244d8d5bf7b49d5e6dac8c2e21
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388762"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="f12d7-102">Comment : appeler une procédure qui retourne une valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f12d7-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="f12d7-103">Une `Function` procédure retourne une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="f12d7-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="f12d7-104">Vous l’appelez en incluant son nom et ses arguments sur le côté droit d’une instruction d’assignation ou dans une expression.</span><span class="sxs-lookup"><span data-stu-id="f12d7-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="f12d7-105">Pour appeler une procédure de fonction dans une expression</span><span class="sxs-lookup"><span data-stu-id="f12d7-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="f12d7-106">Utilisez le `Function` nom de la procédure de la même façon que vous utilisez une variable.</span><span class="sxs-lookup"><span data-stu-id="f12d7-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="f12d7-107">Vous pouvez utiliser un `Function` appel de procédure partout où vous pouvez utiliser une variable ou une constante dans une expression.</span><span class="sxs-lookup"><span data-stu-id="f12d7-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="f12d7-108">Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="f12d7-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="f12d7-109">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="f12d7-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="f12d7-110">Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="f12d7-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="f12d7-111">Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f12d7-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="f12d7-112">Veillez à fournir les arguments dans l’ordre dans lequel la `Function` procédure définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="f12d7-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="f12d7-113">Vous pouvez également passer un ou plusieurs arguments par nom.</span><span class="sxs-lookup"><span data-stu-id="f12d7-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="f12d7-114">Pour plus d’informations, consultez [passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="f12d7-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="f12d7-115">La valeur retournée par la procédure participe à l’expression comme la valeur d’une variable ou d’une constante.</span><span class="sxs-lookup"><span data-stu-id="f12d7-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="f12d7-116">Pour appeler une procédure de fonction dans une instruction d’assignation</span><span class="sxs-lookup"><span data-stu-id="f12d7-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="f12d7-117">Utilisez le `Function` nom de la procédure après le `=` signe égal () dans l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="f12d7-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="f12d7-118">Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="f12d7-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="f12d7-119">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="f12d7-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="f12d7-120">Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="f12d7-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="f12d7-121">Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f12d7-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="f12d7-122">Veillez à fournir les arguments dans l’ordre dans lequel la `Function` procédure définit les paramètres correspondants, sauf si vous les passez par nom.</span><span class="sxs-lookup"><span data-stu-id="f12d7-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="f12d7-123">La valeur retournée par la procédure est stockée dans la variable ou la propriété sur le côté gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="f12d7-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f12d7-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="f12d7-124">Example</span></span>  
 <span data-ttu-id="f12d7-125">L’exemple suivant appelle la Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> pour récupérer la valeur d’une variable d’environnement de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="f12d7-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="f12d7-126">La première ligne appelle `Environ` dans une expression, et la deuxième ligne l’appelle dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="f12d7-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="f12d7-127">`Environ`prend le nom de la variable en tant qu’argument unique.</span><span class="sxs-lookup"><span data-stu-id="f12d7-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="f12d7-128">Elle retourne la valeur de la variable au code appelant.</span><span class="sxs-lookup"><span data-stu-id="f12d7-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="f12d7-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f12d7-129">See also</span></span>

- [<span data-ttu-id="f12d7-130">Function, procédures</span><span class="sxs-lookup"><span data-stu-id="f12d7-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="f12d7-131">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="f12d7-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f12d7-132">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="f12d7-132">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="f12d7-133">Comment : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="f12d7-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="f12d7-134">Comment : retourner une valeur d'une procédure</span><span class="sxs-lookup"><span data-stu-id="f12d7-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="f12d7-135">Comment : appeler une procédure qui ne retourne pas de valeur</span><span class="sxs-lookup"><span data-stu-id="f12d7-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
