---
title: Tableaux de paramètres
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: ffb532fbac70b9aa8ab210450e4d9207f5e0291f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351123"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="3e04b-102">Tableaux de paramètres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e04b-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="3e04b-103">En règle générale, vous ne pouvez pas appeler une procédure avec plus d’arguments que la déclaration de procédure ne le spécifie.</span><span class="sxs-lookup"><span data-stu-id="3e04b-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="3e04b-104">Lorsque vous avez besoin d’un nombre indéfini d’arguments, vous pouvez déclarer un *tableau de paramètres*, ce qui permet à une procédure d’accepter un tableau de valeurs pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="3e04b-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="3e04b-105">Vous n’avez pas besoin de connaître le nombre d’éléments dans le tableau de paramètres lorsque vous définissez la procédure.</span><span class="sxs-lookup"><span data-stu-id="3e04b-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="3e04b-106">La taille du tableau est déterminée individuellement par chaque appel à la procédure.</span><span class="sxs-lookup"><span data-stu-id="3e04b-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="3e04b-107">Déclaration d’un ParamArray</span><span class="sxs-lookup"><span data-stu-id="3e04b-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="3e04b-108">Vous utilisez le mot clé [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) pour désigner un tableau de paramètres dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3e04b-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="3e04b-109">Les règles suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="3e04b-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="3e04b-110">Une procédure ne peut définir qu’un seul tableau de paramètres, et doit être le dernier paramètre de la définition de la procédure.</span><span class="sxs-lookup"><span data-stu-id="3e04b-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="3e04b-111">Le tableau de paramètres doit être passé par valeur.</span><span class="sxs-lookup"><span data-stu-id="3e04b-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="3e04b-112">Il est recommandé d’inclure explicitement le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dans la définition de la procédure.</span><span class="sxs-lookup"><span data-stu-id="3e04b-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="3e04b-113">Le tableau de paramètres est automatiquement facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e04b-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="3e04b-114">Sa valeur par défaut est un tableau unidimensionnel vide du type d’élément du tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3e04b-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="3e04b-115">Tous les paramètres qui précèdent le tableau de paramètres doivent être requis.</span><span class="sxs-lookup"><span data-stu-id="3e04b-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="3e04b-116">Le tableau de paramètres doit être le seul paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="3e04b-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="3e04b-117">Appel d’un ParamArray</span><span class="sxs-lookup"><span data-stu-id="3e04b-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="3e04b-118">Quand vous appelez une procédure qui définit un tableau de paramètres, vous pouvez fournir l’argument de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="3e04b-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="3e04b-119">Rien : vous pouvez omettre l’argument [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) .</span><span class="sxs-lookup"><span data-stu-id="3e04b-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="3e04b-120">Dans ce cas, un tableau vide est passé à la procédure.</span><span class="sxs-lookup"><span data-stu-id="3e04b-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="3e04b-121">Si vous transmettez explicitement le mot clé [Nothing](../../../../visual-basic/language-reference/nothing.md) , un tableau null est passé à la procédure et peut provoquer une exception NullReferenceException si la procédure appelée ne vérifie pas cette condition.</span><span class="sxs-lookup"><span data-stu-id="3e04b-121">If you explicitly pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.</span></span>
  
- <span data-ttu-id="3e04b-122">Liste d’un nombre arbitraire d’arguments, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="3e04b-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="3e04b-123">Le type de données de chaque argument doit être implicitement convertible en type d’élément `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="3e04b-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="3e04b-124">Tableau avec le même type d’élément que le type d’élément du tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3e04b-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="3e04b-125">Dans tous les cas, le code de la procédure traite le tableau de paramètres comme un tableau unidimensionnel avec des éléments du même type de données que le type de données `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="3e04b-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3e04b-126">Chaque fois que vous traitez un tableau qui peut être indéfiniment volumineux, il existe un risque de surexécution de la capacité interne de votre application.</span><span class="sxs-lookup"><span data-stu-id="3e04b-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="3e04b-127">Si vous acceptez un tableau de paramètres, vous devez tester la taille du tableau auquel le code appelant est passé.</span><span class="sxs-lookup"><span data-stu-id="3e04b-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="3e04b-128">Prenez les mesures appropriées si elle est trop volumineuse pour votre application.</span><span class="sxs-lookup"><span data-stu-id="3e04b-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="3e04b-129">Pour plus d’informations, consultez [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e04b-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e04b-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e04b-130">Example</span></span>  
 <span data-ttu-id="3e04b-131">L’exemple suivant définit et appelle la fonction `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="3e04b-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="3e04b-132">Le modificateur `ParamArray` pour le paramètre `args` permet à la fonction d’accepter un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="3e04b-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="3e04b-133">L’exemple suivant définit une procédure avec un tableau de paramètres et renvoie les valeurs de tous les éléments de tableau passés au tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3e04b-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="3e04b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e04b-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="3e04b-135">Procédures</span><span class="sxs-lookup"><span data-stu-id="3e04b-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3e04b-136">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="3e04b-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3e04b-137">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="3e04b-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="3e04b-138">Passage des arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="3e04b-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="3e04b-139">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="3e04b-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="3e04b-140">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="3e04b-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="3e04b-141">Tableaux</span><span class="sxs-lookup"><span data-stu-id="3e04b-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="3e04b-142">Optional</span><span class="sxs-lookup"><span data-stu-id="3e04b-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
