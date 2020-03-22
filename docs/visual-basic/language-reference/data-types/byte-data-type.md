---
title: Octet (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400742"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="8152e-102">Type de données byte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8152e-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="8152e-103">Détient des intégrés 8 bits non signés (1-byte) dont la valeur varie de 0 à 255.</span><span class="sxs-lookup"><span data-stu-id="8152e-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="8152e-104">Notes </span><span class="sxs-lookup"><span data-stu-id="8152e-104">Remarks</span></span>

<span data-ttu-id="8152e-105">Utilisez `Byte` le type de données pour contenir des données binaires.</span><span class="sxs-lookup"><span data-stu-id="8152e-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="8152e-106">La valeur par défaut de `Byte` est 0.</span><span class="sxs-lookup"><span data-stu-id="8152e-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="8152e-107">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="8152e-107">Literal assignments</span></span>

<span data-ttu-id="8152e-108">Vous pouvez déclarer et `Byte` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="8152e-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="8152e-109">Si le littéral intégral est `Byte` en dehors de la portée <xref:System.Byte.MinValue?displayProperty=nameWithType> d’un (c’est-à-dire, si elle est inférieure ou supérieure <xref:System.Byte.MaxValue?displayProperty=nameWithType>à), une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="8152e-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="8152e-110">Dans l’exemple suivant, les intégristes égaux à 201 qui sont représentés comme décimales, hexadecimal, `byte` et les littérals binaires sont implicitement convertis d’Integer à des valeurs. [Integer](integer-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="8152e-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="8152e-111">Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="8152e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="8152e-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="8152e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="8152e-113">En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8152e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="8152e-114">En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal.</span><span class="sxs-lookup"><span data-stu-id="8152e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="8152e-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8152e-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="8152e-116">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="8152e-116">Programming tips</span></span>

- <span data-ttu-id="8152e-117">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="8152e-117">**Negative Numbers.**</span></span> <span data-ttu-id="8152e-118">Parce `Byte` qu’il s’agit d’un type non signé, il ne peut pas représenter un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="8152e-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="8152e-119">Si vous utilisez l’opérateur unary moins (`-`) `Byte`sur une expression qui `Short` évalue au type, Visual Basic convertit l’expression en premier.</span><span class="sxs-lookup"><span data-stu-id="8152e-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="8152e-120">**Conversions de format.**</span><span class="sxs-lookup"><span data-stu-id="8152e-120">**Format Conversions.**</span></span> <span data-ttu-id="8152e-121">Lorsque Visual Basic lit ou écrit des fichiers, ou lorsqu’il appelle les DLL, les méthodes et les propriétés, il peut automatiquement convertir entre les formats de données.</span><span class="sxs-lookup"><span data-stu-id="8152e-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="8152e-122">Les données `Byte` binaires stockées dans les variables et les tableaux sont conservées lors de ces conversions de format.</span><span class="sxs-lookup"><span data-stu-id="8152e-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="8152e-123">Vous ne devez `String` pas utiliser une variable pour les données binaires, car son contenu peut être corrompu lors de la conversion entre les formats ANSI et Unicode.</span><span class="sxs-lookup"><span data-stu-id="8152e-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="8152e-124">**Élargissement.**</span><span class="sxs-lookup"><span data-stu-id="8152e-124">**Widening.**</span></span> <span data-ttu-id="8152e-125">Le `Byte` type de `Short`données `UShort` `Integer`s’élargit `ULong` `Decimal`à `Single`, `Double`, , `UInteger` `Long`, , , , , ou .</span><span class="sxs-lookup"><span data-stu-id="8152e-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="8152e-126">Cela signifie que `Byte` vous pouvez convertir à <xref:System.OverflowException?displayProperty=nameWithType> l’un de ces types sans rencontrer une erreur.</span><span class="sxs-lookup"><span data-stu-id="8152e-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="8152e-127">**Personnages de type.**</span><span class="sxs-lookup"><span data-stu-id="8152e-127">**Type Characters.**</span></span> <span data-ttu-id="8152e-128">`Byte`n’a pas de caractère de type littéral ou de caractère de type identifiant.</span><span class="sxs-lookup"><span data-stu-id="8152e-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="8152e-129">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="8152e-129">**Framework Type.**</span></span> <span data-ttu-id="8152e-130">Le type correspondant dans le .NET Framework est la structure <xref:System.Byte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8152e-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="8152e-131"> Exemple</span><span class="sxs-lookup"><span data-stu-id="8152e-131">Example</span></span>

 <span data-ttu-id="8152e-132">Dans l’exemple `b` suivant, est une `Byte` variable.</span><span class="sxs-lookup"><span data-stu-id="8152e-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="8152e-133">Les énoncés démontrent la portée de la variable et l’application des opérateurs de décalage.</span><span class="sxs-lookup"><span data-stu-id="8152e-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="8152e-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8152e-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="8152e-135">Types de données</span><span class="sxs-lookup"><span data-stu-id="8152e-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="8152e-136">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="8152e-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="8152e-137">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="8152e-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="8152e-138">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="8152e-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
