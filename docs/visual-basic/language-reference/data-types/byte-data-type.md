---
title: Octet (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374315"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="9e0ce-102">Byte, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e0ce-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="9e0ce-103">Contient des entiers 8 bits (1 octet) non signés dont la valeur est comprise entre 0 et 255.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e0ce-104">Notes</span><span class="sxs-lookup"><span data-stu-id="9e0ce-104">Remarks</span></span>

<span data-ttu-id="9e0ce-105">Utilisez le `Byte` type de données pour contenir des données binaires.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="9e0ce-106">La valeur par défaut de `Byte` est 0.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="9e0ce-107">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="9e0ce-107">Literal assignments</span></span>

<span data-ttu-id="9e0ce-108">Vous pouvez déclarer et initialiser une `Byte` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="9e0ce-109">Si le littéral intégral se trouve en dehors de la plage d’un `Byte` (autrement dit, s’il est inférieur à <xref:System.Byte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Byte.MaxValue?displayProperty=nameWithType> ), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="9e0ce-110">Dans l’exemple suivant, les entiers égaux à 201 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis d’un [entier](integer-data-type.md) en `byte` valeurs.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="9e0ce-111">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="9e0ce-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="9e0ce-113">À compter de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_` , comme séparateur de chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="9e0ce-114">À compter de Visual Basic 15,5, vous pouvez également utiliser le trait de soulignement ( `_` ) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="9e0ce-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9e0ce-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="9e0ce-116">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="9e0ce-116">Programming tips</span></span>

- <span data-ttu-id="9e0ce-117">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="9e0ce-117">**Negative Numbers.**</span></span> <span data-ttu-id="9e0ce-118">Étant donné que `Byte` est un type non signé, il ne peut pas représenter un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="9e0ce-119">Si vous utilisez l’opérateur moins unaire ( `-` ) sur une expression qui prend la valeur type `Byte` , Visual Basic convertit d’abord l’expression en `Short` premier.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="9e0ce-120">**Conversions de format.**</span><span class="sxs-lookup"><span data-stu-id="9e0ce-120">**Format Conversions.**</span></span> <span data-ttu-id="9e0ce-121">Lorsque Visual Basic lit ou écrit des fichiers, ou lorsqu’il appelle des dll, des méthodes et des propriétés, il peut effectuer automatiquement une conversion entre des formats de données.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="9e0ce-122">Les données binaires stockées dans des `Byte` variables et des tableaux sont conservées au cours de ces conversions de format.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="9e0ce-123">Vous ne devez pas utiliser une `String` variable pour les données binaires, car son contenu peut être endommagé lors de la conversion entre des formats ANSI et Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="9e0ce-124">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="9e0ce-124">**Widening.**</span></span> <span data-ttu-id="9e0ce-125">Le `Byte` type de données s’étend à `Short` , `UShort` , `Integer` , `UInteger` , `Long` , `ULong` , `Decimal` , `Single` ou `Double` .</span><span class="sxs-lookup"><span data-stu-id="9e0ce-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="9e0ce-126">Cela signifie que vous pouvez `Byte` effectuer une conversion vers l’un de ces types sans rencontrer d' <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="9e0ce-127">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="9e0ce-127">**Type Characters.**</span></span> <span data-ttu-id="9e0ce-128">`Byte`n’a aucun caractère de type de littéral ou caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="9e0ce-129">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="9e0ce-129">**Framework Type.**</span></span> <span data-ttu-id="9e0ce-130">Le type correspondant dans le .NET Framework est la structure <xref:System.Byte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="9e0ce-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e0ce-131">Example</span></span>

 <span data-ttu-id="9e0ce-132">Dans l’exemple suivant, `b` est une `Byte` variable.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="9e0ce-133">Les instructions démontrent la plage de la variable et l’application des opérateurs de décalage de bits.</span><span class="sxs-lookup"><span data-stu-id="9e0ce-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="9e0ce-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e0ce-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="9e0ce-135">Types de données</span><span class="sxs-lookup"><span data-stu-id="9e0ce-135">Data Types</span></span>](index.md)
- [<span data-ttu-id="9e0ce-136">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="9e0ce-136">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="9e0ce-137">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="9e0ce-137">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="9e0ce-138">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="9e0ce-138">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
