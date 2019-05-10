---
title: Structures de décision (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: f8b653b941c5959036256cde097a41f8c6251c7a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601230"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="29f8f-102">Structures de décision (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29f8f-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="29f8f-103">Visual Basic vous permet de tester des conditions et d’effectuer des opérations différentes en fonction des résultats de ce test.</span><span class="sxs-lookup"><span data-stu-id="29f8f-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="29f8f-104">Vous pouvez tester une condition vraie ou fausse, pour différentes valeurs d’une expression ou plusieurs exceptions générées lorsque vous exécutez une série d’instructions.</span><span class="sxs-lookup"><span data-stu-id="29f8f-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="29f8f-105">L’illustration suivante montre une structure de décision qui teste une condition est true et effectue des actions différentes selon qu’il est true ou false.</span><span class="sxs-lookup"><span data-stu-id="29f8f-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Un diagramme de flux d’une instruction If... Then... Construction de l’autre.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="29f8f-107">If... Then... Construction Else</span><span class="sxs-lookup"><span data-stu-id="29f8f-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="29f8f-108">`If...Then...Else` constructions vous permettent de tester pour une ou plusieurs conditions et d’exécuter une ou plusieurs instructions selon chaque condition.</span><span class="sxs-lookup"><span data-stu-id="29f8f-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="29f8f-109">Vous pouvez tester des conditions et prendre des mesures de plusieurs manières :</span><span class="sxs-lookup"><span data-stu-id="29f8f-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="29f8f-110">Exécuter une ou plusieurs instructions si une condition est `True`</span><span class="sxs-lookup"><span data-stu-id="29f8f-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="29f8f-111">Exécuter une ou plusieurs instructions si une condition est `False`</span><span class="sxs-lookup"><span data-stu-id="29f8f-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="29f8f-112">Exécutez des instructions si une condition est `True` et d’autres s’il s’agit `False`</span><span class="sxs-lookup"><span data-stu-id="29f8f-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="29f8f-113">Tester une condition supplémentaire si une condition préalable est `False`</span><span class="sxs-lookup"><span data-stu-id="29f8f-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="29f8f-114">La structure de contrôle qui offre toutes ces possibilités est le [si... Then... Else, instruction](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29f8f-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="29f8f-115">Vous pouvez utiliser une version de ligne si vous avez qu’un test et une instruction à exécuter.</span><span class="sxs-lookup"><span data-stu-id="29f8f-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="29f8f-116">Si vous avez un ensemble de conditions et actions plus complexe, vous pouvez utiliser la version de plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="29f8f-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="29f8f-117">Sélectionnez... Construction de cas</span><span class="sxs-lookup"><span data-stu-id="29f8f-117">Select...Case Construction</span></span>  
 <span data-ttu-id="29f8f-118">Le `Select...Case` construction vous permet d’évaluer une expression une seule fois et d’exécuter différents jeux d’instructions selon différentes valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="29f8f-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="29f8f-119">Pour plus d’informations, consultez [sélectionnez... Instruction case](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29f8f-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="29f8f-120">Try... Catch... Pour finir de Construction</span><span class="sxs-lookup"><span data-stu-id="29f8f-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="29f8f-121">`Try...Catch...Finally` constructions vous permettent d’exécuter un ensemble d’instructions sous un environnement qui conserve le contrôle si l’un de vos instructions provoque une exception.</span><span class="sxs-lookup"><span data-stu-id="29f8f-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="29f8f-122">Vous pouvez prendre des mesures différentes pour différentes exceptions.</span><span class="sxs-lookup"><span data-stu-id="29f8f-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="29f8f-123">Vous pouvez éventuellement spécifier un bloc de code qui s’exécute avant de quitter la totalité `Try...Catch...Finally` construction, quel que soit ce qui se produit.</span><span class="sxs-lookup"><span data-stu-id="29f8f-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="29f8f-124">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29f8f-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29f8f-125">Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés dans la structure sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="29f8f-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="29f8f-126">Par exemple, lorsque vous cliquez sur `If` dans un `If...Then...Else` construction, toutes les instances de `If`, `Then`, `ElseIf`, `Else`, et `End If` dans la construction sont mises en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="29f8f-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="29f8f-127">Pour déplacer vers le mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + flèche haut.</span><span class="sxs-lookup"><span data-stu-id="29f8f-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f8f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f8f-128">See also</span></span>

- [<span data-ttu-id="29f8f-129">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="29f8f-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="29f8f-130">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="29f8f-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="29f8f-131">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="29f8f-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="29f8f-132">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="29f8f-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="29f8f-133">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="29f8f-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
