---
title: Like, opérateur
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 4279d90c74c80403146448a8ba5a6051ec9d12f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401552"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="4b798-102">Like (opérateur Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b798-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="4b798-103">Compare une chaîne à un modèle.</span><span class="sxs-lookup"><span data-stu-id="4b798-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="4b798-104">L' `Like` opérateur n’est actuellement pas pris en charge dans les projets .net Core et .NET standard.</span><span class="sxs-lookup"><span data-stu-id="4b798-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b798-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b798-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="4b798-106">Éléments</span><span class="sxs-lookup"><span data-stu-id="4b798-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="4b798-107">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4b798-107">Required.</span></span> <span data-ttu-id="4b798-108">Toute `Boolean` variable.</span><span class="sxs-lookup"><span data-stu-id="4b798-108">Any `Boolean` variable.</span></span> <span data-ttu-id="4b798-109">Le résultat est une `Boolean` valeur indiquant si le répond à `string` `pattern` .</span><span class="sxs-lookup"><span data-stu-id="4b798-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="4b798-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4b798-110">Required.</span></span> <span data-ttu-id="4b798-111">Toute expression `String` .</span><span class="sxs-lookup"><span data-stu-id="4b798-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="4b798-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4b798-112">Required.</span></span> <span data-ttu-id="4b798-113">Toute `String` expression conforme aux conventions de critères spéciaux décrites dans « remarques ».</span><span class="sxs-lookup"><span data-stu-id="4b798-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b798-114">Notes</span><span class="sxs-lookup"><span data-stu-id="4b798-114">Remarks</span></span>  
 <span data-ttu-id="4b798-115">Si la valeur de `string` est conforme au modèle contenu dans `pattern` , `result` est `True` .</span><span class="sxs-lookup"><span data-stu-id="4b798-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="4b798-116">Si la chaîne n’est pas conforme au modèle, a la valeur `result` `False` .</span><span class="sxs-lookup"><span data-stu-id="4b798-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="4b798-117">Si `string` et `pattern` sont des chaînes vides, le résultat est `True` .</span><span class="sxs-lookup"><span data-stu-id="4b798-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="4b798-118">Méthode de comparaison</span><span class="sxs-lookup"><span data-stu-id="4b798-118">Comparison Method</span></span>  
 <span data-ttu-id="4b798-119">Le comportement de l' `Like` opérateur dépend de l' [instruction Option Compare](../statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4b798-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../statements/option-compare-statement.md).</span></span> <span data-ttu-id="4b798-120">La méthode de comparaison de chaînes par défaut pour chaque fichier source est `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="4b798-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="4b798-121">Options de modèle</span><span class="sxs-lookup"><span data-stu-id="4b798-121">Pattern Options</span></span>  
 <span data-ttu-id="4b798-122">Les critères spéciaux intégrés fournissent un outil polyvalent pour les comparaisons de chaînes.</span><span class="sxs-lookup"><span data-stu-id="4b798-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="4b798-123">Les fonctionnalités de critères spéciaux vous permettent de faire correspondre chaque caractère d' `string` un caractère spécifique, d’un caractère générique, d’une liste de caractères ou d’une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="4b798-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="4b798-124">Le tableau suivant indique les caractères autorisés dans `pattern` et ce qu’ils correspondent.</span><span class="sxs-lookup"><span data-stu-id="4b798-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="4b798-125">Caractères dans`pattern`</span><span class="sxs-lookup"><span data-stu-id="4b798-125">Characters in `pattern`</span></span>|<span data-ttu-id="4b798-126">Correspond à`string`</span><span class="sxs-lookup"><span data-stu-id="4b798-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="4b798-127">Tout caractère unique</span><span class="sxs-lookup"><span data-stu-id="4b798-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="4b798-128">Zéro, un ou plusieurs caractères</span><span class="sxs-lookup"><span data-stu-id="4b798-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="4b798-129">Tout chiffre (0 à 9)</span><span class="sxs-lookup"><span data-stu-id="4b798-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="4b798-130">N’importe quel caractère unique dans`charlist`</span><span class="sxs-lookup"><span data-stu-id="4b798-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="4b798-131">N’importe quel caractère ne figurant pas dans`charlist`</span><span class="sxs-lookup"><span data-stu-id="4b798-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="4b798-132">Listes de caractères</span><span class="sxs-lookup"><span data-stu-id="4b798-132">Character Lists</span></span>  
 <span data-ttu-id="4b798-133">Un groupe d’un ou plusieurs caractères ( `charlist` ) entre crochets ( `[ ]` ) peut être utilisé pour mettre en correspondance n’importe quel caractère unique dans `string` et peut inclure presque n’importe quel code de caractère, y compris des chiffres.</span><span class="sxs-lookup"><span data-stu-id="4b798-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="4b798-134">Un point d’exclamation ( `!` ) au début de `charlist` signifie qu’une correspondance est établie si un caractère quelconque à l’exception des caractères de `charlist` est trouvé dans `string` .</span><span class="sxs-lookup"><span data-stu-id="4b798-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="4b798-135">Lorsqu’il est utilisé en dehors des crochets, le point d’exclamation correspond à lui-même.</span><span class="sxs-lookup"><span data-stu-id="4b798-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="4b798-136">Caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="4b798-136">Special Characters</span></span>  
 <span data-ttu-id="4b798-137">Pour mettre en correspondance les caractères spéciaux ( `[` ), le point d’interrogation ( `?` ), le signe dièse ( `#` ) et l’astérisque ( `*` ), placez-les entre crochets.</span><span class="sxs-lookup"><span data-stu-id="4b798-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="4b798-138">`]`Vous ne pouvez pas utiliser le crochet droit () dans un groupe pour qu’il corresponde à lui-même, mais il peut être utilisé en dehors d’un groupe comme un caractère individuel.</span><span class="sxs-lookup"><span data-stu-id="4b798-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="4b798-139">La séquence de caractères `[]` est considérée comme une chaîne de longueur nulle ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="4b798-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="4b798-140">Toutefois, il ne peut pas faire partie d’une liste de caractères placée entre crochets.</span><span class="sxs-lookup"><span data-stu-id="4b798-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="4b798-141">Si vous souhaitez vérifier si une position dans `string` contient un groupe de caractères ou aucun caractère, vous pouvez utiliser `Like` deux fois.</span><span class="sxs-lookup"><span data-stu-id="4b798-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="4b798-142">Pour obtenir un exemple, consultez [Comment : faire correspondre une chaîne à un modèle](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4b798-142">For an example, see [How to: Match a String against a Pattern](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="4b798-143">Plages de caractères</span><span class="sxs-lookup"><span data-stu-id="4b798-143">Character Ranges</span></span>  
 <span data-ttu-id="4b798-144">En utilisant un trait d’Union ( `–` ) pour séparer les limites inférieure et supérieure de la plage, `charlist` peut spécifier une plage de caractères.</span><span class="sxs-lookup"><span data-stu-id="4b798-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="4b798-145">Par exemple, `[A–Z]` aboutit à une correspondance si la position de caractère correspondante dans `string` contient un caractère quelconque dans la plage `A` `Z` , et `[!H–L]` aboutit à une correspondance si la position de caractère correspondante contient un caractère en dehors de la plage `H` () `L` .</span><span class="sxs-lookup"><span data-stu-id="4b798-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="4b798-146">Lorsque vous spécifiez une plage de caractères, ceux-ci doivent apparaître dans l’ordre de tri croissant, c’est-à-dire de la plus petite à la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="4b798-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="4b798-147">Par conséquent, `[A–Z]` est un modèle valide, mais `[Z–A]` ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="4b798-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="4b798-148">Plusieurs plages de caractères</span><span class="sxs-lookup"><span data-stu-id="4b798-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="4b798-149">Pour spécifier plusieurs plages pour la même position de caractère, placez-les entre les crochets sans délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="4b798-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="4b798-150">Par exemple, `[A–CX–Z]` aboutit à une correspondance si la position de caractère correspondante dans `string` contient un caractère quelconque dans la plage `A` ( `C` ou la plage `X` ) `Z` .</span><span class="sxs-lookup"><span data-stu-id="4b798-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="4b798-151">Utilisation du trait d’Union</span><span class="sxs-lookup"><span data-stu-id="4b798-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="4b798-152">Un trait d’Union ( `–` ) peut apparaître au début (après un point d’exclamation, le cas échéant) ou à la fin de `charlist` pour se mettre en correspondance.</span><span class="sxs-lookup"><span data-stu-id="4b798-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="4b798-153">Dans tout autre emplacement, le trait d’Union identifie une plage de caractères délimitée par les caractères situés de part et d’autre du trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="4b798-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="4b798-154">Séquence de classement</span><span class="sxs-lookup"><span data-stu-id="4b798-154">Collating Sequence</span></span>  
 <span data-ttu-id="4b798-155">La signification d’une plage spécifiée dépend de l’ordre des caractères au moment de l’exécution, tel que déterminé par `Option Compare` et des paramètres régionaux du système sur lequel le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="4b798-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="4b798-156">Avec `Option Compare Binary` , la plage `[A–E]` correspond à,,, `A` `B` `C` `D` et `E` .</span><span class="sxs-lookup"><span data-stu-id="4b798-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="4b798-157">Avec, correspond à,,,,,,,,,, `Option Compare Text` `[A–E]` `A` `a` `À` `à` `B` `b` `C` `c` `D` `d` `E` et `e` .</span><span class="sxs-lookup"><span data-stu-id="4b798-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="4b798-158">La plage ne correspond pas `Ê` ou `ê` parce que les caractères accentués sont triés après les caractères non accentués dans l’ordre de tri.</span><span class="sxs-lookup"><span data-stu-id="4b798-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="4b798-159">Caractères digrammes</span><span class="sxs-lookup"><span data-stu-id="4b798-159">Digraph Characters</span></span>  
 <span data-ttu-id="4b798-160">Dans certains langages, des caractères alphabétiques représentent deux caractères distincts.</span><span class="sxs-lookup"><span data-stu-id="4b798-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="4b798-161">Par exemple, plusieurs langues utilisent le caractère `æ` pour représenter les caractères `a` et `e` lorsqu’ils apparaissent ensemble.</span><span class="sxs-lookup"><span data-stu-id="4b798-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="4b798-162">L' `Like` opérateur reconnaît que le caractère digramme unique et les deux caractères individuels sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="4b798-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="4b798-163">Quand une langue qui utilise un caractère digramme est spécifiée dans les paramètres régionaux du système, une occurrence du caractère digramme unique dans `pattern` ou `string` correspond à la séquence de deux caractères équivalente dans l’autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="4b798-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="4b798-164">De même, un caractère digramme `pattern` placé entre crochets (par lui-même, dans une liste ou dans une plage) correspond à la séquence de deux caractères équivalente dans `string` .</span><span class="sxs-lookup"><span data-stu-id="4b798-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4b798-165">Surcharge</span><span class="sxs-lookup"><span data-stu-id="4b798-165">Overloading</span></span>  
 <span data-ttu-id="4b798-166">L' `Like` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="4b798-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4b798-167">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="4b798-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4b798-168">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4b798-168">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b798-169">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b798-169">Example</span></span>  
 <span data-ttu-id="4b798-170">Cet exemple utilise l' `Like` opérateur pour comparer des chaînes à différents modèles.</span><span class="sxs-lookup"><span data-stu-id="4b798-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="4b798-171">Les résultats sont placés dans une `Boolean` variable indiquant si chaque chaîne est conforme au modèle.</span><span class="sxs-lookup"><span data-stu-id="4b798-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="4b798-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b798-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="4b798-173">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="4b798-173">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="4b798-174">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b798-174">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="4b798-175">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="4b798-175">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="4b798-176">Option Compare, instruction</span><span class="sxs-lookup"><span data-stu-id="4b798-176">Option Compare Statement</span></span>](../statements/option-compare-statement.md)
- [<span data-ttu-id="4b798-177">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="4b798-177">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="4b798-178">Comment : faire correspondre une chaîne à un modèle</span><span class="sxs-lookup"><span data-stu-id="4b798-178">How to: Match a String against a Pattern</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
