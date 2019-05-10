---
title: UShort, type de données (Visual Basic)
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
ms.openlocfilehash: d85219fad631b09c19eac054b87d4843b0c73a45
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646937"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="5b3d0-102">UShort, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b3d0-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="5b3d0-103">Contient des entiers 16 bits (2 octets) non signés compris entre 0 et 65 535.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b3d0-104">Notes</span><span class="sxs-lookup"><span data-stu-id="5b3d0-104">Remarks</span></span>

 <span data-ttu-id="5b3d0-105">Utilisez le `UShort` type de données pour contenir les données binaires trop grandes pour `Byte`.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="5b3d0-106">La valeur par défaut de `UShort` est 0.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="5b3d0-107">Affectations de littéraux</span><span class="sxs-lookup"><span data-stu-id="5b3d0-107">Literal assignments</span></span>

<span data-ttu-id="5b3d0-108">Vous pouvez déclarer et initialiser une `UShort` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="5b3d0-109">Si le littéral entier est en dehors de la plage de `UShort` (autrement dit, s’il est inférieur à <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="5b3d0-110">Dans l’exemple suivant, les entiers égaux à 65 034 représentés comme séparateur décimal, hexadécimal, et les littéraux binaires sont affectés à `UShort` valeurs.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="5b3d0-111">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="5b3d0-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="5b3d0-113">À partir de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant montre.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="5b3d0-114">À partir de Visual Basic 15.5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="5b3d0-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5b3d0-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="5b3d0-116">Littéraux numériques peuvent également inclure le `US` ou `us` [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le `UShort` type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="5b3d0-117">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="5b3d0-117">Programming tips</span></span>
  
- <span data-ttu-id="5b3d0-118">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="5b3d0-118">**Negative Numbers.**</span></span> <span data-ttu-id="5b3d0-119">Étant donné que `UShort` est un type non signé, il ne peut pas représenter un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="5b3d0-120">Si vous utilisez le moins unaire (`-`) opérateur sur une expression qui correspond au type `UShort`, Visual Basic convertit l’expression à `Integer` première.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="5b3d0-121">**Conformité CLS.**</span><span class="sxs-lookup"><span data-stu-id="5b3d0-121">**CLS Compliance.**</span></span> <span data-ttu-id="5b3d0-122">Le `UShort` type de données n’est pas dans le cadre de la [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="5b3d0-123">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="5b3d0-123">**Widening.**</span></span> <span data-ttu-id="5b3d0-124">Le `UShort` type de données s’étend à `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, et `Double`.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="5b3d0-125">Cela signifie que vous pouvez convertir `UShort` à un de ces types sans rencontrer un <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="5b3d0-126">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="5b3d0-126">**Type Characters.**</span></span> <span data-ttu-id="5b3d0-127">Ajout des caractères de type littéral `US` à un littéral force ce dernier à la `UShort` type de données.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="5b3d0-128">`UShort` n’a aucun caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="5b3d0-129">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="5b3d0-129">**Framework Type.**</span></span> <span data-ttu-id="5b3d0-130">Le type correspondant dans le .NET Framework est la structure <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b3d0-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3d0-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b3d0-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="5b3d0-132">Types de données</span><span class="sxs-lookup"><span data-stu-id="5b3d0-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="5b3d0-133">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="5b3d0-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5b3d0-134">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="5b3d0-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="5b3d0-135">Guide pratique pour appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="5b3d0-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="5b3d0-136">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="5b3d0-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
