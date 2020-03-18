---
title: Constructions d’alternative dans les expressions régulières .NET
description: Découvrez comment utiliser des constructions d’alternative pour la correspondance conditionnelle dans les expressions régulières.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159687"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="218a1-103">Constructions d'alternative dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="218a1-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="218a1-104">Les constructions d'alternative modifient une expression régulière pour permettre la correspondance de type inclusif/exclusif ou conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="218a1-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="218a1-105">.NET prend en charge trois constructions d’alternative :</span><span class="sxs-lookup"><span data-stu-id="218a1-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="218a1-106">Utilisation des critères spéciaux avec &#124;</span><span class="sxs-lookup"><span data-stu-id="218a1-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="218a1-107">Correspondance conditionnelle avec (?(expression)oui&#124;non)</span><span class="sxs-lookup"><span data-stu-id="218a1-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="218a1-108">Correspondance conditionnelle selon un groupe capturé valide</span><span class="sxs-lookup"><span data-stu-id="218a1-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="218a1-109">Utilisation des critères spéciaux avec &#124;</span><span class="sxs-lookup"><span data-stu-id="218a1-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="218a1-110">Vous pouvez utiliser la barre verticale (`|`) pour mettre en correspondance un modèle d’une série, dans laquelle le caractère `|` sépare chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="218a1-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="218a1-111">Tout comme la classe de caractères positive, le caractère `|` peut être utilisé pour mettre en correspondance n’importe quel nombre de caractères uniques.</span><span class="sxs-lookup"><span data-stu-id="218a1-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="218a1-112">L’exemple suivant utilise une classe de caractères positive et des critères spéciaux de type inclusif/exclusif avec le caractère `|` pour trouver des occurrences des mots « gray » ou « grey » dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="218a1-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="218a1-113">Dans ce cas, le caractère `|` produit une expression régulière qui est plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="218a1-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="218a1-114">L’expression régulière `|` qui `\bgr(a|e)y\b`utilise le personnage, , est interprétée comme indiqué dans le tableau suivant:</span><span class="sxs-lookup"><span data-stu-id="218a1-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="218a1-115">Modèle</span><span class="sxs-lookup"><span data-stu-id="218a1-115">Pattern</span></span>|<span data-ttu-id="218a1-116">Description</span><span class="sxs-lookup"><span data-stu-id="218a1-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="218a1-117">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="218a1-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="218a1-118">Mettre en correspondance les caractères « gr ».</span><span class="sxs-lookup"><span data-stu-id="218a1-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="218a1-119">Mettre en correspondance un « a » ou un « e ».</span><span class="sxs-lookup"><span data-stu-id="218a1-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="218a1-120">Mettre en correspondance un « y » à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="218a1-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="218a1-121">Le caractère `|` peut également être utilisé pour effectuer une correspondance de type inclusif/exclusif avec plusieurs caractères ou sous-expressions, qui peuvent inclure toute combinaison de caractère littéraux et éléments de langage d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="218a1-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="218a1-122">(La classe de caractère ne fournit pas cette fonctionnalité.) L’exemple suivant `|` utilise le personnage pour extraire soit un numéro de sécurité sociale des États-Unis (SSN), qui est un numéro à 9 chiffres avec le format *ddd*-*ddddd\*\*dd*-, ou un numéro d’identification des employeurs des États-Unis (EIN), qui est un numéro à 9 chiffres avec le format-*ddddddd*. *dd*</span><span class="sxs-lookup"><span data-stu-id="218a1-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="218a1-123">L’expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` régulière est interprétée comme indiquée dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="218a1-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="218a1-124">Modèle</span><span class="sxs-lookup"><span data-stu-id="218a1-124">Pattern</span></span>|<span data-ttu-id="218a1-125">Description</span><span class="sxs-lookup"><span data-stu-id="218a1-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="218a1-126">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="218a1-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="218a1-127">Mettre en correspondance l'un ou l'autre des éléments suivants : deux chiffres décimaux suivis d'un trait d'union suivi de sept chiffres décimaux, ou alors trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="218a1-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="218a1-128">Terminer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="218a1-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="218a1-129">Correspondance conditionnelle avec une expression</span><span class="sxs-lookup"><span data-stu-id="218a1-129">Conditional matching with an expression</span></span>

