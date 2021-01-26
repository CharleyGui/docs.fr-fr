---
title: Tableaux - Guide de programmation C#
description: Stocker plusieurs variables du même type dans une structure de données de tableau en C#. Déclarez un tableau en spécifiant un type ou spécifiez un objet pour stocker tout type.
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794766"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="fbda6-104">Tableaux (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fbda6-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="fbda6-105">Vous pouvez stocker plusieurs variables du même type dans une structure de données de type tableau.</span><span class="sxs-lookup"><span data-stu-id="fbda6-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="fbda6-106">Vous déclarez un tableau en spécifiant le type de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="fbda6-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="fbda6-107">Si vous souhaitez que le tableau stocke des éléments de n’importe quel type, vous pouvez spécifier `object` en tant que type.</span><span class="sxs-lookup"><span data-stu-id="fbda6-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="fbda6-108">Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="fbda6-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="fbda6-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbda6-109">Example</span></span>

<span data-ttu-id="fbda6-110">L’exemple suivant crée des tableaux unidimensionnels, multidimensionnels et en escalier :</span><span class="sxs-lookup"><span data-stu-id="fbda6-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="fbda6-111">Présentation du tableau</span><span class="sxs-lookup"><span data-stu-id="fbda6-111">Array overview</span></span>

<span data-ttu-id="fbda6-112">Un tableau possède les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="fbda6-112">An array has the following properties:</span></span>

- <span data-ttu-id="fbda6-113">Un tableau peut être [unidimensionnel](single-dimensional-arrays.md) [, multidimensionnel ou en](multidimensional-arrays.md) [escalier](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="fbda6-113">An array can be [single-dimensional](single-dimensional-arrays.md), [multidimensional](multidimensional-arrays.md) or [jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="fbda6-114">Le nombre de dimensions et la longueur de chaque dimension sont établis lors de la création de l’instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="fbda6-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="fbda6-115">Ces valeurs ne peuvent pas être modifiées pendant la durée de vie de l’instance.</span><span class="sxs-lookup"><span data-stu-id="fbda6-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="fbda6-116">Les valeurs par défaut des éléments de tableau numériques sont définies sur zéro et les éléments de référence sont définis sur Null.</span><span class="sxs-lookup"><span data-stu-id="fbda6-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="fbda6-117">Un tableau en escalier est un tableau de tableaux, et par conséquent ses éléments sont des types référence et sont initialisés sur `null`.</span><span class="sxs-lookup"><span data-stu-id="fbda6-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="fbda6-118">Les tableaux sont indexés sur zéro : un tableau avec `n` éléments est indexée de `0` à `n-1`.</span><span class="sxs-lookup"><span data-stu-id="fbda6-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="fbda6-119">Les éléments de tableau peuvent être de n’importe quel type, y compris un type tableau.</span><span class="sxs-lookup"><span data-stu-id="fbda6-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="fbda6-120">Les types tableau sont des [types référence](../../language-reference/keywords/reference-types.md) dérivés du type de base abstrait <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="fbda6-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="fbda6-121">Étant donné que ce type implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser l’itération [foreach](../../language-reference/keywords/foreach-in.md) sur tous les tableaux en C#.</span><span class="sxs-lookup"><span data-stu-id="fbda6-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

### <a name="arrays-as-objects"></a><span data-ttu-id="fbda6-122">Tableaux comme objets</span><span class="sxs-lookup"><span data-stu-id="fbda6-122">Arrays as Objects</span></span>

<span data-ttu-id="fbda6-123">En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++.</span><span class="sxs-lookup"><span data-stu-id="fbda6-123">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="fbda6-124"><xref:System.Array> est le type de base abstrait de tous les types de tableau.</span><span class="sxs-lookup"><span data-stu-id="fbda6-124"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="fbda6-125">Vous pouvez utiliser les propriétés et d’autres membres de classe qui <xref:System.Array> possèdent.</span><span class="sxs-lookup"><span data-stu-id="fbda6-125">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="fbda6-126">Par exemple, l’utilisation de la <xref:System.Array.Length%2A> propriété pour récupérer la longueur d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="fbda6-126">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="fbda6-127">Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="fbda6-127">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="fbda6-128">La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.</span><span class="sxs-lookup"><span data-stu-id="fbda6-128">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span> <span data-ttu-id="fbda6-129">L’exemple suivant utilise la <xref:System.Array.Rank%2A> propriété pour afficher le nombre de dimensions d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="fbda6-129">The following example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="fbda6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbda6-130">See also</span></span>

- [<span data-ttu-id="fbda6-131">Comment utiliser des tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="fbda6-131">How to use single-dimensional arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="fbda6-132">Comment utiliser des tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="fbda6-132">How to use multi-dimensional arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="fbda6-133">Comment utiliser des tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="fbda6-133">How to use jagged arrays</span></span>](jagged-arrays.md)
- [<span data-ttu-id="fbda6-134">Utilisation de foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="fbda6-134">Using foreach with arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="fbda6-135">Passage de tableaux en tant qu’arguments</span><span class="sxs-lookup"><span data-stu-id="fbda6-135">Passing arrays as arguments</span></span>](passing-arrays-as-arguments.md)
- [<span data-ttu-id="fbda6-136">Tableaux implicitement typés</span><span class="sxs-lookup"><span data-stu-id="fbda6-136">Implicitly typed arrays</span></span>](implicitly-typed-arrays.md)
- [<span data-ttu-id="fbda6-137">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fbda6-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fbda6-138">Regroupements</span><span class="sxs-lookup"><span data-stu-id="fbda6-138">Collections</span></span>](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
