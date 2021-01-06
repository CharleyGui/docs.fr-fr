---
title: Tableaux en escalier - Guide de programmation C#
description: Un tableau en escalier en C# est un tableau dont les éléments sont des tableaux de tailles différentes. Découvrez comment déclarer, initialiser et accéder à des tableaux en escalier.
ms.date: 12/18/2020
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 6d4fb939fb6594c7644a80eb688ea852ddf8a5c5
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737279"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="d2237-104">Tableaux en escalier (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d2237-104">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="d2237-105">Un tableau en escalier est un tableau dont les éléments sont des tableaux, éventuellement de tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="d2237-105">A jagged array is an array whose elements are arrays, possibly of different sizes.</span></span> <span data-ttu-id="d2237-106">Un tableau en escalier est parfois appelé « tableau de tableaux ».</span><span class="sxs-lookup"><span data-stu-id="d2237-106">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="d2237-107">Les exemples suivants montrent comment déclarer, initialiser et accéder aux tableaux en escalier.</span><span class="sxs-lookup"><span data-stu-id="d2237-107">The following examples show how to declare, initialize, and access jagged arrays.</span></span>

 <span data-ttu-id="d2237-108">Voici une déclaration d’un tableau unidimensionnel qui comporte trois éléments, chacun d’eux étant un tableau unidimensionnel d’entiers :</span><span class="sxs-lookup"><span data-stu-id="d2237-108">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>

 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]

 <span data-ttu-id="d2237-109">Pour pouvoir utiliser `jaggedArray`, vous devez initialiser ses éléments.</span><span class="sxs-lookup"><span data-stu-id="d2237-109">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="d2237-110">Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d2237-110">You can initialize the elements like this:</span></span>

 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]

 <span data-ttu-id="d2237-111">Chacun des éléments est un tableau unidimensionnel d’entiers.</span><span class="sxs-lookup"><span data-stu-id="d2237-111">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="d2237-112">Le premier élément est un tableau de 5 entiers, le deuxième est un tableau de 4 entiers et le troisième est un tableau de 2 entiers.</span><span class="sxs-lookup"><span data-stu-id="d2237-112">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>

 <span data-ttu-id="d2237-113">Il est aussi possible d’utiliser des initialiseurs pour remplir les éléments de tableau de valeurs, auquel cas vous n’avez pas besoin de la taille du tableau.</span><span class="sxs-lookup"><span data-stu-id="d2237-113">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="d2237-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d2237-114">For example:</span></span>

 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]

 <span data-ttu-id="d2237-115">Vous pouvez aussi initialiser le tableau au moment de la déclaration, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="d2237-115">You can also initialize the array upon declaration like this:</span></span>

 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]

 <span data-ttu-id="d2237-116">Vous pouvez utiliser la forme abrégée suivante.</span><span class="sxs-lookup"><span data-stu-id="d2237-116">You can use the following shorthand form.</span></span> <span data-ttu-id="d2237-117">Notez que vous ne pouvez pas omettre l’opérateur `new` dans l’initialisation des éléments, car il n’existe pas d’initialisation par défaut pour les éléments :</span><span class="sxs-lookup"><span data-stu-id="d2237-117">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>

 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]

 <span data-ttu-id="d2237-118">Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.</span><span class="sxs-lookup"><span data-stu-id="d2237-118">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>

 <span data-ttu-id="d2237-119">Vous pouvez accéder aux éléments de tableau individuels comme dans ces exemples :</span><span class="sxs-lookup"><span data-stu-id="d2237-119">You can access individual array elements like these examples:</span></span>

 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]

 <span data-ttu-id="d2237-120">Il est possible de combiner des tableaux en escalier et des tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="d2237-120">It's possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="d2237-121">Vous trouverez ci-dessous une déclaration et une initialisation d’un tableau en escalier unidimensionnel composé de trois éléments de tableau à deux dimensions de tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="d2237-121">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="d2237-122">Pour plus d’informations, consultez [tableaux multidimensionnels](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="d2237-122">For more information, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>

 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]

 <span data-ttu-id="d2237-123">Vous pouvez accéder aux différents éléments comme le montre cet exemple, qui présente la valeur de l’élément `[1,0]` du premier tableau (valeur `5`) :</span><span class="sxs-lookup"><span data-stu-id="d2237-123">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>

 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]

 <span data-ttu-id="d2237-124">La méthode `Length` retourne le nombre de tableaux contenus dans le tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="d2237-124">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="d2237-125">Par exemple, en supposant que vous avez déclaré le tableau précédent, cette ligne :</span><span class="sxs-lookup"><span data-stu-id="d2237-125">For example, assuming you have declared the previous array, this line:</span></span>

 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]

 <span data-ttu-id="d2237-126">retourne la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="d2237-126">returns a value of 3.</span></span>

## <a name="example"></a><span data-ttu-id="d2237-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2237-127">Example</span></span>

 <span data-ttu-id="d2237-128">Cet exemple génère un tableau dont les éléments sont eux-mêmes des tableaux.</span><span class="sxs-lookup"><span data-stu-id="d2237-128">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="d2237-129">Chacun des éléments de tableau ont une taille différente.</span><span class="sxs-lookup"><span data-stu-id="d2237-129">Each one of the array elements has a different size.</span></span>

 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]

## <a name="see-also"></a><span data-ttu-id="d2237-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2237-130">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="d2237-131">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d2237-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d2237-132">Tableaux</span><span class="sxs-lookup"><span data-stu-id="d2237-132">Arrays</span></span>](./index.md)
- [<span data-ttu-id="d2237-133">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="d2237-133">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="d2237-134">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="d2237-134">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
