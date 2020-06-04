---
title: Structures de décision
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: aac9844240defc5a21a3f4e6090fa8f49e6348a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403513"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="da4f4-102">Structures de décision (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da4f4-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="da4f4-103">Visual Basic vous permet de tester des conditions et d’effectuer différentes opérations en fonction des résultats de ce test.</span><span class="sxs-lookup"><span data-stu-id="da4f4-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="da4f4-104">Vous pouvez tester si une condition est true ou false, pour différentes valeurs d’une expression ou pour différentes exceptions générées lorsque vous exécutez une série d’instructions.</span><span class="sxs-lookup"><span data-stu-id="da4f4-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="da4f4-105">L’illustration suivante montre une structure de décision qui teste la présence d’une condition ayant la valeur true et qui effectue des actions différentes selon qu’il s’agit d’une valeur true ou false.</span><span class="sxs-lookup"><span data-stu-id="da4f4-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Organigramme d’une if... Puis... Construction Else.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="da4f4-107">If... Puis... Construction Else</span><span class="sxs-lookup"><span data-stu-id="da4f4-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="da4f4-108">`If...Then...Else`les constructions vous permettent de tester une ou plusieurs conditions et d’exécuter une ou plusieurs instructions en fonction de chaque condition.</span><span class="sxs-lookup"><span data-stu-id="da4f4-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="da4f4-109">Vous pouvez tester des conditions et prendre des mesures de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="da4f4-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="da4f4-110">Exécuter une ou plusieurs instructions si une condition est`True`</span><span class="sxs-lookup"><span data-stu-id="da4f4-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="da4f4-111">Exécuter une ou plusieurs instructions si une condition est`False`</span><span class="sxs-lookup"><span data-stu-id="da4f4-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="da4f4-112">Exécuter des instructions si une condition est `True` et d’autres si elle est`False`</span><span class="sxs-lookup"><span data-stu-id="da4f4-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="da4f4-113">Tester une condition supplémentaire si une condition antérieure est`False`</span><span class="sxs-lookup"><span data-stu-id="da4f4-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="da4f4-114">La structure de contrôle qui offre toutes ces possibilités est le [If... Puis... Instruction Else](../../../language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="da4f4-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="da4f4-115">Vous pouvez utiliser une version sur une seule ligne si vous n’avez qu’un seul test et une seule instruction à exécuter.</span><span class="sxs-lookup"><span data-stu-id="da4f4-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="da4f4-116">Si vous avez un ensemble plus complexe de conditions et d’actions, vous pouvez utiliser la version sur plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="da4f4-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="da4f4-117">Sélectionner... Construction de cas</span><span class="sxs-lookup"><span data-stu-id="da4f4-117">Select...Case Construction</span></span>  
 <span data-ttu-id="da4f4-118">La `Select...Case` construction vous permet d’évaluer une expression une fois et d’exécuter différents jeux d’instructions en fonction de différentes valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="da4f4-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="da4f4-119">Pour plus d’informations, consultez [Select... Instruction case](../../../language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="da4f4-119">For more information, see [Select...Case Statement](../../../language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="da4f4-120">Essayer... Catch... Finalisation de la construction</span><span class="sxs-lookup"><span data-stu-id="da4f4-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="da4f4-121">`Try...Catch...Finally`les constructions vous permettent d’exécuter un ensemble d’instructions sous un environnement qui conserve le contrôle si l’une de vos instructions provoque une exception.</span><span class="sxs-lookup"><span data-stu-id="da4f4-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="da4f4-122">Vous pouvez effectuer différentes actions pour différentes exceptions.</span><span class="sxs-lookup"><span data-stu-id="da4f4-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="da4f4-123">Vous pouvez éventuellement spécifier un bloc de code qui s’exécute avant de quitter la `Try...Catch...Finally` construction entière, indépendamment de ce qui se produit.</span><span class="sxs-lookup"><span data-stu-id="da4f4-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="da4f4-124">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="da4f4-124">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da4f4-125">Pour de nombreuses structures de contrôle, lorsque vous cliquez sur un mot clé, tous les mots clés de la structure sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="da4f4-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="da4f4-126">Par exemple, lorsque vous cliquez `If` dans une `If...Then...Else` construction, toutes les instances de,,, `If` `Then` `ElseIf` `Else` et `End If` de la construction sont mises en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="da4f4-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="da4f4-127">Pour passer au mot clé en surbrillance suivant ou précédent, appuyez sur CTRL + MAJ + flèche bas ou CTRL + MAJ + haut.</span><span class="sxs-lookup"><span data-stu-id="da4f4-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4f4-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da4f4-128">See also</span></span>

- [<span data-ttu-id="da4f4-129">Workflow de contrôle</span><span class="sxs-lookup"><span data-stu-id="da4f4-129">Control Flow</span></span>](index.md)
- [<span data-ttu-id="da4f4-130">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="da4f4-130">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="da4f4-131">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="da4f4-131">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="da4f4-132">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="da4f4-132">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="da4f4-133">If, opérateur</span><span class="sxs-lookup"><span data-stu-id="da4f4-133">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
