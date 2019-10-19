---
title: UInteger, type de données (Visual Basic)
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
ms.openlocfilehash: 1ae0cbd3a518bf863a3c57f50934837a486d2901
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583136"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="a1d04-102">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="a1d04-102">UInteger data type</span></span>

<span data-ttu-id="a1d04-103">Contient des entiers non signés de 32 bits (4 octets) dont la valeur est comprise entre 0 et 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="a1d04-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1d04-104">Notes</span><span class="sxs-lookup"><span data-stu-id="a1d04-104">Remarks</span></span>

<span data-ttu-id="a1d04-105">Le type de données `UInteger` fournit la plus grande valeur non signée dans la largeur de données la plus efficace.</span><span class="sxs-lookup"><span data-stu-id="a1d04-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="a1d04-106">La valeur par défaut de `UInteger` est 0.</span><span class="sxs-lookup"><span data-stu-id="a1d04-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="a1d04-107">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="a1d04-107">Literal assignments</span></span>

<span data-ttu-id="a1d04-108">Vous pouvez déclarer et initialiser une variable `UInteger` en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="a1d04-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="a1d04-109">Si le littéral entier est en dehors de la plage de `UInteger` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="a1d04-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="a1d04-110">Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="a1d04-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="a1d04-111">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="a1d04-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="a1d04-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="a1d04-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a1d04-113">À compter de Visual Basic 2017, vous pouvez également utiliser le trait de soulignement, `_`, comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a1d04-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="a1d04-114">À compter de Visual Basic 15,5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux.</span><span class="sxs-lookup"><span data-stu-id="a1d04-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="a1d04-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="a1d04-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="a1d04-116">Les littéraux numériques peuvent également inclure le caractère de [type](../../programming-guide/language-features/data-types/type-characters.md) `UI` ou `ui` pour désigner le type de données `UInteger`, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a1d04-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="a1d04-117">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="a1d04-117">Programming tips</span></span>

<span data-ttu-id="a1d04-118">Les types de données `UInteger` et `Integer` offrent des performances optimales sur un processeur 32 bits, étant donné que les types d’entiers plus petits (`UShort`, `Short`, `Byte` et `SByte`), même s’ils utilisent moins de bits, prennent plus de temps pour le chargement , Store et FETCH.</span><span class="sxs-lookup"><span data-stu-id="a1d04-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="a1d04-119">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="a1d04-119">**Negative Numbers.**</span></span> <span data-ttu-id="a1d04-120">Étant donné que `UInteger` est un type non signé, il ne peut pas représenter un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="a1d04-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="a1d04-121">Si vous utilisez l’opérateur moins unaire (`-`) sur une expression qui prend la valeur du type `UInteger`, Visual Basic convertit d’abord l’expression en `Long`.</span><span class="sxs-lookup"><span data-stu-id="a1d04-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="a1d04-122">**Conformité CLS.**</span><span class="sxs-lookup"><span data-stu-id="a1d04-122">**CLS Compliance.**</span></span> <span data-ttu-id="a1d04-123">Le type de données `UInteger` ne faisant pas partie du [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="a1d04-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="a1d04-124">**Considérations relatives à l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="a1d04-124">**Interop Considerations.**</span></span> <span data-ttu-id="a1d04-125">Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types tels que `uint` peuvent avoir une largeur de données différente (16 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="a1d04-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="a1d04-126">Si vous passez un argument de 16 bits à un tel composant, déclarez-le comme `UShort` au lieu de `UInteger` dans le code de votre Visual Basic managé.</span><span class="sxs-lookup"><span data-stu-id="a1d04-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="a1d04-127">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="a1d04-127">**Widening.**</span></span> <span data-ttu-id="a1d04-128">Le type de données `UInteger` s’étend à `Long`, `ULong`, `Decimal`, `Single` et `Double`.</span><span class="sxs-lookup"><span data-stu-id="a1d04-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="a1d04-129">Cela signifie que vous pouvez convertir `UInteger` en l’un de ces types sans rencontrer d’erreur de <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a1d04-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="a1d04-130">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="a1d04-130">**Type Characters.**</span></span> <span data-ttu-id="a1d04-131">L’ajout des caractères de type littéral `UI` à un littéral force ce dernier en type de données `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="a1d04-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="a1d04-132">`UInteger` n’a pas de caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="a1d04-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="a1d04-133">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="a1d04-133">**Framework Type.**</span></span> <span data-ttu-id="a1d04-134">Le type correspondant dans le .NET Framework est la structure <xref:System.UInt32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a1d04-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1d04-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1d04-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="a1d04-136">Types de données</span><span class="sxs-lookup"><span data-stu-id="a1d04-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a1d04-137">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="a1d04-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a1d04-138">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="a1d04-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="a1d04-139">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="a1d04-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="a1d04-140">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="a1d04-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
