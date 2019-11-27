---
title: Char, type de données
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 1ed5b19a307d094fc1d5a6bb0251c57052dc9bc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344046"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="5726a-102">Char, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5726a-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="5726a-103">Contient des points de code non signés de 16 bits (2 octets) dont la valeur est comprise entre 0 et 65535.</span><span class="sxs-lookup"><span data-stu-id="5726a-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="5726a-104">Chaque *point de code*, ou code de caractère, représente un caractère Unicode unique.</span><span class="sxs-lookup"><span data-stu-id="5726a-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="5726a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="5726a-105">Remarks</span></span>

<span data-ttu-id="5726a-106">Utilisez le type de données `Char` lorsque vous ne devez contenir qu’un seul caractère et que vous n’avez pas besoin de la surcharge de `String`.</span><span class="sxs-lookup"><span data-stu-id="5726a-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="5726a-107">Dans certains cas, vous pouvez utiliser `Char()`, un tableau d’éléments `Char`, pour contenir plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="5726a-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="5726a-108">La valeur par défaut de `Char` est le caractère avec un point de code de 0.</span><span class="sxs-lookup"><span data-stu-id="5726a-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="5726a-109">Caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="5726a-109">Unicode Characters</span></span>

<span data-ttu-id="5726a-110">Les premiers points de code 128 (0 à 127) d’Unicode correspondent aux lettres et aux symboles sur un clavier américain standard.</span><span class="sxs-lookup"><span data-stu-id="5726a-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="5726a-111">Ces premiers points de code 128 sont les mêmes que ceux définis par le jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="5726a-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="5726a-112">Le deuxième point de code 128 (128 à 255) représente des caractères spéciaux, tels que des lettres alphabetées latines, des accents, des symboles monétaires et des fractions.</span><span class="sxs-lookup"><span data-stu-id="5726a-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="5726a-113">Unicode utilise les points de code restants (256-65535) pour un large éventail de symboles, y compris les caractères textuels mondiaux, les signes diacritiques et les symboles mathématiques et techniques.</span><span class="sxs-lookup"><span data-stu-id="5726a-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="5726a-114">Vous pouvez utiliser des méthodes comme <xref:System.Char.IsDigit%2A> et <xref:System.Char.IsPunctuation%2A> sur une variable `Char` pour déterminer sa classification Unicode.</span><span class="sxs-lookup"><span data-stu-id="5726a-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="5726a-115">Conversions de type</span><span class="sxs-lookup"><span data-stu-id="5726a-115">Type Conversions</span></span>

<span data-ttu-id="5726a-116">Visual Basic ne se convertit pas directement entre `Char` et les types numériques.</span><span class="sxs-lookup"><span data-stu-id="5726a-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="5726a-117">Vous pouvez utiliser la fonction <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> pour convertir une valeur `Char` en une `Integer` qui représente son point de code.</span><span class="sxs-lookup"><span data-stu-id="5726a-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="5726a-118">Vous pouvez utiliser la fonction <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> pour convertir une valeur `Integer` en `Char` qui a ce point de code.</span><span class="sxs-lookup"><span data-stu-id="5726a-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="5726a-119">Si le commutateur de vérification de type ( [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) est activé, vous devez ajouter le caractère de type littéral à un littéral de chaîne à un seul caractère pour l’identifier en tant que type de données `Char`.</span><span class="sxs-lookup"><span data-stu-id="5726a-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="5726a-120">L’exemple suivant illustre ces actions.</span><span class="sxs-lookup"><span data-stu-id="5726a-120">The following example illustrates this.</span></span> <span data-ttu-id="5726a-121">La première assignation à la variable `charVar` génère une erreur du compilateur [BC30512](../../misc/bc30512.md) , car `Option Strict` est activé.</span><span class="sxs-lookup"><span data-stu-id="5726a-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="5726a-122">La deuxième compilation réussit, car le `c` caractère de type de littéral identifie le littéral comme une valeur de `Char`.</span><span class="sxs-lookup"><span data-stu-id="5726a-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="5726a-123">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="5726a-123">Programming Tips</span></span>

- <span data-ttu-id="5726a-124">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="5726a-124">**Negative Numbers.**</span></span> <span data-ttu-id="5726a-125">`Char` est un type non signé et ne peut pas représenter une valeur négative.</span><span class="sxs-lookup"><span data-stu-id="5726a-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="5726a-126">Dans tous les cas, vous ne devez pas utiliser `Char` pour contenir des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="5726a-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="5726a-127">**Considérations relatives à l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="5726a-127">**Interop Considerations.**</span></span> <span data-ttu-id="5726a-128">Si vous interface avec des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types de caractères ont une largeur de données différente (8 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="5726a-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="5726a-129">Si vous transmettez un argument de 8 bits à un tel composant, déclarez-le comme `Byte` au lieu de `Char` dans votre nouveau code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5726a-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="5726a-130">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="5726a-130">**Widening.**</span></span> <span data-ttu-id="5726a-131">Le type de données `Char` s’étend à `String`.</span><span class="sxs-lookup"><span data-stu-id="5726a-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="5726a-132">Cela signifie que vous pouvez convertir `Char` en `String` et que vous ne rencontrerez pas de <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5726a-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="5726a-133">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="5726a-133">**Type Characters.**</span></span> <span data-ttu-id="5726a-134">L’ajout du caractère de type de littéral `C` à un littéral de chaîne à un seul caractère force ce dernier en type de données `Char`.</span><span class="sxs-lookup"><span data-stu-id="5726a-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="5726a-135">`Char` n’a pas de caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="5726a-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="5726a-136">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="5726a-136">**Framework Type.**</span></span> <span data-ttu-id="5726a-137">Le type correspondant dans le .NET Framework est la structure <xref:System.Char?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5726a-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="5726a-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5726a-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="5726a-139">Types de données</span><span class="sxs-lookup"><span data-stu-id="5726a-139">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="5726a-140">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="5726a-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="5726a-141">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="5726a-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5726a-142">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="5726a-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="5726a-143">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="5726a-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="5726a-144">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="5726a-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
