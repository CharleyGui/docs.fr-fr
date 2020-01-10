---
title: Tableaux en escalier - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705702"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="a9462-102">Tableaux en escalier (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a9462-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="a9462-103">Un tableau en escalier est composé de plusieurs tableaux (appelés éléments).</span><span class="sxs-lookup"><span data-stu-id="a9462-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="a9462-104">Les éléments d’un tableau en escalier peuvent être de dimensions et de tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="a9462-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="a9462-105">Un tableau en escalier est parfois appelé « tableau de tableaux ».</span><span class="sxs-lookup"><span data-stu-id="a9462-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="a9462-106">Les exemples suivants montrent comment déclarer, initialiser et accéder aux tableaux en escalier.</span><span class="sxs-lookup"><span data-stu-id="a9462-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="a9462-107">Voici une déclaration d’un tableau unidimensionnel qui comporte trois éléments, chacun d’eux étant un tableau unidimensionnel d’entiers :</span><span class="sxs-lookup"><span data-stu-id="a9462-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="a9462-108">Pour pouvoir utiliser `jaggedArray`, vous devez initialiser ses éléments.</span><span class="sxs-lookup"><span data-stu-id="a9462-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="a9462-109">Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9462-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="a9462-110">Chacun des éléments est un tableau unidimensionnel d’entiers.</span><span class="sxs-lookup"><span data-stu-id="a9462-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="a9462-111">Le premier élément est un tableau de 5 entiers, le deuxième est un tableau de 4 entiers et le troisième est un tableau de 2 entiers.</span><span class="sxs-lookup"><span data-stu-id="a9462-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="a9462-112">Il est aussi possible d’utiliser des initialiseurs pour remplir les éléments de tableau de valeurs, auquel cas vous n’avez pas besoin de la taille du tableau.</span><span class="sxs-lookup"><span data-stu-id="a9462-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="a9462-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a9462-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="a9462-114">Vous pouvez aussi initialiser le tableau au moment de la déclaration, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a9462-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="a9462-115">Vous pouvez utiliser la forme abrégée suivante.</span><span class="sxs-lookup"><span data-stu-id="a9462-115">You can use the following shorthand form.</span></span> <span data-ttu-id="a9462-116">Notez que vous ne pouvez pas omettre l’opérateur `new` dans l’initialisation des éléments, car il n’existe pas d’initialisation par défaut pour les éléments :</span><span class="sxs-lookup"><span data-stu-id="a9462-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="a9462-117">Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.</span><span class="sxs-lookup"><span data-stu-id="a9462-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="a9462-118">Vous pouvez accéder aux éléments de tableau individuels comme dans ces exemples :</span><span class="sxs-lookup"><span data-stu-id="a9462-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="a9462-119">Il est possible de combiner des tableaux en escalier et des tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="a9462-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="a9462-120">Vous trouverez ci-dessous une déclaration et une initialisation d’un tableau en escalier unidimensionnel composé de trois éléments de tableau à deux dimensions de tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="a9462-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="a9462-121">Pour plus d’informations sur les tableaux à deux dimensions, consultez [Tableaux multidimensionnels](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="a9462-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="a9462-122">Vous pouvez accéder aux différents éléments comme le montre cet exemple, qui présente la valeur de l’élément `[1,0]` du premier tableau (valeur `5`) :</span><span class="sxs-lookup"><span data-stu-id="a9462-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="a9462-123">La méthode `Length` retourne le nombre de tableaux contenus dans le tableau en escalier.</span><span class="sxs-lookup"><span data-stu-id="a9462-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="a9462-124">Par exemple, en supposant que vous avez déclaré le tableau précédent, cette ligne :</span><span class="sxs-lookup"><span data-stu-id="a9462-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="a9462-125">retourne la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="a9462-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9462-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="a9462-126">Example</span></span>

 <span data-ttu-id="a9462-127">Cet exemple génère un tableau dont les éléments sont eux-mêmes des tableaux.</span><span class="sxs-lookup"><span data-stu-id="a9462-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="a9462-128">Chacun des éléments de tableau ont une taille différente.</span><span class="sxs-lookup"><span data-stu-id="a9462-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="a9462-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9462-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="a9462-130">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a9462-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a9462-131">Tableaux</span><span class="sxs-lookup"><span data-stu-id="a9462-131">Arrays</span></span>](./index.md)
- [<span data-ttu-id="a9462-132">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="a9462-132">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="a9462-133">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="a9462-133">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
