---
title: Variable objet ou variable bloc With non définie
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 766b95163f164ec76135b964115069b6855ceebf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750679"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="77dc0-102">Variable objet ou variable bloc With non définie</span><span class="sxs-lookup"><span data-stu-id="77dc0-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="77dc0-103">Une variable objet non valide est référencée.</span><span class="sxs-lookup"><span data-stu-id="77dc0-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="77dc0-104">Cette erreur peut se produire pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="77dc0-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="77dc0-105">Une variable a été déclarée sans spécification d’un type.</span><span class="sxs-lookup"><span data-stu-id="77dc0-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="77dc0-106">Si une variable est déclarée sans spécification d’un type, par défaut en type `Object`.</span><span class="sxs-lookup"><span data-stu-id="77dc0-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="77dc0-107">Par exemple, une variable déclarée avec `Dim x` serait de type `Object;` une variable déclarée avec `Dim x As String` serait de type `String`.</span><span class="sxs-lookup"><span data-stu-id="77dc0-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    >  <span data-ttu-id="77dc0-108">Le `Option Strict` instruction n’autorise pas le typage implicite qui aboutit à un `Object` type.</span><span class="sxs-lookup"><span data-stu-id="77dc0-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="77dc0-109">Si vous omettez le type, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="77dc0-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="77dc0-110">Consultez [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77dc0-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="77dc0-111">Vous tentez de référencer un objet qui a été défini sur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="77dc0-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="77dc0-112">Vous tentez d’accéder à un élément d’une variable de tableau n’a pas été correctement déclaré.</span><span class="sxs-lookup"><span data-stu-id="77dc0-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="77dc0-113">Par exemple, un tableau déclaré en tant que `products() As String` déclenche l’erreur si vous essayez de faire référence à un élément du tableau `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="77dc0-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="77dc0-114">Le tableau ne comporte aucun élément et est traité comme un objet.</span><span class="sxs-lookup"><span data-stu-id="77dc0-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="77dc0-115">Vous essayez d’accéder au code dans un `With...End With` bloquer avant le bloc a été initialisé.</span><span class="sxs-lookup"><span data-stu-id="77dc0-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="77dc0-116">Un `With...End With` doit être initialisé en exécutant le `With` point d’entrée instruction.</span><span class="sxs-lookup"><span data-stu-id="77dc0-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="77dc0-117">Dans les versions antérieures de Visual Basic ou VBA cette erreur a été également déclenchée en affectant une valeur à une variable sans utiliser le `Set` mot clé (`x = "name"` au lieu de `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="77dc0-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="77dc0-118">Le `Set` mot clé n’est plus valide en Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="77dc0-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="77dc0-119">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="77dc0-119">To correct this error</span></span>

1. <span data-ttu-id="77dc0-120">Définissez `Option Strict` à `On` en ajoutant le code suivant au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="77dc0-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="77dc0-121">Lorsque vous exécutez le projet, une erreur du compilateur s’affiche dans le **liste d’erreurs** pour n’importe quelle variable qui a été spécifié sans un type.</span><span class="sxs-lookup"><span data-stu-id="77dc0-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="77dc0-122">Si vous ne souhaitez pas activer `Option Strict`, recherchez le code de toutes les variables qui ont été spécifiées sans un type (`Dim x` au lieu de `Dim x As String`) et ajoutez le type prévu à la déclaration.</span><span class="sxs-lookup"><span data-stu-id="77dc0-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="77dc0-123">Vérifiez que vous ne sont pas référence à une variable objet qui a été définie sur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="77dc0-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="77dc0-124">Rechercher votre code pour le mot clé `Nothing`et de réviser votre code pour que l’objet n’est pas défini sur `Nothing` jusqu'à ce qu’une fois que vous avez les référencé.</span><span class="sxs-lookup"><span data-stu-id="77dc0-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="77dc0-125">Assurez-vous que toutes les variables tableau sont dimensionnées avant d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="77dc0-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="77dc0-126">Vous pouvez soit attribuer une dimension lorsque vous créez tout d’abord le tableau (`Dim x(5) As String` au lieu de `Dim x() As String`), ou utiliser le `ReDim` mot clé pour définir les dimensions du tableau avant tout d’abord accéder.</span><span class="sxs-lookup"><span data-stu-id="77dc0-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="77dc0-127">Assurez-vous que votre `With` est initialisé en exécutant le `With` point d’entrée instruction.</span><span class="sxs-lookup"><span data-stu-id="77dc0-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="77dc0-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77dc0-128">See also</span></span>

- [<span data-ttu-id="77dc0-129">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="77dc0-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="77dc0-130">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="77dc0-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="77dc0-131">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="77dc0-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
