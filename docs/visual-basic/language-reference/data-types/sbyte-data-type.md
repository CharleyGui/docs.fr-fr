---
title: SByte (type de données)
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415568"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="f1681-102">SByte, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1681-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="f1681-103">Contient des entiers 8 bits (1 octet) signés dont la valeur est comprise entre-128 et 127.</span><span class="sxs-lookup"><span data-stu-id="f1681-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1681-104">Notes</span><span class="sxs-lookup"><span data-stu-id="f1681-104">Remarks</span></span>

<span data-ttu-id="f1681-105">Utilisez le `SByte` type de données pour contenir des valeurs entières qui ne nécessitent pas la largeur complète des données `Integer` ou même la demi-largeur des données `Short` .</span><span class="sxs-lookup"><span data-stu-id="f1681-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="f1681-106">Dans certains cas, le common language runtime peut être en mesure de `SByte` regrouper vos variables de près et d’économiser la consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f1681-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="f1681-107">La valeur par défaut de `SByte` est 0.</span><span class="sxs-lookup"><span data-stu-id="f1681-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="f1681-108">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="f1681-108">Literal assignments</span></span>

<span data-ttu-id="f1681-109">Vous pouvez déclarer et initialiser une `SByte` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="f1681-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="f1681-110">Dans l’exemple suivant, les entiers égaux à-102 qui sont représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux `SByte` valeurs.</span><span class="sxs-lookup"><span data-stu-id="f1681-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="f1681-111">Cet exemple requiert que vous compiliez avec le `/removeintchecks` commutateur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="f1681-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="f1681-112">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="f1681-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="f1681-113">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="f1681-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f1681-114">À compter de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_` , comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f1681-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="f1681-115">À compter de Visual Basic 15,5, vous pouvez également utiliser le trait de soulignement ( `_` ) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux.</span><span class="sxs-lookup"><span data-stu-id="f1681-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="f1681-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f1681-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="f1681-117">Si le littéral entier est en dehors de la plage de `SByte` (autrement dit, s’il est inférieur à <xref:System.SByte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.SByte.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="f1681-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="f1681-118">Lorsqu’un littéral entier n’a pas de suffixe, un [entier](integer-data-type.md) est déduit.</span><span class="sxs-lookup"><span data-stu-id="f1681-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="f1681-119">Si le littéral entier est en dehors de la plage du `Integer` type, une [valeur long](long-data-type.md) est déduite.</span><span class="sxs-lookup"><span data-stu-id="f1681-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="f1681-120">Cela signifie que, dans les exemples précédents, les littéraux numériques `0x9A` et `0b10011010` sont interprétés comme des entiers signés 32 bits avec une valeur de 156, ce qui dépasse <xref:System.SByte.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f1681-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f1681-121">Pour compiler correctement du code comme celui-ci, qui assigne un entier non décimal à un `SByte` , vous pouvez effectuer l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1681-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="f1681-122">Désactivez les vérifications de limites d’entiers en compilant avec le `/removeintchecks` commutateur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="f1681-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="f1681-123">Utilisez un [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) pour définir explicitement la valeur littérale que vous souhaitez assigner à `SByte` .</span><span class="sxs-lookup"><span data-stu-id="f1681-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="f1681-124">L’exemple suivant assigne une valeur littérale négative `Short` à un `SByte` .</span><span class="sxs-lookup"><span data-stu-id="f1681-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="f1681-125">Notez que, pour les nombres négatifs, le bit de poids fort du mot de poids fort du littéral numérique doit être défini.</span><span class="sxs-lookup"><span data-stu-id="f1681-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="f1681-126">Dans le cas de notre exemple, il s’agit du bit 15 de la valeur littérale `Short` .</span><span class="sxs-lookup"><span data-stu-id="f1681-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="f1681-127">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="f1681-127">Programming tips</span></span>

- <span data-ttu-id="f1681-128">**Conformité CLS.**</span><span class="sxs-lookup"><span data-stu-id="f1681-128">**CLS Compliance.**</span></span> <span data-ttu-id="f1681-129">Le `SByte` type de données ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="f1681-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="f1681-130">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="f1681-130">**Widening.**</span></span> <span data-ttu-id="f1681-131">Le `SByte` type de données s’étend à `Short` , `Integer` ,,, `Long` `Decimal` `Single` et `Double` .</span><span class="sxs-lookup"><span data-stu-id="f1681-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="f1681-132">Cela signifie que vous pouvez `SByte` effectuer une conversion vers l’un de ces types sans rencontrer d' <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="f1681-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="f1681-133">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="f1681-133">**Type Characters.**</span></span> <span data-ttu-id="f1681-134">`SByte`n’a aucun caractère de type de littéral ou caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="f1681-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="f1681-135">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="f1681-135">**Framework Type.**</span></span> <span data-ttu-id="f1681-136">Le type correspondant dans le .NET Framework est la structure <xref:System.SByte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1681-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1681-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1681-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="f1681-138">Types de données</span><span class="sxs-lookup"><span data-stu-id="f1681-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="f1681-139">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="f1681-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="f1681-140">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="f1681-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="f1681-141">Court (type de données)</span><span class="sxs-lookup"><span data-stu-id="f1681-141">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="f1681-142">Entier (type de données)</span><span class="sxs-lookup"><span data-stu-id="f1681-142">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="f1681-143">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="f1681-143">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="f1681-144">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="f1681-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
