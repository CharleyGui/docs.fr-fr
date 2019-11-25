---
title: Single, type de données
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343919"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="68880-102">Single, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68880-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="68880-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span><span class="sxs-lookup"><span data-stu-id="68880-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="68880-104">Single-precision numbers store an approximation of a real number.</span><span class="sxs-lookup"><span data-stu-id="68880-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68880-105">Notes</span><span class="sxs-lookup"><span data-stu-id="68880-105">Remarks</span></span>  

 <span data-ttu-id="68880-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span><span class="sxs-lookup"><span data-stu-id="68880-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="68880-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span><span class="sxs-lookup"><span data-stu-id="68880-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="68880-108">La valeur par défaut de `Single` est 0.</span><span class="sxs-lookup"><span data-stu-id="68880-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="68880-109">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="68880-109">Programming Tips</span></span>  
  
- <span data-ttu-id="68880-110">**Precision.**</span><span class="sxs-lookup"><span data-stu-id="68880-110">**Precision.**</span></span> <span data-ttu-id="68880-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span><span class="sxs-lookup"><span data-stu-id="68880-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="68880-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span><span class="sxs-lookup"><span data-stu-id="68880-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="68880-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="68880-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="68880-114">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="68880-114">**Widening.**</span></span> <span data-ttu-id="68880-115">The `Single` data type widens to `Double`.</span><span class="sxs-lookup"><span data-stu-id="68880-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="68880-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span><span class="sxs-lookup"><span data-stu-id="68880-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="68880-117">**Trailing Zeros.**</span><span class="sxs-lookup"><span data-stu-id="68880-117">**Trailing Zeros.**</span></span> <span data-ttu-id="68880-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span><span class="sxs-lookup"><span data-stu-id="68880-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="68880-119">For example, they do not distinguish between 4.2000 and 4.2.</span><span class="sxs-lookup"><span data-stu-id="68880-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="68880-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span><span class="sxs-lookup"><span data-stu-id="68880-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="68880-121">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="68880-121">**Type Characters.**</span></span> <span data-ttu-id="68880-122">L'ajout du caractère de type littéral `F` à un littéral force ce dernier en type de données `Single`.</span><span class="sxs-lookup"><span data-stu-id="68880-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="68880-123">L'ajout du caractère de type identificateur `!` à un identificateur force ce dernier en type `Single`.</span><span class="sxs-lookup"><span data-stu-id="68880-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="68880-124">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="68880-124">**Framework Type.**</span></span> <span data-ttu-id="68880-125">Le type correspondant dans le .NET Framework est la structure <xref:System.Single?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="68880-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68880-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68880-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="68880-127">Types de données</span><span class="sxs-lookup"><span data-stu-id="68880-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="68880-128">Decimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="68880-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="68880-129">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="68880-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="68880-130">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="68880-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="68880-131">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="68880-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="68880-132">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="68880-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="68880-133">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="68880-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
