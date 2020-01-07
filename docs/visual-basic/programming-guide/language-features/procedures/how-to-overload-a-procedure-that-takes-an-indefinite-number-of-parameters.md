---
title: 'Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 94f12b4cc6cb35864fefbb3b5bb1378bec5e974c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347565"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="349d5-102">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="349d5-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="349d5-103">Si une procédure a un paramètre [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , vous ne pouvez pas définir une version surchargée qui prend un tableau unidimensionnel pour le tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="349d5-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="349d5-104">Pour plus d’informations, consultez « surcharges implicites pour un paramètre ParamArray » dans [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="349d5-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="349d5-105">Pour surcharger une procédure qui accepte un nombre variable de paramètres</span><span class="sxs-lookup"><span data-stu-id="349d5-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="349d5-106">Veillez à ce que la procédure et la logique de code appelant tirent parti des versions surchargées plus qu’à partir d’un paramètre de `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="349d5-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="349d5-107">Consultez « Overloads and ParamArrays » dans [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="349d5-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="349d5-108">Déterminez le nombre de valeurs fournies que la procédure doit accepter dans la partie variable de la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="349d5-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="349d5-109">Cela peut inclure la casse sans valeur et peut inclure le cas d’un tableau unidimensionnel unique.</span><span class="sxs-lookup"><span data-stu-id="349d5-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="349d5-110">Pour chaque nombre acceptable de valeurs fournies, écrivez une `Sub` ou `Function` instruction de déclaration qui définit la liste de paramètres correspondante.</span><span class="sxs-lookup"><span data-stu-id="349d5-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="349d5-111">N’utilisez pas l' `Optional` ou le mot clé `ParamArray` dans cette version surchargée.</span><span class="sxs-lookup"><span data-stu-id="349d5-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="349d5-112">Dans chaque déclaration, faites précéder le mot clé `Sub` ou `Function` du mot clé [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="349d5-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="349d5-113">À la suite de chaque déclaration, écrivez le code de la procédure qui doit s’exécuter lorsque le code appelant fournit des valeurs correspondant à la liste de paramètres de cette déclaration.</span><span class="sxs-lookup"><span data-stu-id="349d5-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="349d5-114">Mettez fin à chaque procédure avec l’instruction `End Sub` ou `End Function`, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="349d5-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="349d5-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="349d5-115">Example</span></span>  
 <span data-ttu-id="349d5-116">L’exemple suivant montre une procédure définie avec un paramètre [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , puis un ensemble équivalent de procédures surchargées.</span><span class="sxs-lookup"><span data-stu-id="349d5-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="349d5-117">Vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="349d5-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="349d5-118">Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="349d5-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="349d5-119">Les déclarations suivantes illustrent cela.</span><span class="sxs-lookup"><span data-stu-id="349d5-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="349d5-120">Le code dans les versions surchargées n’a pas besoin de tester si le code appelant a fourni une ou plusieurs valeurs pour le paramètre `ParamArray`, ou le cas échéant, combien.</span><span class="sxs-lookup"><span data-stu-id="349d5-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="349d5-121">Visual Basic passe le contrôle à la version correspondant à la liste d’arguments d’appel.</span><span class="sxs-lookup"><span data-stu-id="349d5-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="349d5-122">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="349d5-122">Compile the code</span></span>  
 <span data-ttu-id="349d5-123">Étant donné qu’une procédure avec un paramètre `ParamArray` est équivalente à un ensemble de versions surchargées, vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres correspondant à l’une de ces surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="349d5-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="349d5-124">Pour plus d’informations, consultez [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="349d5-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="349d5-125">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="349d5-125">.NET Framework Security</span></span>  
 <span data-ttu-id="349d5-126">Chaque fois que vous traitez un tableau qui peut être indéfiniment volumineux, il existe un risque de surexécution de la capacité interne de votre application.</span><span class="sxs-lookup"><span data-stu-id="349d5-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="349d5-127">Si vous acceptez un tableau de paramètres, vous devez tester la longueur du tableau auquel le code appelant est passé et prendre les mesures appropriées s’il est trop grand pour votre application.</span><span class="sxs-lookup"><span data-stu-id="349d5-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349d5-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="349d5-128">See also</span></span>

- [<span data-ttu-id="349d5-129">Procédures</span><span class="sxs-lookup"><span data-stu-id="349d5-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="349d5-130">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="349d5-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="349d5-131">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="349d5-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="349d5-132">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="349d5-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="349d5-133">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="349d5-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="349d5-134">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="349d5-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="349d5-135">Guide pratique : définir plusieurs versions d’une procédure</span><span class="sxs-lookup"><span data-stu-id="349d5-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="349d5-136">Guide pratique : appeler une procédure surchargée</span><span class="sxs-lookup"><span data-stu-id="349d5-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="349d5-137">Guide pratique : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="349d5-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="349d5-138">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="349d5-138">Overload Resolution</span></span>](./overload-resolution.md)
