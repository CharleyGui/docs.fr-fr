---
title: Tableaux - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715055"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="c7543-102">Tableaux (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c7543-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="c7543-103">Vous pouvez stocker plusieurs variables du même type dans une structure de données de type tableau.</span><span class="sxs-lookup"><span data-stu-id="c7543-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="c7543-104">Vous déclarez un tableau en spécifiant le type de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="c7543-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="c7543-105">Si vous voulez que le tableau stocke `object` des éléments de n’importe quel type, vous pouvez spécifier comme son type.</span><span class="sxs-lookup"><span data-stu-id="c7543-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="c7543-106">Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c7543-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="c7543-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c7543-107">Example</span></span>

<span data-ttu-id="c7543-108">L’exemple suivant crée des tableaux unidimensionnels, multidimensionnels et en escalier :</span><span class="sxs-lookup"><span data-stu-id="c7543-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="c7543-109">Aperçu du tableau</span><span class="sxs-lookup"><span data-stu-id="c7543-109">Array overview</span></span>

<span data-ttu-id="c7543-110">Un tableau possède les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c7543-110">An array has the following properties:</span></span>

- <span data-ttu-id="c7543-111">Un tableau peut être [unidimensionnel](single-dimensional-arrays.md), [multidimensionnel](multidimensional-arrays.md) ou [en escalier](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="c7543-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="c7543-112">Le nombre de dimensions et la longueur de chaque dimension sont établis lors de la création de l’instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="c7543-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="c7543-113">Ces valeurs ne peuvent pas être modifiées pendant la durée de vie de l’instance.</span><span class="sxs-lookup"><span data-stu-id="c7543-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="c7543-114">Les valeurs par défaut des éléments de tableau numériques sont définies sur zéro et les éléments de référence sont définis sur Null.</span><span class="sxs-lookup"><span data-stu-id="c7543-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="c7543-115">Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.</span><span class="sxs-lookup"><span data-stu-id="c7543-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="c7543-116">Les tableaux sont indexés sur zéro : un tableau avec `n` éléments est indexée de `0` à `n-1`.</span><span class="sxs-lookup"><span data-stu-id="c7543-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="c7543-117">Les éléments de tableau peuvent être de n’importe quel type, y compris un type tableau.</span><span class="sxs-lookup"><span data-stu-id="c7543-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="c7543-118">Les types tableau sont des [types référence](../../language-reference/keywords/reference-types.md) dérivés du type de base abstrait <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="c7543-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="c7543-119">Étant donné que ce type implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser l’itération [foreach](../../language-reference/keywords/foreach-in.md) sur tous les tableaux en C#.</span><span class="sxs-lookup"><span data-stu-id="c7543-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c7543-120">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="c7543-120">Related sections</span></span>

- [<span data-ttu-id="c7543-121">Tableaux comme objets</span><span class="sxs-lookup"><span data-stu-id="c7543-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="c7543-122">Utiliser foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="c7543-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="c7543-123">Passage de tableaux en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="c7543-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="c7543-124">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c7543-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c7543-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7543-125">See also</span></span>

- [<span data-ttu-id="c7543-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c7543-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c7543-127">Collections</span><span class="sxs-lookup"><span data-stu-id="c7543-127">Collections</span></span>](../concepts/collections.md)
