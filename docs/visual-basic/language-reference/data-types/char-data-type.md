---
title: Char, type de données (Visual Basic)
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
ms.openlocfilehash: 8313c2282a3b4b7b035f9f3b685a786c4471f53a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630141"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="dd067-102">Char, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd067-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="dd067-103">Contient des points de code non signés de 16 bits (2 octets) dont la valeur est comprise entre 0 et 65535.</span><span class="sxs-lookup"><span data-stu-id="dd067-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="dd067-104">Chaque *point de code*, ou code de caractère, représente un caractère Unicode unique.</span><span class="sxs-lookup"><span data-stu-id="dd067-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd067-105">Notes</span><span class="sxs-lookup"><span data-stu-id="dd067-105">Remarks</span></span>

<span data-ttu-id="dd067-106">Utilisez le `Char` type de données lorsque vous ne devez contenir qu’un seul caractère et que vous n’avez pas `String`besoin de la surcharge de.</span><span class="sxs-lookup"><span data-stu-id="dd067-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="dd067-107">Dans certains cas, vous pouvez `Char()`utiliser, un tableau `Char` d’éléments, pour contenir plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="dd067-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="dd067-108">La valeur par défaut `Char` de est le caractère avec un point de code de 0.</span><span class="sxs-lookup"><span data-stu-id="dd067-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="dd067-109">Caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="dd067-109">Unicode Characters</span></span>

<span data-ttu-id="dd067-110">Les premiers points de code 128 (0 à 127) d’Unicode correspondent aux lettres et aux symboles sur un clavier américain standard.</span><span class="sxs-lookup"><span data-stu-id="dd067-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="dd067-111">Ces premiers points de code 128 sont les mêmes que ceux définis par le jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="dd067-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="dd067-112">Le deuxième point de code 128 (128 à 255) représente des caractères spéciaux, tels que des lettres alphabetées latines, des accents, des symboles monétaires et des fractions.</span><span class="sxs-lookup"><span data-stu-id="dd067-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="dd067-113">Unicode utilise les points de code restants (256-65535) pour un large éventail de symboles, y compris les caractères textuels mondiaux, les signes diacritiques et les symboles mathématiques et techniques.</span><span class="sxs-lookup"><span data-stu-id="dd067-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="dd067-114">Vous pouvez utiliser des méthodes <xref:System.Char.IsDigit%2A> telles <xref:System.Char.IsPunctuation%2A> que et `Char` sur une variable pour déterminer sa classification Unicode.</span><span class="sxs-lookup"><span data-stu-id="dd067-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="dd067-115">Conversions de type</span><span class="sxs-lookup"><span data-stu-id="dd067-115">Type Conversions</span></span>

<span data-ttu-id="dd067-116">Visual Basic n’effectue pas de conversion `Char` directe entre et les types numériques.</span><span class="sxs-lookup"><span data-stu-id="dd067-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="dd067-117">Vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Asc%2A> fonction <xref:Microsoft.VisualBasic.Strings.AscW%2A> ou pour `Integer` convertir une `Char` valeur en qui représente son point de code.</span><span class="sxs-lookup"><span data-stu-id="dd067-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="dd067-118">Vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Chr%2A> fonction <xref:Microsoft.VisualBasic.Strings.ChrW%2A> ou pour `Char` convertir une `Integer` valeur en qui a ce point de code.</span><span class="sxs-lookup"><span data-stu-id="dd067-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="dd067-119">Si le commutateur de vérification de type ( [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) est activé, vous devez ajouter le caractère de type littéral à un littéral de chaîne à un seul caractère pour `Char` l’identifier comme type de données.</span><span class="sxs-lookup"><span data-stu-id="dd067-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="dd067-120">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="dd067-120">The following example illustrates this.</span></span> <span data-ttu-id="dd067-121">La première assignation à la `charVar` variable génère une erreur du compilateur `Option Strict` [BC30512](../../misc/bc30512.md) , car est activé.</span><span class="sxs-lookup"><span data-stu-id="dd067-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="dd067-122">La deuxième compilation réussit, car le `c` caractère de type littéral identifie le littéral comme `Char` une valeur.</span><span class="sxs-lookup"><span data-stu-id="dd067-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

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

## <a name="programming-tips"></a><span data-ttu-id="dd067-123">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="dd067-123">Programming Tips</span></span>

- <span data-ttu-id="dd067-124">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="dd067-124">**Negative Numbers.**</span></span> <span data-ttu-id="dd067-125">`Char`est un type non signé et ne peut pas représenter une valeur négative.</span><span class="sxs-lookup"><span data-stu-id="dd067-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="dd067-126">Dans tous les cas, vous ne devez `Char` pas utiliser pour contenir des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="dd067-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="dd067-127">**Considérations relatives à l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="dd067-127">**Interop Considerations.**</span></span> <span data-ttu-id="dd067-128">Si vous interface avec des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types de caractères ont une largeur de données différente (8 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="dd067-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="dd067-129">Si vous transmettez un argument de 8 bits à un tel composant, déclarez `Byte` -le `Char` comme au lieu de dans votre nouveau Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="dd067-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="dd067-130">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="dd067-130">**Widening.**</span></span> <span data-ttu-id="dd067-131">Le `Char` type de données s’étend `String`à.</span><span class="sxs-lookup"><span data-stu-id="dd067-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="dd067-132">Cela signifie que vous pouvez `Char` convertir `String` en et ne rencontrera <xref:System.OverflowException?displayProperty=nameWithType>pas de.</span><span class="sxs-lookup"><span data-stu-id="dd067-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="dd067-133">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="dd067-133">**Type Characters.**</span></span> <span data-ttu-id="dd067-134">L’ajout du caractère `C` de type littéral à un littéral de chaîne à un seul caractère force ce dernier `Char` en type de données.</span><span class="sxs-lookup"><span data-stu-id="dd067-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="dd067-135">`Char`n’a pas de caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="dd067-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="dd067-136">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="dd067-136">**Framework Type.**</span></span> <span data-ttu-id="dd067-137">Le type correspondant dans le .NET Framework est la structure <xref:System.Char?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd067-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd067-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd067-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="dd067-139">Types de données</span><span class="sxs-lookup"><span data-stu-id="dd067-139">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="dd067-140">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="dd067-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="dd067-141">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="dd067-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="dd067-142">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="dd067-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="dd067-143">Guide pratique pour appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="dd067-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="dd067-144">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="dd067-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
