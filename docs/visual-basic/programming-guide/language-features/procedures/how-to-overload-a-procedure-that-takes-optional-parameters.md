---
title: 'Comment : surcharger une procédure qui accepte des paramètres optionnels'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 9ae6818b1e03ccd00ed554e98690e02ffa45de99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387840"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="8f2fc-102">Comment : surcharger une procédure qui accepte des paramètres optionnels (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f2fc-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="8f2fc-103">Si une procédure a un ou plusieurs paramètres [facultatifs](../../../language-reference/modifiers/optional.md) , vous ne pouvez pas définir une version surchargée correspondant à l’une de ses surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-103">If a procedure has one or more [Optional](../../../language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="8f2fc-104">Pour plus d’informations, consultez « surcharges implicites pour les paramètres facultatifs » dans [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8f2fc-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="8f2fc-105">Un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="8f2fc-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="8f2fc-106">Pour surcharger une procédure qui accepte un paramètre facultatif</span><span class="sxs-lookup"><span data-stu-id="8f2fc-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="8f2fc-107">Écrivez une `Sub` `Function` instruction de déclaration ou qui comprend le paramètre facultatif dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="8f2fc-108">N’utilisez pas le `Optional` mot clé dans cette version surchargée.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="8f2fc-109">Faites précéder le `Sub` `Function` mot clé ou du mot clé [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="8f2fc-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="8f2fc-110">Écrivez le code de procédure qui doit s’exécuter lorsque le code appelant fournit l’argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="8f2fc-111">Mettez fin à la procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="8f2fc-112">Écrivez une deuxième instruction de déclaration qui est identique à la première déclaration, sauf qu’elle n’inclut pas le paramètre facultatif dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="8f2fc-113">Écrivez le code de procédure qui doit s’exécuter lorsque le code appelant ne fournit pas l’argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="8f2fc-114">Mettez fin à la procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="8f2fc-115">L’exemple suivant montre une procédure définie avec un paramètre facultatif, un jeu équivalent de deux procédures surchargées, et enfin des exemples de versions surchargées non valides et valides.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="8f2fc-116">Paramètres facultatifs multiples</span><span class="sxs-lookup"><span data-stu-id="8f2fc-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="8f2fc-117">Pour une procédure avec plusieurs paramètres facultatifs, vous avez généralement besoin de plus de deux versions surchargées.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="8f2fc-118">Par exemple, s’il existe deux paramètres facultatifs, et que le code appelant peut fournir ou omettre chacun indépendamment de l’autre, vous avez besoin de quatre versions surchargées, une pour chaque combinaison possible d’arguments fournis.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="8f2fc-119">À mesure que le nombre de paramètres facultatifs augmente, la complexité de la surcharge augmente.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="8f2fc-120">Sauf si certaines combinaisons d’arguments fournis ne sont pas acceptables, pour N paramètres facultatifs, vous avez besoin de 2 ^ N versions surchargées.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="8f2fc-121">Selon la nature de la procédure, vous pouvez constater que la clarté de la logique justifie l’effort supplémentaire de définition de toutes les versions surchargées.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="8f2fc-122">Pour surcharger une procédure qui accepte plusieurs paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="8f2fc-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="8f2fc-123">Déterminez quelles combinaisons d’arguments facultatifs fournis sont acceptables pour la logique de la procédure.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="8f2fc-124">Une combinaison inacceptable peut survenir si un paramètre facultatif dépend d’un autre.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="8f2fc-125">Par exemple, si un paramètre accepte le nom d’une personne et qu’un autre accepte l’âge de la personne, une combinaison d’arguments fournissant l’âge, mais en omettant le nom, n’est pas acceptable.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="8f2fc-126">Pour chaque combinaison acceptable d’arguments facultatifs fournis, écrivez `Sub` une `Function` instruction de déclaration ou qui définit la liste de paramètres correspondante.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="8f2fc-127">N’utilisez pas le `Optional` mot clé.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="8f2fc-128">Dans chaque déclaration, faites précéder le `Sub` `Function` mot clé ou du mot clé [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="8f2fc-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="8f2fc-129">À la suite de chaque déclaration, écrivez le code de la procédure qui doit s’exécuter lorsque le code appelant fournit une liste d’arguments correspondant à la liste de paramètres de cette déclaration.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="8f2fc-130">Mettez fin à chaque procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8f2fc-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2fc-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f2fc-131">See also</span></span>

- [<span data-ttu-id="8f2fc-132">Procédures</span><span class="sxs-lookup"><span data-stu-id="8f2fc-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8f2fc-133">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="8f2fc-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8f2fc-134">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="8f2fc-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="8f2fc-135">Tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="8f2fc-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="8f2fc-136">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="8f2fc-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="8f2fc-137">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="8f2fc-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="8f2fc-138">Comment : définir plusieurs versions d'une procédure</span><span class="sxs-lookup"><span data-stu-id="8f2fc-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="8f2fc-139">Comment : appeler une procédure surchargée</span><span class="sxs-lookup"><span data-stu-id="8f2fc-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="8f2fc-140">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres</span><span class="sxs-lookup"><span data-stu-id="8f2fc-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="8f2fc-141">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="8f2fc-141">Overload Resolution</span></span>](./overload-resolution.md)
