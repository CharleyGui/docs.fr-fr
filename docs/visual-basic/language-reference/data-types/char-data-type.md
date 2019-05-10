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
ms.openlocfilehash: 6600b3b2945120f2f24e14d4cc898cd814366045
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647063"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="b688d-102">Char, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b688d-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="b688d-103">Contient les points de code de (2 octets) de 16 bits non signé compris entre 0 et 65 535.</span><span class="sxs-lookup"><span data-stu-id="b688d-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="b688d-104">Chaque *point de code*, ou code de caractère, représente un caractère Unicode.</span><span class="sxs-lookup"><span data-stu-id="b688d-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b688d-105">Notes</span><span class="sxs-lookup"><span data-stu-id="b688d-105">Remarks</span></span>  
 <span data-ttu-id="b688d-106">Utilisez le `Char` lorsque vous avez besoin contenir un seul type de données de caractères et n’avez pas besoin de la surcharge de `String`.</span><span class="sxs-lookup"><span data-stu-id="b688d-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="b688d-107">Dans certains cas, vous pouvez utiliser `Char()`, un tableau de `Char` éléments, pour contenir plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="b688d-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="b688d-108">La valeur par défaut de `Char` est le caractère avec un point de code de 0.</span><span class="sxs-lookup"><span data-stu-id="b688d-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="b688d-109">Caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="b688d-109">Unicode Characters</span></span>  
 <span data-ttu-id="b688d-110">Les premiers points de 128 code (0 à 127) Unicode correspondent aux lettres et des symboles sur un clavier américain standard.</span><span class="sxs-lookup"><span data-stu-id="b688d-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="b688d-111">Ces premiers points de 128 code sont les mêmes que celles définit le jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="b688d-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="b688d-112">Les deuxième 128 points de code (128 à 255) représentent des caractères spéciaux, tels que des lettres de l’alphabet Latin en fonction du, les accents, les symboles monétaires et les fractions.</span><span class="sxs-lookup"><span data-stu-id="b688d-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="b688d-113">Unicode utilise les points de code restants (256-65 535) pour une grande variété de symboles, y compris les caractères textuels mondiaux, les signes diacritiques et les symboles mathématiques et techniques.</span><span class="sxs-lookup"><span data-stu-id="b688d-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="b688d-114">Vous pouvez utiliser des méthodes telles que <xref:System.Char.IsDigit%2A> et <xref:System.Char.IsPunctuation%2A> sur une `Char` variable pour déterminer sa classification Unicode.</span><span class="sxs-lookup"><span data-stu-id="b688d-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="b688d-115">Conversions de type</span><span class="sxs-lookup"><span data-stu-id="b688d-115">Type Conversions</span></span>  
 <span data-ttu-id="b688d-116">Visual Basic ne convertit pas directement entre `Char` et les types numériques.</span><span class="sxs-lookup"><span data-stu-id="b688d-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="b688d-117">Vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> fonction pour convertir un `Char` valeur un `Integer` qui représente son point de code.</span><span class="sxs-lookup"><span data-stu-id="b688d-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="b688d-118">Vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> fonction pour convertir un `Integer` valeur un `Char` qui a ce point de code.</span><span class="sxs-lookup"><span data-stu-id="b688d-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="b688d-119">Si le commutateur de vérification de type ([Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md)) est activé, vous devez ajouter le caractère de type littéral à un seul caractère littéral de chaîne à l’identifier en tant que le `Char` type de données.</span><span class="sxs-lookup"><span data-stu-id="b688d-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="b688d-120">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="b688d-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="b688d-121">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="b688d-121">Programming Tips</span></span>  
  
- <span data-ttu-id="b688d-122">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="b688d-122">**Negative Numbers.**</span></span> <span data-ttu-id="b688d-123">`Char` est un type non signé et ne peut pas représenter une valeur négative.</span><span class="sxs-lookup"><span data-stu-id="b688d-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="b688d-124">Dans tous les cas, vous ne devez pas utiliser `Char` pour contenir des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="b688d-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
- <span data-ttu-id="b688d-125">**Considérations sur l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="b688d-125">**Interop Considerations.**</span></span> <span data-ttu-id="b688d-126">Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types de caractère ont une largeur de données différente (8 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="b688d-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="b688d-127">Si vous passez un argument de 8 bits à un tel composant, déclarez-le en tant que `Byte` au lieu de `Char` dans votre nouveau code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b688d-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="b688d-128">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="b688d-128">**Widening.**</span></span> <span data-ttu-id="b688d-129">Le `Char` type de données s’étend à `String`.</span><span class="sxs-lookup"><span data-stu-id="b688d-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="b688d-130">Cela signifie que vous pouvez convertir `Char` à `String` et vous ne rencontrerez pas un <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="b688d-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="b688d-131">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="b688d-131">**Type Characters.**</span></span> <span data-ttu-id="b688d-132">L’ajout du caractère de type de littéral `C` à une chaîne à un caractère littéral force ce dernier à la `Char` type de données.</span><span class="sxs-lookup"><span data-stu-id="b688d-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="b688d-133">`Char` n’a aucun caractère de type d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="b688d-133">`Char` has no identifier type character.</span></span>  
  
- <span data-ttu-id="b688d-134">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="b688d-134">**Framework Type.**</span></span> <span data-ttu-id="b688d-135">Le type correspondant dans le .NET Framework est la structure <xref:System.Char?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b688d-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b688d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b688d-136">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="b688d-137">Types de données</span><span class="sxs-lookup"><span data-stu-id="b688d-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b688d-138">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="b688d-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="b688d-139">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="b688d-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b688d-140">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="b688d-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="b688d-141">Guide pratique pour appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="b688d-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="b688d-142">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="b688d-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
