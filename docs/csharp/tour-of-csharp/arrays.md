---
title: Tableaux C# - Visite guidée du langage C#
description: Les tableaux constituent le type de collection le plus simple du langage C#
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 195df1f31c71ee7a202a3b57076775c4f717d399
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673314"
---
# <a name="arrays"></a><span data-ttu-id="f330f-103">Tableaux</span><span class="sxs-lookup"><span data-stu-id="f330f-103">Arrays</span></span>

<span data-ttu-id="f330f-104">Un ***tableau*** est une structure de données contenant un certain nombre de variables accessibles par le biais d’indices calculés.</span><span class="sxs-lookup"><span data-stu-id="f330f-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="f330f-105">Les variables contenues dans un tableau, également appelé ***éléments*** du tableau, sont tous du même type, et ce type est appelé ***type d’élément*** du tableau.</span><span class="sxs-lookup"><span data-stu-id="f330f-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="f330f-106">Les types tableau sont des types référence, et la déclaration d’une variable tableau réserve simplement un espace pour une référence à une instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="f330f-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="f330f-107">Les instances de tableau réelles sont créées dynamiquement lors de l’exécution à l’aide de l’opérateur new.</span><span class="sxs-lookup"><span data-stu-id="f330f-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="f330f-108">La nouvelle opération spécifie la ***longueur*** de la nouvelle instance de tableau, qui est ensuite fixée pour la durée de vie de l’instance.</span><span class="sxs-lookup"><span data-stu-id="f330f-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="f330f-109">Les indices des éléments d’un tableau vont de `0` à `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="f330f-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="f330f-110">L’opérateur `new` initialise automatiquement les éléments d’un tableau à leur valeur par défaut, c'est-à-dire, par exemple, zéro pour tous les types numériques et `null` pour tous les types référence.</span><span class="sxs-lookup"><span data-stu-id="f330f-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="f330f-111">L’exemple suivant crée un tableau de `int` éléments, initialise le tableau et imprime le contenu du tableau.</span><span class="sxs-lookup"><span data-stu-id="f330f-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="f330f-112">Cet exemple crée et utilise un ***tableau unidimensionnel***.</span><span class="sxs-lookup"><span data-stu-id="f330f-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="f330f-113">C# prend également en charge les ***tableaux multidimensionnels***.</span><span class="sxs-lookup"><span data-stu-id="f330f-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="f330f-114">Le nombre de dimensions d’un type tableau, également appelé ***rang*** du type tableau, est de un plus le nombre de virgules entre les crochets du type tableau.</span><span class="sxs-lookup"><span data-stu-id="f330f-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="f330f-115">L’exemple suivant alloue respectivement des tableaux à une seule, deux et trois dimensions, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f330f-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="f330f-116">Le tableau `a1` contient 10 éléments, le tableau `a2` en contient 50 (10 x 5) et le tableau `a3` en contient 100 (10 × 5 × 2).</span><span class="sxs-lookup"><span data-stu-id="f330f-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="f330f-117">Le type d’élément d’un tableau peut être de n’importe quel type, y compris un type tableau.</span><span class="sxs-lookup"><span data-stu-id="f330f-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="f330f-118">Un tableau avec des éléments d’un type tableau est parfois appelé un ***tableau en escalier***, car les longueurs des tableaux d’éléments ne sont pas nécessairement pas les mêmes.</span><span class="sxs-lookup"><span data-stu-id="f330f-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="f330f-119">L’exemple suivant alloue un tableau de tableaux de `int` :</span><span class="sxs-lookup"><span data-stu-id="f330f-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="f330f-120">La première ligne crée un tableau avec trois éléments, chacun de type `int[]` et chacun avec une valeur initiale de `null`.</span><span class="sxs-lookup"><span data-stu-id="f330f-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="f330f-121">Les lignes suivantes initialisent ensuite les trois éléments avec des références aux instances individuelles de tableau de longueur variable.</span><span class="sxs-lookup"><span data-stu-id="f330f-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="f330f-122">L’opérateur new autorise la spécification des valeurs initiales des éléments du tableau en utilisant un ***initialiseur de tableau***, qui est une liste d’expressions écrites entre les délimiteurs `{` et `}`.</span><span class="sxs-lookup"><span data-stu-id="f330f-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="f330f-123">L’exemple suivant alloue et initialise un `int[]` avec trois éléments.</span><span class="sxs-lookup"><span data-stu-id="f330f-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="f330f-124">Notez que la longueur du tableau est déduite à partir du nombre d’expressions entre { et }.</span><span class="sxs-lookup"><span data-stu-id="f330f-124">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="f330f-125">Les déclarations locales des champs et variables peuvent être abrégées davantage afin de ne pas avoir à redéclarer le type tableau.</span><span class="sxs-lookup"><span data-stu-id="f330f-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="f330f-126">Les deux exemples précédents sont équivalents à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="f330f-126">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="f330f-127">[Précédent](classes-and-objects.md)
>[Suivant](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="f330f-127">[Previous](classes-and-objects.md)
[Next](interfaces.md)</span></span>
