---
title: Variable objet ou variable bloc With non définie
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040557"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="547e7-102">Variable objet ou variable bloc With non définie</span><span class="sxs-lookup"><span data-stu-id="547e7-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="547e7-103">Une variable objet non valide est référencée.</span><span class="sxs-lookup"><span data-stu-id="547e7-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="547e7-104">Cette erreur peut se produire pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="547e7-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="547e7-105">Une variable a été déclarée sans spécifier de type.</span><span class="sxs-lookup"><span data-stu-id="547e7-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="547e7-106">Si une variable est déclarée sans spécifier de type, la valeur par défaut `Object`est type.</span><span class="sxs-lookup"><span data-stu-id="547e7-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="547e7-107">Par exemple, une variable déclarée `Dim x` avec est de type `Object;` , une variable déclarée avec `Dim x As String` est de `String`type.</span><span class="sxs-lookup"><span data-stu-id="547e7-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="547e7-108">L' `Option Strict` instruction interdit le typage implicite qui produit un `Object` type.</span><span class="sxs-lookup"><span data-stu-id="547e7-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="547e7-109">Si vous omettez le type, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="547e7-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="547e7-110">Consultez [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="547e7-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="547e7-111">Vous tentez de référencer un objet qui a été défini `Nothing`sur.</span><span class="sxs-lookup"><span data-stu-id="547e7-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="547e7-112">Vous tentez d’accéder à un élément d’une variable tableau qui n’a pas été correctement déclarée.</span><span class="sxs-lookup"><span data-stu-id="547e7-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="547e7-113">Par exemple, un tableau déclaré comme `products() As String` déclenchera l’erreur si vous tentez de référencer un élément du `products(3) = "Widget"`tableau.</span><span class="sxs-lookup"><span data-stu-id="547e7-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="547e7-114">Le tableau n’a pas d’éléments et est traité comme un objet.</span><span class="sxs-lookup"><span data-stu-id="547e7-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="547e7-115">Vous tentez d’accéder au code dans `With...End With` un bloc avant que le bloc n’ait été initialisé.</span><span class="sxs-lookup"><span data-stu-id="547e7-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="547e7-116">Un `With...End With` bloc doit être initialisé en exécutant le point d' `With` entrée de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="547e7-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="547e7-117">Dans les versions antérieures de Visual Basic ou VBA, cette erreur était également déclenchée en affectant une valeur à une variable sans `Set` utiliser le`x = "name"` mot clé `Set x = "name"`(au lieu de).</span><span class="sxs-lookup"><span data-stu-id="547e7-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="547e7-118">Le `Set` mot clé n’est plus valide dans Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="547e7-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="547e7-119">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="547e7-119">To correct this error</span></span>

1. <span data-ttu-id="547e7-120">Affectez la valeur `Option Strict` enajoutantlecodesuivantaudébutdufichier:`On`</span><span class="sxs-lookup"><span data-stu-id="547e7-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="547e7-121">Quand vous exécutez le projet, une erreur de compilation s’affiche dans le **liste d’erreurs** pour toute variable qui a été spécifiée sans type.</span><span class="sxs-lookup"><span data-stu-id="547e7-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="547e7-122">Si vous ne souhaitez pas activer `Option Strict`, recherchez dans votre code toutes les variables qui ont été spécifiées sans`Dim x` type ( `Dim x As String`au lieu de) et ajoutez le type prévu à la déclaration.</span><span class="sxs-lookup"><span data-stu-id="547e7-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="547e7-123">Assurez-vous que vous ne faites pas référence à une variable objet `Nothing`qui a été définie sur.</span><span class="sxs-lookup"><span data-stu-id="547e7-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="547e7-124">Recherchez le mot clé `Nothing`dans votre code et modifiez votre code afin que l’objet ne soit pas défini sur `Nothing` jusqu’à ce que vous l’ayez référencé.</span><span class="sxs-lookup"><span data-stu-id="547e7-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="547e7-125">Assurez-vous que toutes les variables de tableau sont dimensionnées avant d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="547e7-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="547e7-126">Vous pouvez affecter une dimension lors de la création initiale du tableau (`Dim x(5) As String` au lieu `Dim x() As String`de), ou utiliser `ReDim` le mot clé pour définir les dimensions du tableau avant d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="547e7-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="547e7-127">Assurez- `With` vous que votre bloc est initialisé en exécutant `With` le point d’entrée de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="547e7-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="547e7-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="547e7-128">See also</span></span>

- [<span data-ttu-id="547e7-129">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="547e7-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="547e7-130">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="547e7-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="547e7-131">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="547e7-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
