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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352617"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="61567-102">Passage des arguments par position et par nom (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61567-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="61567-103">Quand vous appelez une procédure `Sub` ou `Function`, vous pouvez passer des arguments *par position* , dans l’ordre dans lequel ils apparaissent dans la définition de la procédure, ou vous pouvez les passer *par nom*, sans tenir compte de la position.</span><span class="sxs-lookup"><span data-stu-id="61567-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="61567-104">Quand vous transmettez un argument par nom, vous spécifiez le nom déclaré de l’argument suivi de deux-points et d’un signe égal (`:=`), suivi de la valeur de l’argument.</span><span class="sxs-lookup"><span data-stu-id="61567-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="61567-105">Vous pouvez fournir des arguments nommés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="61567-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="61567-106">Par exemple, la procédure `Sub` suivante accepte trois arguments :</span><span class="sxs-lookup"><span data-stu-id="61567-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="61567-107">Lorsque vous appelez cette procédure, vous pouvez fournir les arguments par position, par nom ou à l’aide d’une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="61567-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="61567-108">Passage des arguments par position</span><span class="sxs-lookup"><span data-stu-id="61567-108">Passing Arguments by Position</span></span>

<span data-ttu-id="61567-109">Vous pouvez appeler la méthode `Display` avec ses arguments passés par position et délimités par des virgules, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="61567-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="61567-110">Si vous omettez un argument facultatif dans une liste d’arguments positionnels, vous devez conserver son emplacement avec une virgule.</span><span class="sxs-lookup"><span data-stu-id="61567-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="61567-111">L’exemple suivant appelle la méthode `Display` sans l’argument `age` :</span><span class="sxs-lookup"><span data-stu-id="61567-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="61567-112">Passage d’arguments par nom</span><span class="sxs-lookup"><span data-stu-id="61567-112">Passing Arguments by Name</span></span>

<span data-ttu-id="61567-113">Vous pouvez également appeler `Display` avec les arguments passés par nom, également délimités par des virgules, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="61567-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="61567-114">Le passage d’arguments par nom de cette façon est particulièrement utile lorsque vous appelez une procédure qui a plusieurs arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="61567-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="61567-115">Si vous fournissez des arguments par nom, il n’est pas nécessaire d’utiliser des virgules consécutives pour indiquer les arguments positionnels manquants.</span><span class="sxs-lookup"><span data-stu-id="61567-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="61567-116">Le passage d’arguments par nom facilite également le suivi des arguments que vous passez et de ceux que vous omettez.</span><span class="sxs-lookup"><span data-stu-id="61567-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="61567-117">Combinaison d’arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="61567-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="61567-118">Vous pouvez fournir des arguments par position et par nom dans un appel de procédure unique, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="61567-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="61567-119">Dans l’exemple précédent, aucune virgule supplémentaire n’est nécessaire pour contenir la place de l’argument `age` omis, car `birth` est passé par nom.</span><span class="sxs-lookup"><span data-stu-id="61567-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="61567-120">Dans les versions de Visual Basic antérieures à 15,5, lorsque vous fournissez des arguments à l’aide d’un mélange de position et de nom, les arguments positionnels doivent être placés en premier.</span><span class="sxs-lookup"><span data-stu-id="61567-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="61567-121">Une fois que vous avez fourni un argument par nom, tous les arguments restants doivent être passés par nom.</span><span class="sxs-lookup"><span data-stu-id="61567-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="61567-122">Par exemple, l’appel suivant à la méthode `Display` affiche erreur du compilateur [BC30241 : argument nommé attendu](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="61567-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="61567-123">À compter de Visual Basic 15,5, les arguments positionnels peuvent suivre les arguments nommés si les arguments de position de fin se trouvent dans la position correcte.</span><span class="sxs-lookup"><span data-stu-id="61567-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="61567-124">S’il est compilé sous Visual Basic 15,5, l’appel précédent à la méthode `Display` se compile correctement et ne génère plus d’erreur de compilateur [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="61567-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="61567-125">Cette capacité à mélanger et à faire correspondre des arguments nommés et positionnels dans n’importe quel ordre est particulièrement utile lorsque vous souhaitez utiliser un argument nommé pour rendre votre code plus lisible.</span><span class="sxs-lookup"><span data-stu-id="61567-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="61567-126">Par exemple, le constructeur de classe `Person` suivant requiert deux arguments de type `Person`, qui peuvent tous les deux être `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="61567-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="61567-127">L’utilisation d’arguments nommés et positionnels mixtes permet d’effacer l’objectif du code lorsque la valeur des arguments `father` et `mother` est `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="61567-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="61567-128">Pour suivre les arguments positionnels avec des arguments nommés, vous devez ajouter l’élément suivant à votre fichier de projet de Visual Basic (\*. vbproj) :</span><span class="sxs-lookup"><span data-stu-id="61567-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="61567-129">Pour plus d’informations, consultez [définition de la version du langage Visual Basic](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="61567-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="61567-130">Restrictions relatives à la fourniture d’arguments par nom</span><span class="sxs-lookup"><span data-stu-id="61567-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="61567-131">Vous ne pouvez pas passer d’arguments par nom pour éviter d’entrer les arguments requis.</span><span class="sxs-lookup"><span data-stu-id="61567-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="61567-132">Vous pouvez omettre uniquement les arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="61567-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="61567-133">Vous ne pouvez pas passer un tableau de paramètres par nom.</span><span class="sxs-lookup"><span data-stu-id="61567-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="61567-134">En effet, lorsque vous appelez la procédure, vous fournissez un nombre indéfini d’arguments séparés par des virgules pour le tableau de paramètres, et le compilateur ne peut pas associer plusieurs arguments à un seul nom.</span><span class="sxs-lookup"><span data-stu-id="61567-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="61567-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61567-135">See also</span></span>

- [<span data-ttu-id="61567-136">Procédures</span><span class="sxs-lookup"><span data-stu-id="61567-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="61567-137">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="61567-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="61567-138">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="61567-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="61567-139">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="61567-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="61567-140">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="61567-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="61567-141">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="61567-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="61567-142">Optional</span><span class="sxs-lookup"><span data-stu-id="61567-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="61567-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="61567-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
