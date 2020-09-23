---
title: 'Comment : appeler une procédure qui retourne une valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 53589f84c6675d1e7ae2a593341e5dac747132a9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083975"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="01fd6-102">Comment : appeler une procédure qui retourne une valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01fd6-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="01fd6-103">Une `Function` procédure retourne une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="01fd6-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="01fd6-104">Vous l’appelez en incluant son nom et ses arguments sur le côté droit d’une instruction d’assignation ou dans une expression.</span><span class="sxs-lookup"><span data-stu-id="01fd6-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="01fd6-105">Pour appeler une procédure de fonction dans une expression</span><span class="sxs-lookup"><span data-stu-id="01fd6-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="01fd6-106">Utilisez le `Function` nom de la procédure de la même façon que vous utilisez une variable.</span><span class="sxs-lookup"><span data-stu-id="01fd6-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="01fd6-107">Vous pouvez utiliser un `Function` appel de procédure partout où vous pouvez utiliser une variable ou une constante dans une expression.</span><span class="sxs-lookup"><span data-stu-id="01fd6-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="01fd6-108">Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="01fd6-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="01fd6-109">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="01fd6-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="01fd6-110">Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="01fd6-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="01fd6-111">Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="01fd6-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="01fd6-112">Veillez à fournir les arguments dans l’ordre dans lequel la `Function` procédure définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="01fd6-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="01fd6-113">Vous pouvez également passer un ou plusieurs arguments par nom.</span><span class="sxs-lookup"><span data-stu-id="01fd6-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="01fd6-114">Pour plus d’informations, consultez [passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="01fd6-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="01fd6-115">La valeur retournée par la procédure participe à l’expression comme la valeur d’une variable ou d’une constante.</span><span class="sxs-lookup"><span data-stu-id="01fd6-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="01fd6-116">Pour appeler une procédure de fonction dans une instruction d’assignation</span><span class="sxs-lookup"><span data-stu-id="01fd6-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="01fd6-117">Utilisez le `Function` nom de la procédure après le `=` signe égal () dans l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="01fd6-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="01fd6-118">Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="01fd6-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="01fd6-119">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="01fd6-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="01fd6-120">Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="01fd6-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="01fd6-121">Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="01fd6-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="01fd6-122">Veillez à fournir les arguments dans l’ordre dans lequel la `Function` procédure définit les paramètres correspondants, sauf si vous les passez par nom.</span><span class="sxs-lookup"><span data-stu-id="01fd6-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="01fd6-123">La valeur retournée par la procédure est stockée dans la variable ou la propriété sur le côté gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="01fd6-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01fd6-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="01fd6-124">Example</span></span>  

 <span data-ttu-id="01fd6-125">L’exemple suivant appelle la Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> pour récupérer la valeur d’une variable d’environnement de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="01fd6-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="01fd6-126">La première ligne appelle `Environ` dans une expression, et la deuxième ligne l’appelle dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="01fd6-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="01fd6-127">`Environ` prend le nom de la variable en tant qu’argument unique.</span><span class="sxs-lookup"><span data-stu-id="01fd6-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="01fd6-128">Elle retourne la valeur de la variable au code appelant.</span><span class="sxs-lookup"><span data-stu-id="01fd6-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="01fd6-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01fd6-129">See also</span></span>

- [<span data-ttu-id="01fd6-130">Function, procédures</span><span class="sxs-lookup"><span data-stu-id="01fd6-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="01fd6-131">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="01fd6-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="01fd6-132">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="01fd6-132">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="01fd6-133">Comment : créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="01fd6-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="01fd6-134">Comment : retourner une valeur d'une procédure</span><span class="sxs-lookup"><span data-stu-id="01fd6-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="01fd6-135">Comment : appeler une procédure qui ne retourne pas de valeur</span><span class="sxs-lookup"><span data-stu-id="01fd6-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
