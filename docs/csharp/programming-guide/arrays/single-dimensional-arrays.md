---
title: Tableaux unidimensionnels - Guide de programmation C#
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: e189253eedc21fa2d51e16407f04b034610bb57b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410242"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="5317a-102">Tableaux unidimensionnels (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5317a-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5317a-103">Vous créez un tableau unidimensionnel à l’aide de l’opérateur [New](../../language-reference/operators/new-operator.md) en spécifiant le type d’élément de tableau et le nombre d’éléments.</span><span class="sxs-lookup"><span data-stu-id="5317a-103">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="5317a-104">L’exemple suivant déclare un tableau de cinq entiers :</span><span class="sxs-lookup"><span data-stu-id="5317a-104">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="5317a-105">Ce tableau contient les éléments de `array[0]` à `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="5317a-105">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="5317a-106">Les éléments du tableau sont initialisés à la valeur par défaut du type d’élément, `0` pour les entiers.</span><span class="sxs-lookup"><span data-stu-id="5317a-106">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="5317a-107">Les tableaux peuvent stocker tout type d’élément que vous spécifiez, comme dans l’exemple suivant, qui déclare un tableau de chaînes :</span><span class="sxs-lookup"><span data-stu-id="5317a-107">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="5317a-108">Initialisation du tableau</span><span class="sxs-lookup"><span data-stu-id="5317a-108">Array Initialization</span></span>

<span data-ttu-id="5317a-109">Vous pouvez initialiser les éléments d’un tableau lorsque vous déclarez le tableau.</span><span class="sxs-lookup"><span data-stu-id="5317a-109">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="5317a-110">Le spécificateur de longueur n’est pas nécessaire, car il est déduit par le nombre d’éléments dans la liste d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="5317a-110">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="5317a-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5317a-111">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="5317a-112">Le code suivant illustre une déclaration d’un tableau de chaînes où chaque élément de tableau est initialisé par un nom de jour :</span><span class="sxs-lookup"><span data-stu-id="5317a-112">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="5317a-113">Vous pouvez éviter l' `new` expression et le type de tableau lorsque vous initialisez un tableau lors de la déclaration, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="5317a-113">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="5317a-114">C’est ce qu’on appelle un [tableau implicitement typé](implicitly-typed-arrays.md):</span><span class="sxs-lookup"><span data-stu-id="5317a-114">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="5317a-115">Vous pouvez déclarer une variable tableau sans la créer, mais vous devez utiliser l' `new` opérateur quand vous assignez un nouveau tableau à cette variable.</span><span class="sxs-lookup"><span data-stu-id="5317a-115">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="5317a-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5317a-116">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="5317a-117">Tableaux de types valeur et de types référence</span><span class="sxs-lookup"><span data-stu-id="5317a-117">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="5317a-118">Considérons la déclaration de tableau suivante :</span><span class="sxs-lookup"><span data-stu-id="5317a-118">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="5317a-119">Le résultat de cette instruction varie selon que `SomeType` est un type valeur ou un type référence.</span><span class="sxs-lookup"><span data-stu-id="5317a-119">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="5317a-120">S’il s’agit d’un type valeur, l’instruction crée un tableau de 10 éléments, chacun d’entre eux ayant le type `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="5317a-120">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="5317a-121">Si `SomeType` est un type référence, l’instruction crée un tableau de 10 éléments dont chacun est initialisé avec une référence null.</span><span class="sxs-lookup"><span data-stu-id="5317a-121">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="5317a-122">Dans les deux instances, les éléments sont initialisés à la valeur par défaut pour le type d’élément.</span><span class="sxs-lookup"><span data-stu-id="5317a-122">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="5317a-123">Pour plus d’informations sur les types valeur et les types référence, consultez types [valeur](../../language-reference/builtin-types/value-types.md) et [types référence](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="5317a-123">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5317a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5317a-124">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="5317a-125">Tableaux</span><span class="sxs-lookup"><span data-stu-id="5317a-125">Arrays</span></span>](./index.md)
- [<span data-ttu-id="5317a-126">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="5317a-126">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="5317a-127">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="5317a-127">Jagged Arrays</span></span>](./jagged-arrays.md)
