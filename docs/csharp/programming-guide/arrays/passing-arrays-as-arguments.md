---
title: Passage de tableaux en tant qu’arguments - Guide de programmation C#
description: Les tableaux en C# peuvent être passés en tant qu’arguments aux paramètres de méthode. Comme les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 68f174421e56e2cf082fe670f93c4f6627d7c17b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474629"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="3756a-104">Passage de tableaux en tant qu’arguments (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3756a-104">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="3756a-105">Les tableaux peuvent être passés en tant qu’arguments à des paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="3756a-105">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="3756a-106">Comme les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.</span><span class="sxs-lookup"><span data-stu-id="3756a-106">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="3756a-107">Passage de tableaux unidimensionnels en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="3756a-107">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="3756a-108">Vous pouvez passer un tableau unidimensionnel initialisé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="3756a-108">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="3756a-109">Par exemple, l’instruction suivante envoie un tableau à une méthode Print.</span><span class="sxs-lookup"><span data-stu-id="3756a-109">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="3756a-110">Le code suivant illustre une implémentation partielle de la méthode Print.</span><span class="sxs-lookup"><span data-stu-id="3756a-110">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="3756a-111">Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3756a-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="3756a-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3756a-112">Example</span></span>

<span data-ttu-id="3756a-113">Dans l’exemple suivant, un tableau de chaînes est initialisé et passé en tant qu’argument à une méthode `DisplayArray` pour des chaînes.</span><span class="sxs-lookup"><span data-stu-id="3756a-113">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="3756a-114">La méthode affiche les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="3756a-114">The method displays the elements of the array.</span></span> <span data-ttu-id="3756a-115">Ensuite, la méthode `ChangeArray` inverse les éléments du tableau, puis la méthode `ChangeArrayElements` modifie les trois premiers éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="3756a-115">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="3756a-116">Une fois que chaque méthode est retournée, la méthode `DisplayArray` montre que le passage d’un tableau par valeur n’empêche pas les modifications des éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="3756a-116">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="3756a-117">Passage de tableaux multidimensionnels en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="3756a-117">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="3756a-118">Vous pouvez passer un tableau multidimensionnel initialisé à une méthode de la même manière que vous passez un tableau unidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="3756a-118">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="3756a-119">Le code suivant illustre une déclaration partielle d’une méthode Print qui accepte un tableau à deux dimensions en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="3756a-119">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="3756a-120">Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3756a-120">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="3756a-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="3756a-121">Example</span></span>

<span data-ttu-id="3756a-122">Dans l’exemple suivant, un tableau à deux dimensions d’entiers est initialisé et passé à la méthode `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="3756a-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="3756a-123">La méthode affiche les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="3756a-123">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="3756a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3756a-124">See also</span></span>

- [<span data-ttu-id="3756a-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3756a-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3756a-126">Tableaux</span><span class="sxs-lookup"><span data-stu-id="3756a-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="3756a-127">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="3756a-127">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="3756a-128">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="3756a-128">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="3756a-129">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="3756a-129">Jagged Arrays</span></span>](jagged-arrays.md)
