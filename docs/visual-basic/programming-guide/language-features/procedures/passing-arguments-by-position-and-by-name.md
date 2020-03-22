---
title: Passage des arguments par position et par nom
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400854"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="3b878-102">Passage des arguments par position et par nom (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b878-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="3b878-103">Lorsque vous `Sub` appelez `Function` un ou une procédure, vous pouvez passer des arguments *par position* — dans l’ordre dans lequel ils apparaissent dans la définition de la procédure — ou vous pouvez les passer par *leur nom,* sans égard à la position.</span><span class="sxs-lookup"><span data-stu-id="3b878-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="3b878-104">Lorsque vous passez un argument par nom, vous spécifiez le nom`:=`déclaré de l’argument suivi d’un côlon et d’un signe égal ( ), suivi de la valeur de l’argument.</span><span class="sxs-lookup"><span data-stu-id="3b878-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="3b878-105">Vous pouvez fournir des arguments nommés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="3b878-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="3b878-106">Par exemple, `Sub` la procédure suivante prend trois arguments :</span><span class="sxs-lookup"><span data-stu-id="3b878-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="3b878-107">Lorsque vous appelez cette procédure, vous pouvez fournir les arguments par position, par nom, ou en utilisant un mélange des deux.</span><span class="sxs-lookup"><span data-stu-id="3b878-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="3b878-108">Arguments de passage par position</span><span class="sxs-lookup"><span data-stu-id="3b878-108">Passing Arguments by Position</span></span>

<span data-ttu-id="3b878-109">Vous pouvez `Display` appeler la méthode avec ses arguments adoptés par position et délimités par des virgules, comme le montre l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="3b878-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="3b878-110">Si vous ometez un argument facultatif dans une liste d’arguments positionnel, vous devez tenir sa place avec une virgule.</span><span class="sxs-lookup"><span data-stu-id="3b878-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="3b878-111">L’exemple suivant `Display` appelle `age` la méthode sans l’argument :</span><span class="sxs-lookup"><span data-stu-id="3b878-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="3b878-112">Arguments de passage par nom</span><span class="sxs-lookup"><span data-stu-id="3b878-112">Passing Arguments by Name</span></span>

<span data-ttu-id="3b878-113">Alternativement, vous `Display` pouvez appeler avec les arguments passés par leur nom, également délimités par des virgules, comme le montre l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="3b878-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="3b878-114">Passer des arguments par nom de cette façon est particulièrement utile lorsque vous appelez une procédure qui a plus d’un argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="3b878-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="3b878-115">Si vous fournissez des arguments par nom, vous n’avez pas à utiliser des virgules consécutives pour désigner les arguments de position manquants.</span><span class="sxs-lookup"><span data-stu-id="3b878-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="3b878-116">Passer des arguments par leur nom permet également de garder plus facilement une trace des arguments que vous passez et ceux que vous omettez.</span><span class="sxs-lookup"><span data-stu-id="3b878-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="3b878-117">Mélanger les arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="3b878-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="3b878-118">Vous pouvez fournir des arguments par position et par nom dans un seul appel de procédure, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3b878-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="3b878-119">Dans l’exemple précédent, aucune virgule supplémentaire n’est nécessaire pour tenir la place de l’argument omis, `age` puisque `birth` est passé par son nom.</span><span class="sxs-lookup"><span data-stu-id="3b878-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="3b878-120">Dans les versions de Visual Basic avant 15,5, lorsque vous fournissez des arguments par un mélange de position et de nom, les arguments de position doivent tous passer en premier.</span><span class="sxs-lookup"><span data-stu-id="3b878-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="3b878-121">Une fois que vous fournissez un argument par nom, tous les arguments restants doivent tous être adoptés par leur nom.</span><span class="sxs-lookup"><span data-stu-id="3b878-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="3b878-122">Par exemple, l’appel `Display` suivant à la méthode affiche l’erreur de compilateur [BC30241: Argument nommé prévu](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="3b878-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="3b878-123">En commençant par Visual Basic 15.5, les arguments de position peuvent suivre les arguments nommés si les arguments de position de fin sont dans la bonne position.</span><span class="sxs-lookup"><span data-stu-id="3b878-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="3b878-124">S’il est compilé sous Visual Basic 15.5, l’appel précédent à la `Display` méthode compile avec succès et ne génère plus d’erreur de compilateur [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="3b878-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="3b878-125">Cette capacité de mélanger et assortir les arguments nommés et de position dans n’importe quel ordre est particulièrement utile lorsque vous voulez utiliser un argument nommé pour rendre votre code plus lisible.</span><span class="sxs-lookup"><span data-stu-id="3b878-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="3b878-126">Par exemple, `Person` le constructeur de classe `Person`suivant nécessite deux `Nothing`arguments de type, qui peuvent tous deux être .</span><span class="sxs-lookup"><span data-stu-id="3b878-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="3b878-127">L’utilisation d’arguments mixtes nommés et de position permet `father` `mother` de `Nothing`rendre l’intention du code claire lorsque la valeur de la et des arguments est :</span><span class="sxs-lookup"><span data-stu-id="3b878-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="3b878-128">Pour suivre les arguments de position avec les arguments nommés,\*vous devez ajouter l’élément suivant à votre projet Visual Basic (.vbproj) fichier:</span><span class="sxs-lookup"><span data-stu-id="3b878-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="3b878-129">Pour plus d’informations voir [le réglage de la version visuelle de la langue de base](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="3b878-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="3b878-130">Restrictions sur l’approvisionnement des arguments par nom</span><span class="sxs-lookup"><span data-stu-id="3b878-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="3b878-131">Vous ne pouvez pas passer des arguments par nom pour éviter d’entrer les arguments requis.</span><span class="sxs-lookup"><span data-stu-id="3b878-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="3b878-132">Vous ne pouvez omettre que les arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="3b878-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="3b878-133">Vous ne pouvez pas passer un tableau de paramètres par nom.</span><span class="sxs-lookup"><span data-stu-id="3b878-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="3b878-134">C’est parce que lorsque vous appelez la procédure, vous fournissez un nombre indéfini d’arguments comma-séparés pour le tableau de paramètres, et le compilateur ne peut pas associer plus d’un argument avec un seul nom.</span><span class="sxs-lookup"><span data-stu-id="3b878-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b878-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b878-135">See also</span></span>

- [<span data-ttu-id="3b878-136">Procédures</span><span class="sxs-lookup"><span data-stu-id="3b878-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3b878-137">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="3b878-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3b878-138">Comment : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="3b878-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="3b878-139">Passage des arguments par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="3b878-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="3b878-140">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="3b878-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="3b878-141">Paramètres Arrays</span><span class="sxs-lookup"><span data-stu-id="3b878-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="3b878-142">Optionnel</span><span class="sxs-lookup"><span data-stu-id="3b878-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="3b878-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="3b878-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
