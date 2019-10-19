---
title: Long, type de données (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: efbe54c2495d05e8fe215690f60ba3c7ea9cfef6
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582524"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="85790-102">Long, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85790-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="85790-103">Contient des entiers 64 bits (8 octets) signés dont la valeur est comprise entre-9223372036854775808 et 9 223 372 036 854 775 807 (9.2... E + 18).</span><span class="sxs-lookup"><span data-stu-id="85790-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="85790-104">Notes</span><span class="sxs-lookup"><span data-stu-id="85790-104">Remarks</span></span>

<span data-ttu-id="85790-105">Utilisez le type de données `Long` pour contenir des nombres entiers trop grands pour être contenus dans le type de données `Integer`.</span><span class="sxs-lookup"><span data-stu-id="85790-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="85790-106">La valeur par défaut de `Long` est 0.</span><span class="sxs-lookup"><span data-stu-id="85790-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="85790-107">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="85790-107">Literal assignments</span></span>

<span data-ttu-id="85790-108">Vous pouvez déclarer et initialiser une variable `Long` en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="85790-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="85790-109">Si le littéral entier est en dehors de la plage de `Long` (autrement dit, s’il est inférieur à <xref:System.Int64.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int64.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="85790-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="85790-110">Dans l’exemple suivant, les entiers égaux à 4 294 967 296 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `Long`.</span><span class="sxs-lookup"><span data-stu-id="85790-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="85790-111">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="85790-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="85790-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="85790-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="85790-113">À compter de Visual Basic 2017, vous pouvez également utiliser le trait de soulignement, `_`, comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="85790-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="85790-114">À compter de Visual Basic 15,5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux.</span><span class="sxs-lookup"><span data-stu-id="85790-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="85790-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="85790-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="85790-116">Les littéraux numériques peuvent également inclure le [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) `L` pour désigner le type de données `Long`, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="85790-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="85790-117">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="85790-117">Programming tips</span></span>

- <span data-ttu-id="85790-118">**Considérations relatives à l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="85790-118">**Interop Considerations.**</span></span> <span data-ttu-id="85790-119">Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que `Long` a une largeur de données différente (32 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="85790-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="85790-120">Si vous passez un argument 32 bits à un tel composant, déclarez-le comme `Integer` au lieu de `Long` dans votre nouveau code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="85790-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="85790-121">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="85790-121">**Widening.**</span></span> <span data-ttu-id="85790-122">Le type de données `Long` s’étend à `Decimal`, `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="85790-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="85790-123">Cela signifie que vous pouvez convertir `Long` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85790-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="85790-124">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="85790-124">**Type Characters.**</span></span> <span data-ttu-id="85790-125">L'ajout du caractère de type littéral `L` à un littéral force ce dernier en type de données `Long`.</span><span class="sxs-lookup"><span data-stu-id="85790-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="85790-126">L'ajout du caractère de type identificateur `&` à un identificateur force ce dernier en type `Long`.</span><span class="sxs-lookup"><span data-stu-id="85790-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="85790-127">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="85790-127">**Framework Type.**</span></span> <span data-ttu-id="85790-128">Le type correspondant dans le .NET Framework est la structure <xref:System.Int64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85790-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="85790-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85790-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="85790-130">Types de données</span><span class="sxs-lookup"><span data-stu-id="85790-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="85790-131">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="85790-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="85790-132">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="85790-132">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="85790-133">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="85790-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="85790-134">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="85790-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="85790-135">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="85790-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
