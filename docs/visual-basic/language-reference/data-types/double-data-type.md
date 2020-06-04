---
title: Double (type de données)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 899554f427ac77ead465752c35e51ca88d045763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415632"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="1b7ae-102">Double, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b7ae-102">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="1b7ae-103">Contient des nombres à virgule flottante double précision IEEE 64 bits (8 octets) qui comprisent entre-1.79769313486231570 E + 308 et-4.94065645841246544 E-324 pour les valeurs négatives et de 4.94065645841246544 E-324 à 1.79769313486231570 E + 308 pour les valeurs positives.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="1b7ae-104">Les nombres à double précision stockent une approximation d’un nombre réel.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-104">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b7ae-105">Notes</span><span class="sxs-lookup"><span data-stu-id="1b7ae-105">Remarks</span></span>

<span data-ttu-id="1b7ae-106">Le `Double` type de données fournit les plus grandes et les plus petites amplitudes possibles pour un nombre.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="1b7ae-107">La valeur par défaut de `Double` est 0.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-107">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="1b7ae-108">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="1b7ae-108">Programming Tips</span></span>

- <span data-ttu-id="1b7ae-109">**Précision.**</span><span class="sxs-lookup"><span data-stu-id="1b7ae-109">**Precision.**</span></span> <span data-ttu-id="1b7ae-110">Lorsque vous utilisez des nombres à virgule flottante, n’oubliez pas qu’ils n’ont pas toujours une représentation précise en mémoire.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="1b7ae-111">Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l' `Mod` opérateur.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="1b7ae-112">Pour plus d’informations, consultez [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="1b7ae-112">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="1b7ae-113">**Zéros de fin.**</span><span class="sxs-lookup"><span data-stu-id="1b7ae-113">**Trailing Zeros.**</span></span> <span data-ttu-id="1b7ae-114">Les types de données à virgule flottante n’ont pas de représentation interne des zéros de fin.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="1b7ae-115">Par exemple, ils ne font pas la distinction entre 4,2000 et 4,2.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="1b7ae-116">Par conséquent, aucun caractère de fin ne s’affiche lorsque vous affichez ou imprimez des valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="1b7ae-117">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="1b7ae-117">**Type Characters.**</span></span> <span data-ttu-id="1b7ae-118">L'ajout du caractère de type littéral `R` à un littéral force ce dernier en type de données `Double`.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="1b7ae-119">Par exemple, si une valeur entière est suivie de `R` , la valeur est remplacée par `Double` .</span><span class="sxs-lookup"><span data-stu-id="1b7ae-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="1b7ae-120">L'ajout du caractère de type identificateur `#` à un identificateur force ce dernier en type `Double`.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="1b7ae-121">Dans l’exemple suivant, la variable `num` est de type `Double` :</span><span class="sxs-lookup"><span data-stu-id="1b7ae-121">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="1b7ae-122">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="1b7ae-122">**Framework Type.**</span></span> <span data-ttu-id="1b7ae-123">Le type correspondant dans le .NET Framework est la structure <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b7ae-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b7ae-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b7ae-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="1b7ae-125">Types de données</span><span class="sxs-lookup"><span data-stu-id="1b7ae-125">Data Types</span></span>](index.md)
- [<span data-ttu-id="1b7ae-126">Décimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="1b7ae-126">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="1b7ae-127">Single (type de données)</span><span class="sxs-lookup"><span data-stu-id="1b7ae-127">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="1b7ae-128">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="1b7ae-128">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="1b7ae-129">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="1b7ae-129">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="1b7ae-130">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="1b7ae-130">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="1b7ae-131">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="1b7ae-131">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="1b7ae-132">Caractères de type</span><span class="sxs-lookup"><span data-stu-id="1b7ae-132">Type Characters</span></span>](../../programming-guide/language-features/data-types/type-characters.md)
