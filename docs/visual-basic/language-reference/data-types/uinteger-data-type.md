---
title: UInteger (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400784"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="4b8d9-102">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="4b8d9-102">UInteger data type</span></span>

<span data-ttu-id="4b8d9-103">Détient des intégrés 32 bits non signés (4-byte) dont la valeur varie de 0 à 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b8d9-104">Notes </span><span class="sxs-lookup"><span data-stu-id="4b8d9-104">Remarks</span></span>

<span data-ttu-id="4b8d9-105">Le `UInteger` type de données fournit la plus grande valeur non signée dans la largeur de données la plus efficace.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="4b8d9-106">La valeur par défaut de `UInteger` est 0.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="4b8d9-107">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="4b8d9-107">Literal assignments</span></span>

<span data-ttu-id="4b8d9-108">Vous pouvez déclarer et `UInteger` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="4b8d9-109">Si le littéral entier est en dehors de la plage de `UInteger` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="4b8d9-110">Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="4b8d9-111">Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="4b8d9-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4b8d9-113">En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="4b8d9-114">En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4b8d9-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4b8d9-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="4b8d9-116">Les littérals numériques `ui` peuvent également inclure `UInteger` le caractère ou le `UI` [type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="4b8d9-117">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="4b8d9-117">Programming tips</span></span>

<span data-ttu-id="4b8d9-118">Les `UInteger` `Integer` types et les types de données offrent des performances optimales sur`UShort` `Short`un `Byte`processeur `SByte`32 bits, parce que les petits types d’intégreurs ( , , , , et ), même s’ils utilisent moins de bits, prendre plus de temps pour charger, stocker, et aller chercher.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="4b8d9-119">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="4b8d9-119">**Negative Numbers.**</span></span> <span data-ttu-id="4b8d9-120">Parce `UInteger` qu’il s’agit d’un type non signé, il ne peut pas représenter un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="4b8d9-121">Si vous utilisez l’opérateur unary moins (`-`) `UInteger`sur une expression qui `Long` évalue au type, Visual Basic convertit l’expression en premier.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="4b8d9-122">**Conformité CLS.**</span><span class="sxs-lookup"><span data-stu-id="4b8d9-122">**CLS Compliance.**</span></span> <span data-ttu-id="4b8d9-123">Le `UInteger` type de données ne fait pas partie de la [spécification de langue commune](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), de sorte que le code conforme à CLS ne peut pas consommer un composant qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="4b8d9-124">**Considérations sur l'interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="4b8d9-124">**Interop Considerations.**</span></span> <span data-ttu-id="4b8d9-125">Si vous entrelacez avec des composants non écrits pour le cadre .NET, par exemple `uint` des objets Automation ou COM, gardez à l’esprit que les types tels que peuvent avoir une largeur de données différente (16 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="4b8d9-126">Si vous passez un argument 16 bits à `UShort` un `UInteger` tel composant, déclarez-le comme au lieu de dans votre code de base visuel géré.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="4b8d9-127">**Élargissement.**</span><span class="sxs-lookup"><span data-stu-id="4b8d9-127">**Widening.**</span></span> <span data-ttu-id="4b8d9-128">Le `UInteger` type de `Long`données `ULong` `Decimal`s’élargit à , , , `Single`et `Double`.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="4b8d9-129">Cela signifie que `UInteger` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="4b8d9-130">**Personnages de type.**</span><span class="sxs-lookup"><span data-stu-id="4b8d9-130">**Type Characters.**</span></span> <span data-ttu-id="4b8d9-131">Appending les caractères `UI` de type littéral `UInteger` à un littéral le force au type de données.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="4b8d9-132">`UInteger`n’a pas de caractère de type identificateur.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="4b8d9-133">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="4b8d9-133">**Framework Type.**</span></span> <span data-ttu-id="4b8d9-134">Le type correspondant dans le .NET Framework est la structure <xref:System.UInt32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b8d9-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b8d9-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b8d9-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="4b8d9-136">Types de données</span><span class="sxs-lookup"><span data-stu-id="4b8d9-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="4b8d9-137">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="4b8d9-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="4b8d9-138">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="4b8d9-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="4b8d9-139">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="4b8d9-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="4b8d9-140">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="4b8d9-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
