---
title: UShort (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400693"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="b4889-102">Type de données UShort (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4889-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="b4889-103">Détient des 16 pouces non signés (2-byte) d’une valeur allant de 0 à 65 535.</span><span class="sxs-lookup"><span data-stu-id="b4889-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4889-104">Notes </span><span class="sxs-lookup"><span data-stu-id="b4889-104">Remarks</span></span>

 <span data-ttu-id="b4889-105">Utilisez `UShort` le type de données pour `Byte`contenir des données binaires trop grandes pour .</span><span class="sxs-lookup"><span data-stu-id="b4889-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="b4889-106">La valeur par défaut de `UShort` est 0.</span><span class="sxs-lookup"><span data-stu-id="b4889-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="b4889-107">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="b4889-107">Literal assignments</span></span>

<span data-ttu-id="b4889-108">Vous pouvez déclarer et `UShort` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="b4889-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="b4889-109">Si le littéral entier est en dehors de la plage de `UShort` (autrement dit, s’il est inférieur à <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="b4889-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="b4889-110">Dans l’exemple suivant, les intégristes sont égaux à 65 034 qui sont représentés comme décimales, hexadecimal, et les littérals binaires sont attribués aux `UShort` valeurs.</span><span class="sxs-lookup"><span data-stu-id="b4889-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="b4889-111">Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="b4889-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="b4889-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="b4889-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="b4889-113">En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b4889-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="b4889-114">En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal.</span><span class="sxs-lookup"><span data-stu-id="b4889-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="b4889-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4889-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="b4889-116">Les littérals numériques `us` peuvent également inclure `UShort` le caractère ou le `US` [type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b4889-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="b4889-117">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="b4889-117">Programming tips</span></span>
  
- <span data-ttu-id="b4889-118">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="b4889-118">**Negative Numbers.**</span></span> <span data-ttu-id="b4889-119">Parce `UShort` qu’il s’agit d’un type non signé, il ne peut pas représenter un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="b4889-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="b4889-120">Si vous utilisez l’opérateur unary moins (`-`) `UShort`sur une expression qui `Integer` évalue au type, Visual Basic convertit l’expression en premier.</span><span class="sxs-lookup"><span data-stu-id="b4889-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="b4889-121">**Conformité CLS.**</span><span class="sxs-lookup"><span data-stu-id="b4889-121">**CLS Compliance.**</span></span> <span data-ttu-id="b4889-122">Le `UShort` type de données ne fait pas partie de la [spécification de langue commune](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), de sorte que le code conforme à CLS ne peut pas consommer un composant qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="b4889-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="b4889-123">**Élargissement.**</span><span class="sxs-lookup"><span data-stu-id="b4889-123">**Widening.**</span></span> <span data-ttu-id="b4889-124">Le `UShort` type de `Integer`données `UInteger` `Long`s’élargit à , , `ULong`, , `Decimal`, `Single`et `Double`.</span><span class="sxs-lookup"><span data-stu-id="b4889-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="b4889-125">Cela signifie que `UShort` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.</span><span class="sxs-lookup"><span data-stu-id="b4889-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="b4889-126">**Personnages de type.**</span><span class="sxs-lookup"><span data-stu-id="b4889-126">**Type Characters.**</span></span> <span data-ttu-id="b4889-127">Appending les caractères `US` de type littéral `UShort` à un littéral le force au type de données.</span><span class="sxs-lookup"><span data-stu-id="b4889-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="b4889-128">`UShort`n’a pas de caractère de type identificateur.</span><span class="sxs-lookup"><span data-stu-id="b4889-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="b4889-129">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="b4889-129">**Framework Type.**</span></span> <span data-ttu-id="b4889-130">Le type correspondant dans le .NET Framework est la structure <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4889-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4889-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4889-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="b4889-132">Types de données</span><span class="sxs-lookup"><span data-stu-id="b4889-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b4889-133">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="b4889-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b4889-134">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="b4889-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="b4889-135">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="b4889-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="b4889-136">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="b4889-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