<span data-ttu-id="218a1-130">Cet élément de langage tente de mettre en correspondance un modèle parmi deux fournis selon qu'il parvient ou non à mettre en correspondance un modèle initial.</span><span class="sxs-lookup"><span data-stu-id="218a1-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="218a1-131">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="218a1-131">Its syntax is:</span></span>  

<span data-ttu-id="218a1-132">`(?(`*expression* `)` *oui* `|` *non*`)`</span><span class="sxs-lookup"><span data-stu-id="218a1-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="218a1-133">lorsque *l’expression* est le modèle initial pour correspondre, *oui* est le modèle à assortir si *l’expression* est assortie, et *non* est le modèle facultatif pour correspondre si *l’expression* n’est pas assortie.</span><span class="sxs-lookup"><span data-stu-id="218a1-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="218a1-134">Le moteur d’expression régulière traite l’*expression* comme une assertion de largeur nulle ; c’est-à-dire que le moteur d’expression régulière n’avance pas dans le flux d’entrée après avoir évalué l’*expression*.</span><span class="sxs-lookup"><span data-stu-id="218a1-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="218a1-135">Par conséquent, cette construction est équivalente à la suivante :</span><span class="sxs-lookup"><span data-stu-id="218a1-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="218a1-136">`(?(?=`*expression* `)` *oui* `|` *non*`)`</span><span class="sxs-lookup"><span data-stu-id="218a1-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="218a1-137">où `(?=` *l’expression* `)` est une construction d’affirmation à largeur zéro.</span><span class="sxs-lookup"><span data-stu-id="218a1-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="218a1-138">(Pour plus d’informations, voir [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Parce que le moteur d’expression régulière interprète *l’expression* comme une ancre (une affirmation de largeur zéro), *l’expression* doit soit être une affirmation de largeur zéro (pour plus d’informations, voir [Anchors](anchors-in-regular-expressions.md)) ou une sous-expression qui est également contenue dans *oui*.</span><span class="sxs-lookup"><span data-stu-id="218a1-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="218a1-139">Sinon, aucune correspondance ne peut être établie avec le modèle *oui* .</span><span class="sxs-lookup"><span data-stu-id="218a1-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="218a1-140">Si *l’expression* est un groupe de capture nommé ou numéroté, la construction d’alternance est interprétée comme un test de capture; pour plus d’informations, voir la section suivante, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="218a1-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="218a1-141">En d'autres termes, le moteur des expressions régulières ne tente pas de mettre en correspondance la sous-chaîne capturée, mais à la place teste la présence ou l'absence du groupe.</span><span class="sxs-lookup"><span data-stu-id="218a1-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="218a1-142">L’exemple suivant est une variante de celui donné dans la section [Critères spéciaux de type inclusif/exclusif avec &#124;](#Either_Or).</span><span class="sxs-lookup"><span data-stu-id="218a1-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="218a1-143">Il utilise la mise en correspondance conditionnelle pour déterminer si les trois premiers caractères après une limite de mot se composent de deux chiffres suivis d'un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="218a1-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="218a1-144">Si c'est le cas, il tente de mettre en correspondance un numéro d'identification de l'employeur (EIN) américain.</span><span class="sxs-lookup"><span data-stu-id="218a1-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="218a1-145">Si ce n'est pas le cas, il tente de mettre en correspondance un numéro de sécurité sociale (SSN) américain.</span><span class="sxs-lookup"><span data-stu-id="218a1-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="218a1-146">Le modèle `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` d’expression ordinaire est interprété comme indiqué dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="218a1-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="218a1-147">Modèle</span><span class="sxs-lookup"><span data-stu-id="218a1-147">Pattern</span></span>|<span data-ttu-id="218a1-148">Description</span><span class="sxs-lookup"><span data-stu-id="218a1-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="218a1-149">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="218a1-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="218a1-150">Déterminer si les trois caractères suivants se composent de deux chiffres suivis d'un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="218a1-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="218a1-151">Si le modèle précédent correspond, mettre en correspondance deux chiffres suivis d'un trait d'union suivi de sept chiffres.</span><span class="sxs-lookup"><span data-stu-id="218a1-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="218a1-152">Si le modèle ne correspond pas, faire correspondre trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="218a1-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="218a1-153">Mettre en correspondance la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="218a1-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="218a1-154">Correspondance conditionnelle selon un groupe capturé valide</span><span class="sxs-lookup"><span data-stu-id="218a1-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="218a1-155">Cet élément de langage essaie de faire correspondre l'un de deux modèles selon qu'il peut correspondre à un groupe capturé spécifié.</span><span class="sxs-lookup"><span data-stu-id="218a1-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="218a1-156">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="218a1-156">Its syntax is:</span></span>

<span data-ttu-id="218a1-157">`(?(` *name* `)` *oui* `|` *non* `)`</span><span class="sxs-lookup"><span data-stu-id="218a1-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="218a1-158">or</span><span class="sxs-lookup"><span data-stu-id="218a1-158">or</span></span>

<span data-ttu-id="218a1-159">`(?(` *nombre* `)` *oui* `|` *non* `)`</span><span class="sxs-lookup"><span data-stu-id="218a1-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="218a1-160">lorsque le *nom* est le nom et le *numéro* est le nombre d’un groupe de capture, *oui* est l’expression pour correspondre si le *nom* ou le *numéro* a une correspondance, et *non* est l’expression facultative pour correspondre si elle ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="218a1-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="218a1-161">Si le *nom* ne correspond pas au nom d'un groupe de capture utilisé dans le modèle d'expression régulière, la construction alternative est interprétée comme un test d'expression, comme expliqué dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="218a1-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="218a1-162">Typiquement, cela signifie que `false` *l’expression* évalue à .</span><span class="sxs-lookup"><span data-stu-id="218a1-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="218a1-163">Si le *nombre* ne correspond pas à un groupe de capture numéroté utilisé dans le modèle d'expression régulière, le moteur des expressions régulières lève une <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="218a1-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="218a1-164">L’exemple suivant est une variante de celui donné dans la section [Critères spéciaux de type inclusif/exclusif avec &#124;](#Either_Or).</span><span class="sxs-lookup"><span data-stu-id="218a1-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="218a1-165">Il utilise un groupe de capture nommé `n2` qui se compose de deux chiffres suivis d'un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="218a1-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="218a1-166">La construction d'alternative tests si ce groupe de capture a été mis en correspondance dans la chaîne d'entrée.</span><span class="sxs-lookup"><span data-stu-id="218a1-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="218a1-167">Si c'est le cas, la construction alternative essaie de mettre en correspondance les sept derniers chiffres d'un numéro d'identification de l'employeur (EIN) américain.</span><span class="sxs-lookup"><span data-stu-id="218a1-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="218a1-168">Si ce n'est le cas, il essaie de faire correspondre un numéro de sécurité sociale (SSN) américain.</span><span class="sxs-lookup"><span data-stu-id="218a1-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="218a1-169">Le modèle `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` d’expression ordinaire est interprété comme indiqué dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="218a1-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="218a1-170">Modèle</span><span class="sxs-lookup"><span data-stu-id="218a1-170">Pattern</span></span>|<span data-ttu-id="218a1-171">Description</span><span class="sxs-lookup"><span data-stu-id="218a1-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="218a1-172">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="218a1-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="218a1-173">Mettre en correspondance zéro ou une occurrence de deux chiffres suivis d'un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="218a1-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="218a1-174">Nommer ce groupe de capture `n2`.</span><span class="sxs-lookup"><span data-stu-id="218a1-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="218a1-175">Testez si `n2` a été mis en correspondance dans la chaîne d'entrée.</span><span class="sxs-lookup"><span data-stu-id="218a1-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="218a1-176">Si `n2` a été mis en correspondance, faites correspondre sept chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="218a1-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="218a1-177">Si `n2` ne correspondait pas, faites correspondre trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="218a1-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="218a1-178">Mettre en correspondance la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="218a1-178">Match a word boundary.</span></span>|  

<span data-ttu-id="218a1-179">Une variation de cet exemple qui utilise un groupe numéroté au lieu d'un groupe nommé est illustrée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="218a1-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="218a1-180">Son modèle d'expression régulière est `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="218a1-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="218a1-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="218a1-181">See also</span></span>

- [<span data-ttu-id="218a1-182">Langage d’expression régulière - Référence rapide</span><span class="sxs-lookup"><span data-stu-id="218a1-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
