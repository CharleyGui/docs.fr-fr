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
ms.openlocfilehash: ddff8c8cd82593b7d89fb0847e56123c287e364b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387879"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="48575-102">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48575-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="48575-103">Si une procédure a un paramètre [ParamArray](../../../language-reference/modifiers/paramarray.md) , vous ne pouvez pas définir une version surchargée qui prend un tableau unidimensionnel pour le tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="48575-103">If a procedure has a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="48575-104">Pour plus d’informations, consultez « surcharges implicites pour un paramètre ParamArray » dans [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="48575-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="48575-105">Pour surcharger une procédure qui accepte un nombre variable de paramètres</span><span class="sxs-lookup"><span data-stu-id="48575-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="48575-106">Veillez à ce que la procédure et la logique de code appelant tirent parti des versions surchargées plus qu’à partir d’un `ParamArray` paramètre.</span><span class="sxs-lookup"><span data-stu-id="48575-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="48575-107">Consultez « Overloads and ParamArrays » dans [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="48575-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="48575-108">Déterminez le nombre de valeurs fournies que la procédure doit accepter dans la partie variable de la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="48575-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="48575-109">Cela peut inclure la casse sans valeur et peut inclure le cas d’un tableau unidimensionnel unique.</span><span class="sxs-lookup"><span data-stu-id="48575-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="48575-110">Pour chaque nombre acceptable de valeurs fournies, écrivez une `Sub` `Function` instruction de déclaration ou qui définit la liste de paramètres correspondante.</span><span class="sxs-lookup"><span data-stu-id="48575-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="48575-111">N’utilisez pas le `Optional` `ParamArray` mot clé ou dans cette version surchargée.</span><span class="sxs-lookup"><span data-stu-id="48575-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="48575-112">Dans chaque déclaration, faites précéder le `Sub` `Function` mot clé ou du mot clé [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="48575-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="48575-113">À la suite de chaque déclaration, écrivez le code de la procédure qui doit s’exécuter lorsque le code appelant fournit des valeurs correspondant à la liste de paramètres de cette déclaration.</span><span class="sxs-lookup"><span data-stu-id="48575-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="48575-114">Mettez fin à chaque procédure avec l' `End Sub` `End Function` instruction ou, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="48575-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48575-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="48575-115">Example</span></span>  
 <span data-ttu-id="48575-116">L’exemple suivant montre une procédure définie avec un paramètre [ParamArray](../../../language-reference/modifiers/paramarray.md) , puis un ensemble équivalent de procédures surchargées.</span><span class="sxs-lookup"><span data-stu-id="48575-116">The following example shows a procedure defined with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="48575-117">Vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="48575-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="48575-118">Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="48575-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="48575-119">Les déclarations suivantes illustrent cela.</span><span class="sxs-lookup"><span data-stu-id="48575-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="48575-120">Le code dans les versions surchargées n’a pas besoin de tester si le code appelant a fourni une ou plusieurs valeurs pour le `ParamArray` paramètre, ou le cas échéant, combien.</span><span class="sxs-lookup"><span data-stu-id="48575-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="48575-121">Visual Basic passe le contrôle à la version correspondant à la liste d’arguments d’appel.</span><span class="sxs-lookup"><span data-stu-id="48575-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="48575-122">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="48575-122">Compile the code</span></span>  
 <span data-ttu-id="48575-123">Étant donné qu’une procédure avec un `ParamArray` paramètre est équivalente à un ensemble de versions surchargées, vous ne pouvez pas surcharger une telle procédure avec une liste de paramètres correspondant à l’une de ces surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="48575-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="48575-124">Pour plus d’informations, consultez [Considérations sur la surcharge des procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="48575-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="48575-125">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48575-125">.NET Framework Security</span></span>  
 <span data-ttu-id="48575-126">Chaque fois que vous traitez un tableau qui peut être indéfiniment volumineux, il existe un risque de surexécution de la capacité interne de votre application.</span><span class="sxs-lookup"><span data-stu-id="48575-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="48575-127">Si vous acceptez un tableau de paramètres, vous devez tester la longueur du tableau auquel le code appelant est passé et prendre les mesures appropriées s’il est trop grand pour votre application.</span><span class="sxs-lookup"><span data-stu-id="48575-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48575-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48575-128">See also</span></span>

- [<span data-ttu-id="48575-129">Procédures</span><span class="sxs-lookup"><span data-stu-id="48575-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="48575-130">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="48575-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="48575-131">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="48575-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="48575-132">Tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="48575-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="48575-133">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="48575-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="48575-134">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="48575-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="48575-135">Comment : définir plusieurs versions d'une procédure</span><span class="sxs-lookup"><span data-stu-id="48575-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="48575-136">Comment : appeler une procédure surchargée</span><span class="sxs-lookup"><span data-stu-id="48575-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="48575-137">Comment : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="48575-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="48575-138">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="48575-138">Overload Resolution</span></span>](./overload-resolution.md)
