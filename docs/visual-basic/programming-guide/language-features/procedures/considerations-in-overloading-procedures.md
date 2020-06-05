---
title: Considérations sur les surcharges de procédures
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: c4075c87df8b9daa56ca1d35e0d6661598895fdc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403367"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="8803a-102">Considérations sur les surcharges de procédures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8803a-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="8803a-103">Quand vous surchargez une procédure, vous devez utiliser une *signature* différente pour chaque version surchargée.</span><span class="sxs-lookup"><span data-stu-id="8803a-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="8803a-104">Cela signifie généralement que chaque version doit spécifier une liste de paramètres différente.</span><span class="sxs-lookup"><span data-stu-id="8803a-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="8803a-105">Pour plus d’informations, consultez « signature différente » dans surcharge de la [procédure](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="8803a-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="8803a-106">Vous pouvez surcharger une `Function` procédure à l’aide d’une `Sub` procédure, et vice versa, à condition qu’elles aient des signatures différentes.</span><span class="sxs-lookup"><span data-stu-id="8803a-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="8803a-107">Deux surcharges ne peuvent pas différer uniquement si elle a une valeur de retour et que l’autre ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="8803a-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="8803a-108">Vous pouvez surcharger une propriété de la même façon que vous surchargez une procédure, et avec les mêmes restrictions.</span><span class="sxs-lookup"><span data-stu-id="8803a-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="8803a-109">Toutefois, vous ne pouvez pas surcharger une procédure avec une propriété, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="8803a-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="8803a-110">Alternatives aux versions surchargées</span><span class="sxs-lookup"><span data-stu-id="8803a-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="8803a-111">Vous avez parfois des alternatives à des versions surchargées, en particulier lorsque la présence d’arguments est facultative ou que leur nombre est variable.</span><span class="sxs-lookup"><span data-stu-id="8803a-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="8803a-112">Gardez à l’esprit que les arguments facultatifs ne sont pas nécessairement pris en charge par tous les langages, et que les tableaux de paramètres sont limités à Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8803a-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="8803a-113">Si vous écrivez une procédure qui est susceptible d’être appelée à partir d’un code écrit dans plusieurs langages différents, les versions surchargées offrent la plus grande flexibilité.</span><span class="sxs-lookup"><span data-stu-id="8803a-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="8803a-114">Surcharges et arguments facultatifs</span><span class="sxs-lookup"><span data-stu-id="8803a-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="8803a-115">Lorsque le code appelant peut éventuellement fournir ou omettre un ou plusieurs arguments, vous pouvez définir plusieurs versions surchargées ou utiliser des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="8803a-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="8803a-116">Quand utiliser des versions surchargées</span><span class="sxs-lookup"><span data-stu-id="8803a-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="8803a-117">Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="8803a-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="8803a-118">La logique dans le code de la procédure est très différente selon que le code appelant fournit ou non un argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="8803a-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="8803a-119">Le code de la procédure ne peut pas tester de manière fiable si le code appelant a fourni un argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="8803a-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="8803a-120">C’est le cas, par exemple, s’il n’y a pas de candidat possible pour une valeur par défaut que le code appelant n’est pas censé fournir.</span><span class="sxs-lookup"><span data-stu-id="8803a-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="8803a-121">Quand utiliser des paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="8803a-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="8803a-122">Vous préférerez peut-être un ou plusieurs paramètres facultatifs dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="8803a-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="8803a-123">La seule action requise lorsque le code appelant ne fournit pas d’argument facultatif consiste à définir le paramètre sur une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8803a-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="8803a-124">Dans ce cas, le code de la procédure peut être moins compliqué si vous définissez une seule version avec un ou plusieurs `Optional` paramètres.</span><span class="sxs-lookup"><span data-stu-id="8803a-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="8803a-125">Pour plus d’informations, consultez [paramètres facultatifs](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8803a-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="8803a-126">Surcharges et ParamArrays</span><span class="sxs-lookup"><span data-stu-id="8803a-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="8803a-127">Lorsque le code appelant peut passer un nombre variable d’arguments, vous pouvez définir plusieurs versions surchargées ou utiliser un tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8803a-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="8803a-128">Quand utiliser des versions surchargées</span><span class="sxs-lookup"><span data-stu-id="8803a-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="8803a-129">Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="8803a-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="8803a-130">Vous savez que le code appelant ne passe jamais plus d’un petit nombre de valeurs au tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8803a-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="8803a-131">La logique dans le code de la procédure est très différente selon le nombre de valeurs que le code appelant transmet.</span><span class="sxs-lookup"><span data-stu-id="8803a-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="8803a-132">Le code appelant peut passer des valeurs de types de données différents.</span><span class="sxs-lookup"><span data-stu-id="8803a-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="8803a-133">Quand utiliser un tableau de paramètres</span><span class="sxs-lookup"><span data-stu-id="8803a-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="8803a-134">Vous êtes mieux servi par un `ParamArray` paramètre dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="8803a-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="8803a-135">Vous n’êtes pas en mesure de prédire le nombre de valeurs que le code appelant peut passer au tableau de paramètres, et il peut s’agir d’un grand nombre.</span><span class="sxs-lookup"><span data-stu-id="8803a-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="8803a-136">La logique de la procédure se prête à itérer au sein de toutes les valeurs que le code appelant passe, en effectuant essentiellement les mêmes opérations sur chaque valeur.</span><span class="sxs-lookup"><span data-stu-id="8803a-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="8803a-137">Pour plus d’informations, consultez [tableaux de paramètres](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8803a-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="8803a-138">Surcharges implicites pour les paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="8803a-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="8803a-139">Une procédure avec un paramètre [facultatif](../../../language-reference/modifiers/optional.md) équivaut à deux procédures surchargées, l’une avec le paramètre facultatif et l’autre sans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="8803a-139">A procedure with an [Optional](../../../language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="8803a-140">Vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres correspondant à l’un ou l’autre de ces.</span><span class="sxs-lookup"><span data-stu-id="8803a-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="8803a-141">Les déclarations suivantes illustrent cela.</span><span class="sxs-lookup"><span data-stu-id="8803a-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="8803a-142">Pour une procédure avec plusieurs paramètres facultatifs, il existe un ensemble de surcharges implicites, reçues à l’aide d’une logique similaire à celle de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="8803a-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="8803a-143">Surcharges implicites pour un paramètre ParamArray</span><span class="sxs-lookup"><span data-stu-id="8803a-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="8803a-144">Le compilateur considère qu’une procédure avec un paramètre [ParamArray](../../../language-reference/modifiers/paramarray.md) a un nombre infini de surcharges, en distinguant les unes des autres dans ce que le code appelant transmet au tableau de paramètres, comme suit :</span><span class="sxs-lookup"><span data-stu-id="8803a-144">The compiler considers a procedure with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="8803a-145">Une surcharge pour lorsque le code appelant ne fournit pas d’argument à la`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="8803a-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="8803a-146">Une surcharge pour lorsque le code appelant fournit un tableau unidimensionnel du type d' `ParamArray` élément</span><span class="sxs-lookup"><span data-stu-id="8803a-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="8803a-147">Pour chaque entier positif, une surcharge pour lorsque le code appelant fournit ce nombre d’arguments, chacun du `ParamArray` type d’élément</span><span class="sxs-lookup"><span data-stu-id="8803a-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="8803a-148">Les déclarations suivantes illustrent ces surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="8803a-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="8803a-149">Vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8803a-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="8803a-150">Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="8803a-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="8803a-151">Les déclarations suivantes illustrent cela.</span><span class="sxs-lookup"><span data-stu-id="8803a-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="8803a-152">Programmation non typée comme alternative à la surcharge</span><span class="sxs-lookup"><span data-stu-id="8803a-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="8803a-153">Si vous souhaitez autoriser le code appelant à passer des types de données différents à un paramètre, une autre approche est la programmation sans type.</span><span class="sxs-lookup"><span data-stu-id="8803a-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="8803a-154">Vous pouvez définir le commutateur de vérification de type à `Off` l’aide de l’option d' [instruction Option Strict](../../../language-reference/statements/option-strict-statement.md) ou de l’option [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) du compilateur.</span><span class="sxs-lookup"><span data-stu-id="8803a-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="8803a-155">Vous n’avez pas besoin de déclarer le type de données du paramètre.</span><span class="sxs-lookup"><span data-stu-id="8803a-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="8803a-156">Toutefois, cette approche présente les inconvénients suivants par rapport à la surcharge :</span><span class="sxs-lookup"><span data-stu-id="8803a-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="8803a-157">La programmation sans type produit un code d’exécution moins efficace.</span><span class="sxs-lookup"><span data-stu-id="8803a-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="8803a-158">La procédure doit tester tous les types de données qu’elle prévoit de passer.</span><span class="sxs-lookup"><span data-stu-id="8803a-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="8803a-159">Le compilateur ne peut pas signaler une erreur si le code appelant passe un type de données que la procédure ne prend pas en charge.</span><span class="sxs-lookup"><span data-stu-id="8803a-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8803a-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8803a-160">See also</span></span>

- [<span data-ttu-id="8803a-161">Procédures</span><span class="sxs-lookup"><span data-stu-id="8803a-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8803a-162">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="8803a-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8803a-163">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="8803a-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="8803a-164">Comment : définir plusieurs versions d'une procédure</span><span class="sxs-lookup"><span data-stu-id="8803a-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="8803a-165">Comment : appeler une procédure surchargée</span><span class="sxs-lookup"><span data-stu-id="8803a-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="8803a-166">Comment : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="8803a-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="8803a-167">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres</span><span class="sxs-lookup"><span data-stu-id="8803a-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="8803a-168">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="8803a-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="8803a-169">Surcharges</span><span class="sxs-lookup"><span data-stu-id="8803a-169">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
