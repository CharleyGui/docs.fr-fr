---
title: Dimensions du tableau
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: f971f0c3693177adbcb8869d487e3ad41d49ddc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413102"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="f7e4d-102">Dimensions du tableau dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f7e4d-102">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="f7e4d-103">Une *dimension* est un sens dans lequel vous pouvez faire varier la spécification des éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="f7e4d-104">Un tableau qui contient le total des ventes pour chaque jour du mois a une dimension (le jour du mois).</span><span class="sxs-lookup"><span data-stu-id="f7e4d-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="f7e4d-105">Un tableau qui contient le total des ventes par département pour chaque jour du mois a deux dimensions (le numéro de service et le jour du mois).</span><span class="sxs-lookup"><span data-stu-id="f7e4d-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="f7e4d-106">Le nombre de dimensions d’un tableau est appelé son *rang*.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-106">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="f7e4d-107">Vous pouvez utiliser la <xref:System.Array.Rank%2A> propriété pour déterminer le nombre de dimensions d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="f7e4d-108">Utilisation de dimensions</span><span class="sxs-lookup"><span data-stu-id="f7e4d-108">Working with Dimensions</span></span>

<span data-ttu-id="f7e4d-109">Vous spécifiez un élément d’un tableau en fournissant un *index* ou un *indice* pour chacune de ses dimensions.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="f7e4d-110">Les éléments sont contigus le long de chaque dimension à partir de l’index 0 jusqu’à l’index le plus élevé pour cette dimension.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="f7e4d-111">Les illustrations suivantes montrent la structure conceptuelle des tableaux avec des rangs différents.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="f7e4d-112">Chaque élément dans les illustrations affiche les valeurs d’index qui y accèdent.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="f7e4d-113">Par exemple, vous pouvez accéder au premier élément de la deuxième ligne du tableau à deux dimensions en spécifiant des index `(1, 0)` .</span><span class="sxs-lookup"><span data-stu-id="f7e4d-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![Diagramme qui montre un tableau unidimensionnel.](./media/array-dimensions/one-dimensional-array.gif)

![Diagramme qui montre un tableau à deux dimensions.](./media/array-dimensions/two-dimensional-array.gif)

![Diagramme qui montre un tableau à trois dimensions.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="f7e4d-117">Une dimension</span><span class="sxs-lookup"><span data-stu-id="f7e4d-117">One Dimension</span></span>

<span data-ttu-id="f7e4d-118">De nombreux tableaux n’ont qu’une seule dimension, comme le nombre de personnes de chaque âge.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="f7e4d-119">La seule condition requise pour spécifier un élément est l’âge pour lequel cet élément contient le nombre.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="f7e4d-120">Par conséquent, un tel tableau utilise un seul index.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="f7e4d-121">L’exemple suivant déclare une variable qui doit contenir un *tableau unidimensionnel* de nombres d’âge pour les âges de 0 à 120.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="f7e4d-122">Deux dimensions</span><span class="sxs-lookup"><span data-stu-id="f7e4d-122">Two Dimensions</span></span>

<span data-ttu-id="f7e4d-123">Certains tableaux ont deux dimensions, telles que le nombre de bureaux à chaque étage de chaque bâtiment sur un campus.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="f7e4d-124">La spécification d’un élément nécessite à la fois le numéro de bâtiment et le plancher, et chaque élément contient le nombre pour cette combinaison de construction et d’étage.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="f7e4d-125">Par conséquent, un tel tableau utilise deux index.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="f7e4d-126">L’exemple suivant déclare une variable destinée à contenir un *tableau à deux dimensions* de nombres de bureaux, pour les bâtiments de 0 à 40 et les étages de 0 à 5.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="f7e4d-127">Un tableau à deux dimensions est également appelé *tableau rectangulaire*.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-127">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="f7e4d-128">Trois dimensions</span><span class="sxs-lookup"><span data-stu-id="f7e4d-128">Three Dimensions</span></span>

<span data-ttu-id="f7e4d-129">Quelques tableaux ont trois dimensions, telles que des valeurs dans un espace tridimensionnel.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="f7e4d-130">Ce type de tableau utilise trois index, qui dans ce cas représentent les coordonnées x, y et z de l’espace physique.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="f7e4d-131">L’exemple suivant déclare une variable qui doit contenir un *tableau à trois dimensions* de températures atmosphériques à différents points d’un volume tridimensionnel.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="f7e4d-132">Plus de trois dimensions</span><span class="sxs-lookup"><span data-stu-id="f7e4d-132">More than Three Dimensions</span></span>

<span data-ttu-id="f7e4d-133">Bien qu’un tableau puisse avoir jusqu’à 32 dimensions, il est rare d’en avoir plus de trois.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="f7e4d-134">Lorsque vous ajoutez des dimensions à un tableau, le stockage total requis par le tableau augmente considérablement, donc utilisez des tableaux multidimensionnels avec précaution.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="f7e4d-135">Utilisation de différentes dimensions</span><span class="sxs-lookup"><span data-stu-id="f7e4d-135">Using Different Dimensions</span></span>

<span data-ttu-id="f7e4d-136">Supposons que vous souhaitez effectuer le suivi des montants des ventes pour chaque jour du mois présent.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="f7e4d-137">Vous pouvez déclarer un tableau unidimensionnel avec 31 éléments, un pour chaque jour du mois, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="f7e4d-138">Supposons à présent que vous souhaitiez suivre les mêmes informations non seulement pour chaque jour du mois, mais également pour chaque mois de l’année.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="f7e4d-139">Vous pouvez déclarer un tableau à deux dimensions avec 12 lignes (pour les mois) et 31 colonnes (pour les jours), comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="f7e4d-140">Supposons à présent que vous décidiez que votre tableau conserve les informations pendant plus d’un an.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="f7e4d-141">Si vous souhaitez effectuer le suivi des montants des ventes pendant 5 ans, vous pouvez déclarer un tableau à trois dimensions avec 5 couches, 12 lignes et 31 colonnes, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="f7e4d-142">Notez que, étant donné que chaque index varie de 0 à son maximum, chaque dimension de `salesAmounts` est déclarée comme une valeur inférieure à la longueur requise pour cette dimension.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="f7e4d-143">Notez également que la taille du tableau augmente avec chaque nouvelle dimension.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="f7e4d-144">Les trois tailles dans les exemples précédents sont respectivement 31, 372 et 1 860 éléments.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="f7e4d-145">Vous pouvez créer un tableau sans utiliser l' `Dim` instruction ou la `New` clause.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="f7e4d-146">Par exemple, vous pouvez appeler la <xref:System.Array.CreateInstance%2A> méthode, ou un autre composant peut passer votre code à un tableau créé de cette manière.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="f7e4d-147">Un tel tableau peut avoir une limite inférieure différente de 0.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="f7e4d-148">Vous pouvez toujours tester la limite inférieure d’une dimension à l’aide de la <xref:System.Array.GetLowerBound%2A> méthode ou de la `LBound` fonction.</span><span class="sxs-lookup"><span data-stu-id="f7e4d-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7e4d-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7e4d-149">See also</span></span>

- [<span data-ttu-id="f7e4d-150">Tableaux</span><span class="sxs-lookup"><span data-stu-id="f7e4d-150">Arrays</span></span>](index.md)
- [<span data-ttu-id="f7e4d-151">Résolution des problèmes de tableaux</span><span class="sxs-lookup"><span data-stu-id="f7e4d-151">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
