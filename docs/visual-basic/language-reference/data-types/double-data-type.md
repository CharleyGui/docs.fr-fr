---
title: Double, type de données (Visual Basic)
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
ms.openlocfilehash: 92adb26702d94dee08e51decd845d019c797e195
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630100"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="0c1d2-102">Double, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c1d2-102">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="0c1d2-103">Contient des nombres à virgule flottante double précision IEEE 64 bits (8 octets) qui comprises dans la valeur de-1.79769313486231570 E + 308 à-4.94065645841246544 E-324 pour les valeurs négatives et de 4.94065645841246544 E-324 à 1.79769313486231570 E + 308 pour valeurs positives.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="0c1d2-104">Les nombres à double précision stockent une approximation d’un nombre réel.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-104">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c1d2-105">Notes</span><span class="sxs-lookup"><span data-stu-id="0c1d2-105">Remarks</span></span>

<span data-ttu-id="0c1d2-106">Le `Double` type de données fournit les plus grandes et les plus petites amplitudes possibles pour un nombre.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="0c1d2-107">La valeur par défaut de `Double` est 0.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-107">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="0c1d2-108">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="0c1d2-108">Programming Tips</span></span>

- <span data-ttu-id="0c1d2-109">**Précision.**</span><span class="sxs-lookup"><span data-stu-id="0c1d2-109">**Precision.**</span></span> <span data-ttu-id="0c1d2-110">Lorsque vous utilisez des nombres à virgule flottante, n’oubliez pas qu’ils n’ont pas toujours une représentation précise en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="0c1d2-111">Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison `Mod` de valeurs et l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="0c1d2-112">Pour plus d’informations, consultez [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="0c1d2-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="0c1d2-113">**Zéros de fin.**</span><span class="sxs-lookup"><span data-stu-id="0c1d2-113">**Trailing Zeros.**</span></span> <span data-ttu-id="0c1d2-114">Les types de données à virgule flottante n’ont pas de représentation interne des zéros de fin.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="0c1d2-115">Par exemple, ils ne font pas la distinction entre 4,2000 et 4,2.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="0c1d2-116">Par conséquent, aucun caractère de fin ne s’affiche lorsque vous affichez ou imprimez des valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="0c1d2-117">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="0c1d2-117">**Type Characters.**</span></span> <span data-ttu-id="0c1d2-118">L'ajout du caractère de type littéral `R` à un littéral force ce dernier en type de données `Double`.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="0c1d2-119">Par exemple, si une valeur entière est suivie de `R`, la valeur est remplacée `Double`par.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="0c1d2-120">L'ajout du caractère de type identificateur `#` à un identificateur force ce dernier en type `Double`.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="0c1d2-121">Dans l’exemple suivant, la variable `num` est de type: `Double`</span><span class="sxs-lookup"><span data-stu-id="0c1d2-121">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="0c1d2-122">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="0c1d2-122">**Framework Type.**</span></span> <span data-ttu-id="0c1d2-123">Le type correspondant dans le .NET Framework est la structure <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1d2-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c1d2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c1d2-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="0c1d2-125">Types de données</span><span class="sxs-lookup"><span data-stu-id="0c1d2-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0c1d2-126">Decimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="0c1d2-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="0c1d2-127">Single (type de données)</span><span class="sxs-lookup"><span data-stu-id="0c1d2-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="0c1d2-128">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="0c1d2-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0c1d2-129">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="0c1d2-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="0c1d2-130">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="0c1d2-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="0c1d2-131">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="0c1d2-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="0c1d2-132">Caractères de type</span><span class="sxs-lookup"><span data-stu-id="0c1d2-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
