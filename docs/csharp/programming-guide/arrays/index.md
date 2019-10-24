---
title: Tableaux - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e31cff94c51c626c4b8f0e08df270c45a9cc1316
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772102"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="8dc29-102">Tableaux (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8dc29-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="8dc29-103">Vous pouvez stocker plusieurs variables du même type dans une structure de données de type tableau.</span><span class="sxs-lookup"><span data-stu-id="8dc29-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="8dc29-104">Vous déclarez un tableau en spécifiant le type de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="8dc29-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="8dc29-105">Si vous souhaitez que le tableau stocke des éléments de n’importe quel type, vous pouvez spécifier `object` comme son type.</span><span class="sxs-lookup"><span data-stu-id="8dc29-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="8dc29-106">Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8dc29-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="8dc29-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="8dc29-107">Example</span></span>

<span data-ttu-id="8dc29-108">L’exemple suivant crée des tableaux unidimensionnels, multidimensionnels et en escalier :</span><span class="sxs-lookup"><span data-stu-id="8dc29-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="8dc29-109">Présentation du tableau</span><span class="sxs-lookup"><span data-stu-id="8dc29-109">Array overview</span></span>

<span data-ttu-id="8dc29-110">Un tableau possède les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8dc29-110">An array has the following properties:</span></span>

- <span data-ttu-id="8dc29-111">Un tableau peut être [unidimensionnel](single-dimensional-arrays.md), [multidimensionnel](multidimensional-arrays.md) ou [en escalier](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8dc29-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="8dc29-112">Le nombre de dimensions et la longueur de chaque dimension sont établis lors de la création de l’instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="8dc29-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="8dc29-113">Ces valeurs ne peuvent pas être modifiées pendant la durée de vie de l’instance.</span><span class="sxs-lookup"><span data-stu-id="8dc29-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="8dc29-114">Les valeurs par défaut des éléments de tableau numériques sont définies sur zéro et les éléments de référence sont définis sur Null.</span><span class="sxs-lookup"><span data-stu-id="8dc29-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="8dc29-115">Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.</span><span class="sxs-lookup"><span data-stu-id="8dc29-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="8dc29-116">Les tableaux sont indexés sur zéro : un tableau avec `n` éléments est indexée de `0` à `n-1`.</span><span class="sxs-lookup"><span data-stu-id="8dc29-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="8dc29-117">Les éléments de tableau peuvent être de n’importe quel type, y compris un type tableau.</span><span class="sxs-lookup"><span data-stu-id="8dc29-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="8dc29-118">Les types tableau sont des [types référence](../../language-reference/keywords/reference-types.md) dérivés du type de base abstrait <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="8dc29-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="8dc29-119">Étant donné que ce type implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser l’itération [foreach](../../language-reference/keywords/foreach-in.md) sur tous les tableaux en C#.</span><span class="sxs-lookup"><span data-stu-id="8dc29-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8dc29-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8dc29-120">Related sections</span></span>

- [<span data-ttu-id="8dc29-121">Tableaux comme objets</span><span class="sxs-lookup"><span data-stu-id="8dc29-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="8dc29-122">Utilisation de foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="8dc29-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="8dc29-123">Passage de tableaux en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="8dc29-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="8dc29-124">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8dc29-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8dc29-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dc29-125">See also</span></span>

- [<span data-ttu-id="8dc29-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8dc29-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8dc29-127">Regroupements</span><span class="sxs-lookup"><span data-stu-id="8dc29-127">Collections</span></span>](../concepts/collections.md)
