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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 560597770d667cf8c7668bf2338ac4bac3eb192f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968574"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="b2804-103">Constructions d'alternative dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="b2804-103">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a> <span data-ttu-id="b2804-104">Les constructions d'alternative modifient une expression régulière pour permettre la correspondance de type inclusif/exclusif ou conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="b2804-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="b2804-105">.NET prend en charge trois constructions d’alternative :</span><span class="sxs-lookup"><span data-stu-id="b2804-105">.NET supports three alternation constructs:</span></span>  
  
- [<span data-ttu-id="b2804-106">Utilisation des critères spéciaux avec &#124;</span><span class="sxs-lookup"><span data-stu-id="b2804-106">Pattern matching with &#124;</span></span>](#Either_Or)  
  
- [<span data-ttu-id="b2804-107">Correspondance conditionnelle avec (?(expression)oui&#124;non)</span><span class="sxs-lookup"><span data-stu-id="b2804-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
- [<span data-ttu-id="b2804-108">Correspondance conditionnelle selon un groupe capturé valide</span><span class="sxs-lookup"><span data-stu-id="b2804-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="b2804-109">Utilisation des critères spéciaux avec &#124;</span><span class="sxs-lookup"><span data-stu-id="b2804-109">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="b2804-110">Vous pouvez utiliser la barre verticale (`|`) pour mettre en correspondance un modèle d’une série, dans laquelle le caractère `|` sépare chaque modèle.</span><span class="sxs-lookup"><span data-stu-id="b2804-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="b2804-111">Tout comme la classe de caractères positive, le caractère `|` peut être utilisé pour mettre en correspondance n’importe quel nombre de caractères uniques.</span><span class="sxs-lookup"><span data-stu-id="b2804-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="b2804-112">L’exemple suivant utilise une classe de caractères positive et des critères spéciaux de type inclusif/exclusif avec le caractère `|` pour trouver des occurrences des mots « gray » ou « grey » dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b2804-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="b2804-113">Dans ce cas, le caractère `|` produit une expression régulière qui est plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="b2804-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="b2804-114">L’expression régulière qui utilise le caractère `|` , `\bgr(a|e)y\b`, est interprétée comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b2804-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b2804-115">Motif</span><span class="sxs-lookup"><span data-stu-id="b2804-115">Pattern</span></span>|<span data-ttu-id="b2804-116">Description</span><span class="sxs-lookup"><span data-stu-id="b2804-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b2804-117">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="b2804-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="b2804-118">Mettre en correspondance les caractères « gr ».</span><span class="sxs-lookup"><span data-stu-id="b2804-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="b2804-119">Mettre en correspondance un « a » ou un « e ».</span><span class="sxs-lookup"><span data-stu-id="b2804-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="b2804-120">Mettre en correspondance un « y » à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="b2804-120">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="b2804-121">Le caractère `|` peut également être utilisé pour effectuer une correspondance de type inclusif/exclusif avec plusieurs caractères ou sous-expressions, qui peuvent inclure toute combinaison de caractère littéraux et éléments de langage d’expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="b2804-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="b2804-122">(La classe de caractères ne fournit pas cette fonctionnalité.) L’exemple suivant utilise le caractère `|` pour extraire un numéro de sécurité sociale (SSN) américain, qui est un nombre de 9 chiffres au format *ddd*-*dd*-*dddd*, ou un numéro d’identification de l’employeur (EIN) américain, qui est un nombre de 9 chiffres au format *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="b2804-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="b2804-123">L'expression régulière `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` est interprétée comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b2804-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b2804-124">Motif</span><span class="sxs-lookup"><span data-stu-id="b2804-124">Pattern</span></span>|<span data-ttu-id="b2804-125">Description</span><span class="sxs-lookup"><span data-stu-id="b2804-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b2804-126">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="b2804-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="b2804-127">Mettre en correspondance l'un ou l'autre des éléments suivants : deux chiffres décimaux suivis d'un trait d'union suivi de sept chiffres décimaux, ou alors trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="b2804-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="b2804-128">Terminer la correspondance à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="b2804-128">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="b2804-129">Retour au début</span><span class="sxs-lookup"><span data-stu-id="b2804-129">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="b2804-130">Correspondance conditionnelle avec une expression</span><span class="sxs-lookup"><span data-stu-id="b2804-130">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="b2804-131">Cet élément de langage tente de mettre en correspondance un modèle parmi deux fournis selon qu'il parvient ou non à mettre en correspondance un modèle initial.</span><span class="sxs-lookup"><span data-stu-id="b2804-131">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="b2804-132">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b2804-132">Its syntax is:</span></span>  
  
 <span data-ttu-id="b2804-133">`(?(` *expression* `)` *oui* `|` *non* `)`</span><span class="sxs-lookup"><span data-stu-id="b2804-133">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b2804-134">où *expression* est le modèle initial à faire correspondre, *oui* est le modèle à faire correspondre si l' *expression* est mise en correspondance, et *no* est le modèle facultatif à faire correspondre si l' *expression* n'est pas mise en correspondance.</span><span class="sxs-lookup"><span data-stu-id="b2804-134">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="b2804-135">Le moteur d'expressions régulières traite *expression* comme une assertion de largeur nulle ; c'est-à-dire que le moteur d'expressions régulières n'avance pas dans le flux d'entrée après avoir évalué l' *expression*.</span><span class="sxs-lookup"><span data-stu-id="b2804-135">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="b2804-136">Par conséquent, cette construction est équivalente à la suivante :</span><span class="sxs-lookup"><span data-stu-id="b2804-136">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="b2804-137">`(?(?=` *expression* `)` *oui* `|` *non* `)`</span><span class="sxs-lookup"><span data-stu-id="b2804-137">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b2804-138">où `(?=`*expression*`)` est une construction d'assertion de largeur nulle.</span><span class="sxs-lookup"><span data-stu-id="b2804-138">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="b2804-139">(Pour plus d'informations, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Étant donné que le moteur des expressions régulières interprète *l’expression* comme une ancre (assertion de largeur nulle), *l’expression* doit être soit une assertion de largeur nulle (pour plus d’informations, consultez [Ancres](../../../docs/standard/base-types/anchors-in-regular-expressions.md)), soit une sous-expression qui est également contenue dans *oui*.</span><span class="sxs-lookup"><span data-stu-id="b2804-139">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="b2804-140">Sinon, aucune correspondance ne peut être établie avec le modèle *oui*.</span><span class="sxs-lookup"><span data-stu-id="b2804-140">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2804-141">Si l’ *expression*est un groupe de capture nommé ou numéroté, la construction alternative est interprétée comme un test de capture. Pour plus d’informations, consultez la section suivante, [Correspondance conditionnelle selon un groupe capturé valide](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="b2804-141">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="b2804-142">En d'autres termes, le moteur des expressions régulières ne tente pas de mettre en correspondance la sous-chaîne capturée, mais à la place teste la présence ou l'absence du groupe.</span><span class="sxs-lookup"><span data-stu-id="b2804-142">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="b2804-143">L’exemple suivant est une variante de celui donné dans la section [Critères spéciaux de type inclusif/exclusif avec &#124;](#Either_Or).</span><span class="sxs-lookup"><span data-stu-id="b2804-143">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="b2804-144">Il utilise la mise en correspondance conditionnelle pour déterminer si les trois premiers caractères après une limite de mot se composent de deux chiffres suivis d'un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="b2804-144">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="b2804-145">Si c'est le cas, il tente de mettre en correspondance un numéro d'identification de l'employeur (EIN) américain.</span><span class="sxs-lookup"><span data-stu-id="b2804-145">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="b2804-146">Si ce n'est pas le cas, il tente de mettre en correspondance un numéro de sécurité sociale (SSN) américain.</span><span class="sxs-lookup"><span data-stu-id="b2804-146">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="b2804-147">Le modèle d'expression régulière `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` est interprété comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b2804-147">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b2804-148">Motif</span><span class="sxs-lookup"><span data-stu-id="b2804-148">Pattern</span></span>|<span data-ttu-id="b2804-149">Description</span><span class="sxs-lookup"><span data-stu-id="b2804-149">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b2804-150">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="b2804-150">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="b2804-151">Déterminer si les trois caractères suivants se composent de deux chiffres suivis d'un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="b2804-151">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="b2804-152">Si le modèle précédent correspond, mettre en correspondance deux chiffres suivis d'un trait d'union suivi de sept chiffres.</span><span class="sxs-lookup"><span data-stu-id="b2804-152">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="b2804-153">Si le modèle ne correspond pas, faire correspondre trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="b2804-153">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="b2804-154">Mettre en correspondance la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="b2804-154">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="b2804-155">Retour au début</span><span class="sxs-lookup"><span data-stu-id="b2804-155">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="b2804-156">Correspondance conditionnelle selon un groupe capturé valide</span><span class="sxs-lookup"><span data-stu-id="b2804-156">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="b2804-157">Cet élément de langage essaie de faire correspondre l'un de deux modèles selon qu'il peut correspondre à un groupe capturé spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2804-157">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="b2804-158">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b2804-158">Its syntax is:</span></span>  
  
 <span data-ttu-id="b2804-159">`(?(` *name* `)` *oui* `|` *non* `)`</span><span class="sxs-lookup"><span data-stu-id="b2804-159">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b2804-160">ou</span><span class="sxs-lookup"><span data-stu-id="b2804-160">or</span></span>  
  
 <span data-ttu-id="b2804-161">`(?(` *nombre* `)` *oui* `|` *non* `)`</span><span class="sxs-lookup"><span data-stu-id="b2804-161">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b2804-162">où *nom* est le nom et *numéro* est le numéro d'un groupe de capture, *oui* est l'expression à faire correspondre si *nom* ou *nombre* a une correspondance et *non* est l'expression facultative à faire correspondre dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="b2804-162">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="b2804-163">Si le *nom* ne correspond pas au nom d'un groupe de capture utilisé dans le modèle d'expression régulière, la construction alternative est interprétée comme un test d'expression, comme expliqué dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="b2804-163">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="b2804-164">En général, cela signifie que l' *expression* prend la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="b2804-164">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="b2804-165">Si le *nombre* ne correspond pas à un groupe de capture numéroté utilisé dans le modèle d'expression régulière, le moteur des expressions régulières lève une <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="b2804-165">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="b2804-166">L’exemple suivant est une variante de celui donné dans la section [Critères spéciaux de type inclusif/exclusif avec &#124;](#Either_Or).</span><span class="sxs-lookup"><span data-stu-id="b2804-166">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="b2804-167">Il utilise un groupe de capture nommé `n2` qui se compose de deux chiffres suivis d'un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="b2804-167">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="b2804-168">La construction d'alternative tests si ce groupe de capture a été mis en correspondance dans la chaîne d'entrée.</span><span class="sxs-lookup"><span data-stu-id="b2804-168">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="b2804-169">Si c'est le cas, la construction alternative essaie de mettre en correspondance les sept derniers chiffres d'un numéro d'identification de l'employeur (EIN) américain.</span><span class="sxs-lookup"><span data-stu-id="b2804-169">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="b2804-170">Si ce n'est le cas, il essaie de faire correspondre un numéro de sécurité sociale (SSN) américain.</span><span class="sxs-lookup"><span data-stu-id="b2804-170">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="b2804-171">Le modèle d'expression régulière `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` est interprété comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b2804-171">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b2804-172">Motif</span><span class="sxs-lookup"><span data-stu-id="b2804-172">Pattern</span></span>|<span data-ttu-id="b2804-173">Description</span><span class="sxs-lookup"><span data-stu-id="b2804-173">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b2804-174">Commencer à la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="b2804-174">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="b2804-175">Mettre en correspondance zéro ou une occurrence de deux chiffres suivis d'un trait d'union.</span><span class="sxs-lookup"><span data-stu-id="b2804-175">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="b2804-176">Nommer ce groupe de capture `n2`.</span><span class="sxs-lookup"><span data-stu-id="b2804-176">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="b2804-177">Testez si `n2` a été mis en correspondance dans la chaîne d'entrée.</span><span class="sxs-lookup"><span data-stu-id="b2804-177">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="b2804-178">Si `n2` a été mis en correspondance, faites correspondre sept chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="b2804-178">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="b2804-179">Si `n2` ne correspondait pas, faites correspondre trois chiffres décimaux, un trait d'union, deux chiffres décimaux, un autre trait d'union et quatre chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="b2804-179">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="b2804-180">Mettre en correspondance la limite d'un mot.</span><span class="sxs-lookup"><span data-stu-id="b2804-180">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="b2804-181">Une variation de cet exemple qui utilise un groupe numéroté au lieu d'un groupe nommé est illustrée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b2804-181">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="b2804-182">Son modèle d'expression régulière est `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="b2804-182">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b2804-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2804-183">See also</span></span>

- [<span data-ttu-id="b2804-184">Langage des expressions régulières - Aide-mémoire</span><span class="sxs-lookup"><span data-stu-id="b2804-184">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
