---
title: Type de données UInteger (Visual Basic)
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
ms.openlocfilehash: 12447e56f89914121dcc9eda2bee0700343baf12
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646976"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="7d5f3-102">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="7d5f3-102">UInteger data type</span></span>

<span data-ttu-id="7d5f3-103">Contient des entiers 32 bits (4 octets) non signés dont la valeur comprise entre 0 et 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d5f3-104">Notes</span><span class="sxs-lookup"><span data-stu-id="7d5f3-104">Remarks</span></span>

 <span data-ttu-id="7d5f3-105">Le `UInteger` type de données fournit la plus grande valeur non signée dans la largeur de données plus efficace.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="7d5f3-106">La valeur par défaut de `UInteger` est 0.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="7d5f3-107">Affectations de littéraux</span><span class="sxs-lookup"><span data-stu-id="7d5f3-107">Literal assignments</span></span>

<span data-ttu-id="7d5f3-108">Vous pouvez déclarer et initialiser une `UInteger` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="7d5f3-109">Si le littéral entier est en dehors de la plage de `UInteger` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="7d5f3-110">Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="7d5f3-111">Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire et le préfixe `&o` ou `&O` pour désigner un littéral octal.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="7d5f3-112">Les littéraux décimaux n’ont pas de préfixe.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7d5f3-113">À partir de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant montre.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="7d5f3-114">À partir de Visual Basic 15.5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="7d5f3-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7d5f3-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="7d5f3-116">Littéraux numériques peuvent également inclure le `UI` ou `ui` [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le `UInteger` type de données, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="7d5f3-117">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="7d5f3-117">Programming tips</span></span>

 <span data-ttu-id="7d5f3-118">Le `UInteger` et `Integer` types de données offrent des performances optimales sur un processeur 32 bits, car les types d’entier plus petits (`UShort`, `Short`, `Byte`, et `SByte`), même si elles utilisent moins de bits, davantage de temps charger, stocker et à extraire.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
- <span data-ttu-id="7d5f3-119">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="7d5f3-119">**Negative Numbers.**</span></span> <span data-ttu-id="7d5f3-120">Étant donné que `UInteger` est un type non signé, il ne peut pas représenter un nombre négatif.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="7d5f3-121">Si vous utilisez le moins unaire (`-`) opérateur sur une expression qui correspond au type `UInteger`, Visual Basic convertit l’expression à `Long` première.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
- <span data-ttu-id="7d5f3-122">**Conformité CLS.**</span><span class="sxs-lookup"><span data-stu-id="7d5f3-122">**CLS Compliance.**</span></span> <span data-ttu-id="7d5f3-123">Le `UInteger` type de données n’est pas dans le cadre de la [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="7d5f3-124">**Considérations sur l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="7d5f3-124">**Interop Considerations.**</span></span> <span data-ttu-id="7d5f3-125">Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types tels que `uint` peut avoir une largeur de données différente (16 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="7d5f3-126">Si vous passez un argument de 16 bits à un tel composant, déclarez-le en tant que `UShort` au lieu de `UInteger` dans votre code managé de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
- <span data-ttu-id="7d5f3-127">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="7d5f3-127">**Widening.**</span></span> <span data-ttu-id="7d5f3-128">Le `UInteger` type de données s’étend à `Long`, `ULong`, `Decimal`, `Single`, et `Double`.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="7d5f3-129">Cela signifie que vous pouvez convertir `UInteger` à un de ces types sans rencontrer un <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="7d5f3-130">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="7d5f3-130">**Type Characters.**</span></span> <span data-ttu-id="7d5f3-131">Ajout des caractères de type littéral `UI` à un littéral force ce dernier à la `UInteger` type de données.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="7d5f3-132">`UInteger` n’a aucun caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-132">`UInteger` has no identifier type character.</span></span>  
  
- <span data-ttu-id="7d5f3-133">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="7d5f3-133">**Framework Type.**</span></span> <span data-ttu-id="7d5f3-134">Le type correspondant dans le .NET Framework est la structure <xref:System.UInt32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d5f3-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5f3-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d5f3-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="7d5f3-136">Types de données</span><span class="sxs-lookup"><span data-stu-id="7d5f3-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="7d5f3-137">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="7d5f3-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="7d5f3-138">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="7d5f3-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="7d5f3-139">Guide pratique pour appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="7d5f3-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="7d5f3-140">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="7d5f3-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
