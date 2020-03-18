---
title: Tableaux unidimensionnels - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: bd4ab53a9cb53e5cf636601bff5ac64a10a310a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170349"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="13cd5-102">Tableaux unidimensionnels (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="13cd5-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="13cd5-103">Vous pouvez déclarer un tableau unidimensionnel de cinq entiers comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="13cd5-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="13cd5-104">Ce tableau contient les éléments de `array[0]` à `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="13cd5-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="13cd5-105">L’opérateur [new](../../language-reference/operators/new-operator.md) est utilisé pour créer le tableau et initialiser ses éléments à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="13cd5-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="13cd5-106">Dans cet exemple, tous les éléments du tableau sont initialisés à zéro.</span><span class="sxs-lookup"><span data-stu-id="13cd5-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="13cd5-107">Un tableau qui stocke des éléments de type chaîne peut être déclaré de la même façon.</span><span class="sxs-lookup"><span data-stu-id="13cd5-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="13cd5-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="13cd5-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="13cd5-109">Initialisation du tableau</span><span class="sxs-lookup"><span data-stu-id="13cd5-109">Array Initialization</span></span>

 <span data-ttu-id="13cd5-110">Il est possible d’initialiser un tableau lors de sa déclaration, auquel cas le spécificateur de longueur n’est pas nécessaire, car il est déjà fourni par le nombre d’éléments figurant dans la liste d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="13cd5-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="13cd5-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="13cd5-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="13cd5-112">Un tableau de chaînes peut être initialisé de la même manière.</span><span class="sxs-lookup"><span data-stu-id="13cd5-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="13cd5-113">Voici une déclaration d’un tableau de chaînes où chaque élément du tableau est initialisé par un nom de jour de la semaine :</span><span class="sxs-lookup"><span data-stu-id="13cd5-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  

 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="13cd5-114">Quand vous initialisez un tableau lors de sa déclaration, vous pouvez utiliser les raccourcis suivants :</span><span class="sxs-lookup"><span data-stu-id="13cd5-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="13cd5-115">Il est possible de déclarer une variable de tableau sans initialisation, mais vous devez alors utiliser l’opérateur `new` quand vous affectez un tableau à cette variable.</span><span class="sxs-lookup"><span data-stu-id="13cd5-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="13cd5-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="13cd5-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="13cd5-117">C# 3.0 introduit les tableaux implicitement typés.</span><span class="sxs-lookup"><span data-stu-id="13cd5-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="13cd5-118">Pour plus d’informations, consultez [Tableaux implicitement typés](./implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="13cd5-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="13cd5-119">Tableaux de types valeur et de types référence</span><span class="sxs-lookup"><span data-stu-id="13cd5-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="13cd5-120">Considérons la déclaration de tableau suivante :</span><span class="sxs-lookup"><span data-stu-id="13cd5-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="13cd5-121">Le résultat de cette instruction varie selon que `SomeType` est un type valeur ou un type référence.</span><span class="sxs-lookup"><span data-stu-id="13cd5-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="13cd5-122">S’il s’agit d’un type de valeur, l’instruction crée un tableau de 10 éléments, chacun ayant le type `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="13cd5-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="13cd5-123">Si `SomeType` est un type référence, l’instruction crée un tableau de 10 éléments dont chacun est initialisé avec une référence null.</span><span class="sxs-lookup"><span data-stu-id="13cd5-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
<span data-ttu-id="13cd5-124">Pour plus d’informations sur les types de valeur et les types de référence, voir [les types de valeur](../../language-reference/builtin-types/value-types.md) et les types de [référence](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="13cd5-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="13cd5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13cd5-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="13cd5-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="13cd5-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="13cd5-127">Tableaux</span><span class="sxs-lookup"><span data-stu-id="13cd5-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="13cd5-128">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="13cd5-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="13cd5-129">Arrays déchiquetés</span><span class="sxs-lookup"><span data-stu-id="13cd5-129">Jagged Arrays</span></span>](./jagged-arrays.md)
