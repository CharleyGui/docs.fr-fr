---
title: Décimal (type de données)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 690c8061b6df1115aa24668520170b44edfa8287
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415645"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="0ca3e-102">Decimal, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca3e-102">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="0ca3e-103">Contient des valeurs 128 bits (16 octets) signées représentant des nombres entiers 96 bits (12 octets) mis à l’échelle par une puissance de variable de 10.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="0ca3e-104">Le facteur d’échelle spécifie le nombre de chiffres à droite de la virgule décimale ; elle est comprise entre 0 et 28.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="0ca3e-105">Avec une échelle de 0 (pas de décimale), la plus grande valeur possible est +/-79 228 162 514 264 337 593 543 950 335 (+/-7.9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="0ca3e-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="0ca3e-106">Avec 28 décimales, la plus grande valeur est +/-7,9228162514264337593543950335 et la plus petite valeur différente de zéro est +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="0ca3e-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="0ca3e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0ca3e-107">Remarks</span></span>

<span data-ttu-id="0ca3e-108">Le `Decimal` type de données fournit le plus grand nombre de chiffres significatifs pour un nombre.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="0ca3e-109">Il prend en charge jusqu’à 29 chiffres significatifs et peut représenter des valeurs dépassant 7,9228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="0ca3e-110">Elle est particulièrement adaptée aux calculs, tels que Financial, qui requièrent un grand nombre de chiffres, mais ne tolèrent pas les erreurs d’arrondi.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="0ca3e-111">La valeur par défaut de `Decimal` est 0.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-111">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="0ca3e-112">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="0ca3e-112">Programming Tips</span></span>

- <span data-ttu-id="0ca3e-113">**Précision.**</span><span class="sxs-lookup"><span data-stu-id="0ca3e-113">**Precision.**</span></span> <span data-ttu-id="0ca3e-114">`Decimal`n’est pas un type de données à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="0ca3e-115">La `Decimal` structure contient une valeur d’entier binaire, ainsi qu’un bit de signe et un facteur d’échelle d’entier qui spécifie la partie de la valeur qui est une fraction décimale.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="0ca3e-116">Pour cette raison, `Decimal` les nombres ont une représentation plus précise en mémoire que les types à virgule flottante ( `Single` et `Double` ).</span><span class="sxs-lookup"><span data-stu-id="0ca3e-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="0ca3e-117">**Niveau de performance.**</span><span class="sxs-lookup"><span data-stu-id="0ca3e-117">**Performance.**</span></span> <span data-ttu-id="0ca3e-118">Le `Decimal` type de données est le plus lent de tous les types numériques.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="0ca3e-119">Vous devez évaluer l’importance de la précision par rapport aux performances avant de choisir un type de données.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="0ca3e-120">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="0ca3e-120">**Widening.**</span></span> <span data-ttu-id="0ca3e-121">Le `Decimal` type de données s’étend à `Single` ou `Double` .</span><span class="sxs-lookup"><span data-stu-id="0ca3e-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="0ca3e-122">Cela signifie que vous pouvez `Decimal` effectuer une conversion vers l’un de ces types sans rencontrer d' <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="0ca3e-123">**Zéros de fin.**</span><span class="sxs-lookup"><span data-stu-id="0ca3e-123">**Trailing Zeros.**</span></span> <span data-ttu-id="0ca3e-124">Visual Basic ne stocke pas les zéros de fin dans un `Decimal` littéral.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="0ca3e-125">Toutefois, une `Decimal` variable conserve tous les zéros de fin acquis au calcul.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="0ca3e-126">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-126">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="0ca3e-127">La sortie de `MsgBox` dans l’exemple précédent est la suivante :</span><span class="sxs-lookup"><span data-stu-id="0ca3e-127">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="0ca3e-128">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="0ca3e-128">**Type Characters.**</span></span> <span data-ttu-id="0ca3e-129">L'ajout du caractère de type littéral `D` à un littéral force ce dernier en type de données `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-129">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="0ca3e-130">L'ajout du caractère de type identificateur `@` à un identificateur force ce dernier en type `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-130">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="0ca3e-131">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="0ca3e-131">**Framework Type.**</span></span> <span data-ttu-id="0ca3e-132">Le type correspondant dans le .NET Framework est la structure <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-132">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="0ca3e-133">Plage</span><span class="sxs-lookup"><span data-stu-id="0ca3e-133">Range</span></span>

 <span data-ttu-id="0ca3e-134">Vous devrez peut-être utiliser le `D` caractère de type pour affecter une valeur élevée à une `Decimal` variable ou une constante.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-134">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="0ca3e-135">Cette exigence est due au fait que le compilateur interprète un littéral comme, `Long` sauf si un caractère de type littéral suit le littéral, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-135">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="0ca3e-136">La déclaration pour `bigDec1` ne produit pas de dépassement de capacité, car la valeur qui lui est assignée est comprise dans la plage de `Long` .</span><span class="sxs-lookup"><span data-stu-id="0ca3e-136">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="0ca3e-137">La `Long` valeur peut être assignée à la `Decimal` variable.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-137">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="0ca3e-138">La déclaration pour `bigDec2` génère une erreur de dépassement de capacité, car la valeur qui lui est assignée est trop grande pour `Long` .</span><span class="sxs-lookup"><span data-stu-id="0ca3e-138">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="0ca3e-139">Étant donné que le littéral numérique ne peut pas être d’abord interprété comme un `Long` , il ne peut pas être assigné à la `Decimal` variable.</span><span class="sxs-lookup"><span data-stu-id="0ca3e-139">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="0ca3e-140">Pour `bigDec3` , le caractère de type de littéral `D` résout le problème en forçant le compilateur à interpréter le littéral comme un `Decimal` et non comme un `Long` .</span><span class="sxs-lookup"><span data-stu-id="0ca3e-140">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ca3e-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ca3e-141">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0ca3e-142">Types de données</span><span class="sxs-lookup"><span data-stu-id="0ca3e-142">Data Types</span></span>](index.md)
- [<span data-ttu-id="0ca3e-143">Single (type de données)</span><span class="sxs-lookup"><span data-stu-id="0ca3e-143">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="0ca3e-144">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="0ca3e-144">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="0ca3e-145">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="0ca3e-145">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="0ca3e-146">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="0ca3e-146">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="0ca3e-147">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="0ca3e-147">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
