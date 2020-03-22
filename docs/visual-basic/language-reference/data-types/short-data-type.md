---
title: Court (type de données)
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400728"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="8794c-102">Type de données courts (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8794c-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="8794c-103">Détient signé 16 bits (2-byte) integers qui varient en valeur de -32 768 à 32 767.</span><span class="sxs-lookup"><span data-stu-id="8794c-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8794c-104">Notes </span><span class="sxs-lookup"><span data-stu-id="8794c-104">Remarks</span></span>  

 <span data-ttu-id="8794c-105">Utilisez `Short` le type de données pour contenir des valeurs integer qui ne nécessitent pas toute la largeur des données de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8794c-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="8794c-106">Dans certains cas, le temps d’exécution de langage commun peut emballer vos `Short` variables étroitement ensemble et enregistrer la consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="8794c-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="8794c-107">La valeur par défaut de `Short` est 0.</span><span class="sxs-lookup"><span data-stu-id="8794c-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="8794c-108">Affectations littérales</span><span class="sxs-lookup"><span data-stu-id="8794c-108">Literal assignments</span></span>

<span data-ttu-id="8794c-109">Vous pouvez déclarer et `Short` initialiser une variable en lui assignant un littéal décimal, un littéal hexadecimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="8794c-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="8794c-110">Si le littéral entier est en dehors de la plage de `Short` (autrement dit, s’il est inférieur à <xref:System.Int16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="8794c-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="8794c-111">Dans l’exemple suivant, les intégristes sont égaux à 1 034 qui sont représentés comme décimales, hexadecimal, et les littérals binaires sont implicitement convertis d’Integer à des [Integer](integer-data-type.md) `Short` valeurs.</span><span class="sxs-lookup"><span data-stu-id="8794c-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="8794c-112">Vous utilisez le `&h` `&H` préfixe ou pour désigner un littératal hexadecimal, le `&b` préfixe ou `&B` pour désigner un littératique binaire, et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="8794c-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="8794c-113">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="8794c-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="8794c-114">En commençant par Visual Basic 2017, vous `_`pouvez également utiliser le personnage de soulignement, , comme séparateur à chiffres pour améliorer la lisibilité, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8794c-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="8794c-115">En commençant par Visual Basic 15.5, vous`_`pouvez également utiliser le caractère de soulignement ( ) comme séparateur de premier plan entre le préfixe et les chiffres hexadecimal, binaire ou octal.</span><span class="sxs-lookup"><span data-stu-id="8794c-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="8794c-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8794c-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="8794c-117">Les littérals numériques peuvent également inclure le `S` [caractère type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le `Short` type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8794c-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="8794c-118">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="8794c-118">Programming tips</span></span>

- <span data-ttu-id="8794c-119">**Élargissement.**</span><span class="sxs-lookup"><span data-stu-id="8794c-119">**Widening.**</span></span> <span data-ttu-id="8794c-120">Le `Short` type de `Integer`données `Long` `Decimal`s’élargit à , , , `Single`ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="8794c-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="8794c-121">Cela signifie que vous pouvez convertir `Short` en l'un de ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8794c-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="8794c-122">**Personnages de type.**</span><span class="sxs-lookup"><span data-stu-id="8794c-122">**Type Characters.**</span></span> <span data-ttu-id="8794c-123">L'ajout du caractère de type littéral `S` à un littéral force ce dernier en type de données `Short`.</span><span class="sxs-lookup"><span data-stu-id="8794c-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="8794c-124">`Short`n’a pas de caractère de type identificateur.</span><span class="sxs-lookup"><span data-stu-id="8794c-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="8794c-125">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="8794c-125">**Framework Type.**</span></span> <span data-ttu-id="8794c-126">Le type correspondant dans le .NET Framework est la structure <xref:System.Int16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8794c-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8794c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8794c-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="8794c-128">Types de données</span><span class="sxs-lookup"><span data-stu-id="8794c-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="8794c-129">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="8794c-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="8794c-130">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="8794c-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="8794c-131">Type de données integer</span><span class="sxs-lookup"><span data-stu-id="8794c-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="8794c-132">Long (type de données)</span><span class="sxs-lookup"><span data-stu-id="8794c-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="8794c-133">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="8794c-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
