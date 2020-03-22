---
title: Long (type de données)
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
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400812"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="0dc1d-102">Type de données longue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dc1d-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="0dc1d-103">Détient signé 64 bits (8-byte) integers allant de -9 223 372 036 854 775 808 à 9 223 372 036 854 775 807 (9,2...E-18).</span><span class="sxs-lookup"><span data-stu-id="0dc1d-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="0dc1d-104">Notes </span><span class="sxs-lookup"><span data-stu-id="0dc1d-104">Remarks</span></span>

<span data-ttu-id="0dc1d-105">Utilisez `Long` le type de données pour contenir des nombres `Integer` d’intégrants trop grands pour s’adapter au type de données.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="0dc1d-106">La valeur par défaut de `Long` est 0.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="0dc1d-107">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="0dc1d-107">Literal assignments</span></span>

<span data-ttu-id="0dc1d-108">Vous pouvez déclarer et `Long` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="0dc1d-109">Si le littéral entier est en dehors de la plage de `Long` (autrement dit, s’il est inférieur à <xref:System.Int64.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int64.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="0dc1d-110">Dans l’exemple suivant, les entiers égaux à 4 294 967 296 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `Long`.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="0dc1d-111">Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="0dc1d-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="0dc1d-113">En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="0dc1d-114">En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="0dc1d-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0dc1d-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="0dc1d-116">Les littérals numériques peuvent également inclure le `L` [caractère type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le `Long` type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="0dc1d-117">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="0dc1d-117">Programming tips</span></span>

- <span data-ttu-id="0dc1d-118">**Considérations sur l'interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="0dc1d-118">**Interop Considerations.**</span></span> <span data-ttu-id="0dc1d-119">Si vous entrelacez avec des composants non écrits pour le cadre .NET, par exemple des objets Automation ou COM, rappelez-vous que `Long` la largeur des données est différente (32 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="0dc1d-120">Si vous passez un argument 32 bits à `Integer` un `Long` tel composant, déclarez-le comme au lieu de dans votre nouveau code de base visuelle.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="0dc1d-121">**Élargissement.**</span><span class="sxs-lookup"><span data-stu-id="0dc1d-121">**Widening.**</span></span> <span data-ttu-id="0dc1d-122">Le `Long` type de `Decimal`données `Single`s’élargit à , , ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="0dc1d-123">Cela signifie que vous pouvez convertir `Long` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="0dc1d-124">**Personnages de type.**</span><span class="sxs-lookup"><span data-stu-id="0dc1d-124">**Type Characters.**</span></span> <span data-ttu-id="0dc1d-125">L'ajout du caractère de type littéral `L` à un littéral force ce dernier en type de données `Long`.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="0dc1d-126">L'ajout du caractère de type identificateur `&` à un identificateur force ce dernier en type `Long`.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="0dc1d-127">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="0dc1d-127">**Framework Type.**</span></span> <span data-ttu-id="0dc1d-128">Le type correspondant dans le .NET Framework est la structure <xref:System.Int64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dc1d-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="0dc1d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dc1d-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="0dc1d-130">Types de données</span><span class="sxs-lookup"><span data-stu-id="0dc1d-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0dc1d-131">Type de données integer</span><span class="sxs-lookup"><span data-stu-id="0dc1d-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="0dc1d-132">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="0dc1d-132">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="0dc1d-133">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="0dc1d-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0dc1d-134">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="0dc1d-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="0dc1d-135">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="0dc1d-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
