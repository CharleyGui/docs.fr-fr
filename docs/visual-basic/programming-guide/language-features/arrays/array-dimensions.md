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
ms.openlocfilehash: 12e983ae62fa9f9ea762d434ffe5b73873a4a2e8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351907"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="21d64-102">Dimensions du tableau dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21d64-102">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="21d64-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span><span class="sxs-lookup"><span data-stu-id="21d64-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="21d64-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span><span class="sxs-lookup"><span data-stu-id="21d64-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="21d64-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span><span class="sxs-lookup"><span data-stu-id="21d64-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="21d64-106">The number of dimensions an array has is called its *rank*.</span><span class="sxs-lookup"><span data-stu-id="21d64-106">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="21d64-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span><span class="sxs-lookup"><span data-stu-id="21d64-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="21d64-108">Working with Dimensions</span><span class="sxs-lookup"><span data-stu-id="21d64-108">Working with Dimensions</span></span>

<span data-ttu-id="21d64-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span><span class="sxs-lookup"><span data-stu-id="21d64-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="21d64-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span><span class="sxs-lookup"><span data-stu-id="21d64-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="21d64-111">The following illustrations show the conceptual structure of arrays with different ranks.</span><span class="sxs-lookup"><span data-stu-id="21d64-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="21d64-112">Each element in the illustrations shows the index values that access it.</span><span class="sxs-lookup"><span data-stu-id="21d64-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="21d64-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="21d64-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![Diagram that shows a one-dimensional array.](./media/array-dimensions/one-dimensional-array.gif)

![Diagram that shows a two-dimensional array.](./media/array-dimensions/two-dimensional-array.gif)

![Diagram that shows a three-dimensional array.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="21d64-117">One Dimension</span><span class="sxs-lookup"><span data-stu-id="21d64-117">One Dimension</span></span>

<span data-ttu-id="21d64-118">Many arrays have only one dimension, such as the number of people of each age.</span><span class="sxs-lookup"><span data-stu-id="21d64-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="21d64-119">The only requirement to specify an element is the age for which that element holds the count.</span><span class="sxs-lookup"><span data-stu-id="21d64-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="21d64-120">Therefore, such an array uses only one index.</span><span class="sxs-lookup"><span data-stu-id="21d64-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="21d64-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span><span class="sxs-lookup"><span data-stu-id="21d64-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="21d64-122">Two Dimensions</span><span class="sxs-lookup"><span data-stu-id="21d64-122">Two Dimensions</span></span>

<span data-ttu-id="21d64-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span><span class="sxs-lookup"><span data-stu-id="21d64-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="21d64-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span><span class="sxs-lookup"><span data-stu-id="21d64-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="21d64-125">Therefore, such an array uses two indexes.</span><span class="sxs-lookup"><span data-stu-id="21d64-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="21d64-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span><span class="sxs-lookup"><span data-stu-id="21d64-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="21d64-127">A two-dimensional array is also called a *rectangular array*.</span><span class="sxs-lookup"><span data-stu-id="21d64-127">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="21d64-128">Three Dimensions</span><span class="sxs-lookup"><span data-stu-id="21d64-128">Three Dimensions</span></span>

<span data-ttu-id="21d64-129">A few arrays have three dimensions, such as values in three-dimensional space.</span><span class="sxs-lookup"><span data-stu-id="21d64-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="21d64-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span><span class="sxs-lookup"><span data-stu-id="21d64-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="21d64-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span><span class="sxs-lookup"><span data-stu-id="21d64-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="21d64-132">More than Three Dimensions</span><span class="sxs-lookup"><span data-stu-id="21d64-132">More than Three Dimensions</span></span>

<span data-ttu-id="21d64-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span><span class="sxs-lookup"><span data-stu-id="21d64-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="21d64-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span><span class="sxs-lookup"><span data-stu-id="21d64-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="21d64-135">Using Different Dimensions</span><span class="sxs-lookup"><span data-stu-id="21d64-135">Using Different Dimensions</span></span>

<span data-ttu-id="21d64-136">Suppose you want to track sales amounts for every day of the present month.</span><span class="sxs-lookup"><span data-stu-id="21d64-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="21d64-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="21d64-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="21d64-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span><span class="sxs-lookup"><span data-stu-id="21d64-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="21d64-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="21d64-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="21d64-140">Now suppose you decide to have your array hold information for more than one year.</span><span class="sxs-lookup"><span data-stu-id="21d64-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="21d64-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="21d64-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="21d64-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span><span class="sxs-lookup"><span data-stu-id="21d64-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="21d64-143">Note also that the size of the array increases with each new dimension.</span><span class="sxs-lookup"><span data-stu-id="21d64-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="21d64-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span><span class="sxs-lookup"><span data-stu-id="21d64-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="21d64-145">You can create an array without using the `Dim` statement or the `New` clause.</span><span class="sxs-lookup"><span data-stu-id="21d64-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="21d64-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span><span class="sxs-lookup"><span data-stu-id="21d64-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="21d64-147">Such an array can have a lower bound other than 0.</span><span class="sxs-lookup"><span data-stu-id="21d64-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="21d64-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span><span class="sxs-lookup"><span data-stu-id="21d64-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="21d64-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21d64-149">See also</span></span>

- [<span data-ttu-id="21d64-150">Tableaux</span><span class="sxs-lookup"><span data-stu-id="21d64-150">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="21d64-151">Dépannage des tableaux</span><span class="sxs-lookup"><span data-stu-id="21d64-151">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
