---
title: Conventions de codage C# - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399734"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="56da3-102">Conventions de codage C# (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="56da3-102">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="56da3-103">Les conventions de codage répondent aux objectifs suivants :</span><span class="sxs-lookup"><span data-stu-id="56da3-103">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="56da3-104">Elles confèrent une apparence cohérente au code, afin que les lecteurs puissent se concentrer sur le contenu, pas sur la disposition.</span><span class="sxs-lookup"><span data-stu-id="56da3-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="56da3-105">Elles permettent aux lecteurs de comprendre le code plus rapidement en formulant des hypothèses selon leur expérience antérieure.</span><span class="sxs-lookup"><span data-stu-id="56da3-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="56da3-106">Elles facilitent la copie, la modification et la gestion du code.</span><span class="sxs-lookup"><span data-stu-id="56da3-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="56da3-107">Elles illustrent les bonnes pratiques en C#.</span><span class="sxs-lookup"><span data-stu-id="56da3-107">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="56da3-108">Les lignes directrices de cet article sont utilisées par Microsoft pour développer des échantillons et de la documentation.</span><span class="sxs-lookup"><span data-stu-id="56da3-108">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="56da3-109">Conventions de nommage</span><span class="sxs-lookup"><span data-stu-id="56da3-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="56da3-110">Dans les exemples courts qui ne comprennent pas de [directives](../../language-reference/keywords/using-directive.md), utilisez les qualifications d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="56da3-110">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="56da3-111">Si vous savez qu'un espace de noms est importé par défaut dans un projet, vous n'êtes pas obligé de qualifier entièrement les noms à partir de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="56da3-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="56da3-112">Les noms qualifiés peuvent être interrompus après un point (.) s'ils sont trop longs pour contenir sur une ligne unique, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="56da3-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="56da3-113">Vous n'avez pas à modifier les noms des objets qui ont été créés à l'aide des outils du concepteur Visual Studio pour les rendre conformes aux autres directives.</span><span class="sxs-lookup"><span data-stu-id="56da3-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="56da3-114">Conventions de disposition</span><span class="sxs-lookup"><span data-stu-id="56da3-114">Layout Conventions</span></span>  

<span data-ttu-id="56da3-115">Une bonne disposition utilise la mise en forme pour souligner la structure de votre code et en faciliter la lecture.</span><span class="sxs-lookup"><span data-stu-id="56da3-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="56da3-116">Les exemples Microsoft et autres se conforment aux conventions suivantes :</span><span class="sxs-lookup"><span data-stu-id="56da3-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="56da3-117">Utilisez les paramètres par défaut de l'éditeur de code (retrait intelligent, retrait de quatre caractères, tabulations enregistrées en tant qu'espaces).</span><span class="sxs-lookup"><span data-stu-id="56da3-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="56da3-118">Pour plus d’informations, consultez [Options, Éditeur de texte, C#, Mise en forme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="56da3-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="56da3-119">Écrivez une seule instruction par ligne.</span><span class="sxs-lookup"><span data-stu-id="56da3-119">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="56da3-120">Écrivez une seule déclaration par ligne.</span><span class="sxs-lookup"><span data-stu-id="56da3-120">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="56da3-121">Si les lignes de continuation ne sont pas mises en retrait automatiquement, indentez-les à l'aide d'un taquet de tabulation (quatre espaces).</span><span class="sxs-lookup"><span data-stu-id="56da3-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="56da3-122">Ajoutez au moins une ligne blanche entre les définitions des méthodes et les définitions des propriétés.</span><span class="sxs-lookup"><span data-stu-id="56da3-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="56da3-123">Utilisez des parenthèses pour rendre apparentes les clauses d'une expression, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="56da3-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="56da3-124">Conventions de commentaires</span><span class="sxs-lookup"><span data-stu-id="56da3-124">Commenting Conventions</span></span>  
  
- <span data-ttu-id="56da3-125">Placez le commentaire sur une ligne séparée, pas à la fin d'une ligne de code.</span><span class="sxs-lookup"><span data-stu-id="56da3-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="56da3-126">Commencez le commentaire par une lettre majuscule.</span><span class="sxs-lookup"><span data-stu-id="56da3-126">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="56da3-127">Terminez le texte de commentaire par un point.</span><span class="sxs-lookup"><span data-stu-id="56da3-127">End comment text with a period.</span></span>  
  
- <span data-ttu-id="56da3-128">Insérez un espace entre le délimiteur de commentaire (//) et le texte du commentaire, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="56da3-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="56da3-129">Ne créez pas de blocs d'astérisques mis en forme autour des commentaires.</span><span class="sxs-lookup"><span data-stu-id="56da3-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="56da3-130">Directives du langage</span><span class="sxs-lookup"><span data-stu-id="56da3-130">Language Guidelines</span></span>  

<span data-ttu-id="56da3-131">Les sections suivantes décrivent les pratiques que l'équipe C# suit pour préparer les exemples de code et autres.</span><span class="sxs-lookup"><span data-stu-id="56da3-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="56da3-132">String, type de données</span><span class="sxs-lookup"><span data-stu-id="56da3-132">String Data Type</span></span>  
  
- <span data-ttu-id="56da3-133">Utilisez une [interpolation de chaîne](../../language-reference/tokens/interpolated.md) pour concaténer les chaînes courtes, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="56da3-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="56da3-134">Pour ajouter des chaînes dans des boucles, en particulier lorsque vous travaillez avec une quantité de texte importante, utilisez un objet <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="56da3-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="56da3-135">Variables locales implicitement typées</span><span class="sxs-lookup"><span data-stu-id="56da3-135">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="56da3-136">Utilisez le [typage implicite](../classes-and-structs/implicitly-typed-local-variables.md) pour les variables locales quand le type de la variable est évident à droite de l’assignation ou quand le type précis n’importe pas.</span><span class="sxs-lookup"><span data-stu-id="56da3-136">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="56da3-137">N’utilisez pas [var](../../language-reference/keywords/var.md) quand le type n’est pas apparent à droite de l’assignation.</span><span class="sxs-lookup"><span data-stu-id="56da3-137">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="56da3-138">Ne vous basez pas sur le nom de la variable pour spécifier son type.</span><span class="sxs-lookup"><span data-stu-id="56da3-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="56da3-139">Il peut ne pas être correct.</span><span class="sxs-lookup"><span data-stu-id="56da3-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="56da3-140">Évitez d’utiliser `var` à la place de [dynamic](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="56da3-140">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="56da3-141">Utilisez la saisie implicite pour déterminer le type de variable de boucle [pour](../../language-reference/keywords/for.md) les boucles.</span><span class="sxs-lookup"><span data-stu-id="56da3-141">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
     <span data-ttu-id="56da3-142">L'exemple suivant utilise un typage implicite dans une instruction `for`.</span><span class="sxs-lookup"><span data-stu-id="56da3-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- <span data-ttu-id="56da3-143">N’utilisez pas de dactylographie implicite pour déterminer le type de variable de boucle dans les boucles [de avant-premier.](../../language-reference/keywords/foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="56da3-143">Do not use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

     <span data-ttu-id="56da3-144">L’exemple suivant utilise la `foreach` saisie explicite dans une déclaration.</span><span class="sxs-lookup"><span data-stu-id="56da3-144">The following example uses explicit typing in a `foreach` statement.</span></span>

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > <span data-ttu-id="56da3-145">Veillez à ne pas changer accidentellement un type d’élément de la collection itérable.</span><span class="sxs-lookup"><span data-stu-id="56da3-145">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="56da3-146">Par exemple, il est <xref:System.Linq.IQueryable?displayProperty=nameWithType> facile <xref:System.Collections.IEnumerable?displayProperty=nameWithType> de `foreach` passer à dans une déclaration, ce qui modifie l’exécution d’une requête.</span><span class="sxs-lookup"><span data-stu-id="56da3-146">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-type"></a><span data-ttu-id="56da3-147">Type de données non signé</span><span class="sxs-lookup"><span data-stu-id="56da3-147">Unsigned Data Type</span></span>  
  
<span data-ttu-id="56da3-148">En règle générale, utilisez `int` plutôt que les types non signés.</span><span class="sxs-lookup"><span data-stu-id="56da3-148">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="56da3-149">L'utilisation de `int` est commun en C# et il est plus facile d'interagir avec d'autres bibliothèques lorsque vous utilisez `int`.</span><span class="sxs-lookup"><span data-stu-id="56da3-149">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="56da3-150">Tableaux</span><span class="sxs-lookup"><span data-stu-id="56da3-150">Arrays</span></span>  
  
<span data-ttu-id="56da3-151">Utilisez la syntaxe concise lorsque vous initialisez des tableaux sur la ligne de déclaration.</span><span class="sxs-lookup"><span data-stu-id="56da3-151">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="56da3-152">Délégués</span><span class="sxs-lookup"><span data-stu-id="56da3-152">Delegates</span></span>  
  
<span data-ttu-id="56da3-153">Utilisez la syntaxe concise pour créer des instances d'un type délégué.</span><span class="sxs-lookup"><span data-stu-id="56da3-153">Use the concise syntax to create instances of a delegate type.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="56da3-154">Instructions try-catch et using dans la gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="56da3-154">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="56da3-155">Utilisez une instruction [try-catch](../../language-reference/keywords/try-catch.md) pour la plus grande part de la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="56da3-155">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="56da3-156">Simplifiez votre code à l’aide de l’instruction [using](../../language-reference/keywords/using-statement.md) C#.</span><span class="sxs-lookup"><span data-stu-id="56da3-156">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="56da3-157">Si vous avez une instruction [try-finally](../../language-reference/keywords/try-finally.md) dans laquelle le seul code du bloc `finally` est un appel à la méthode <xref:System.IDisposable.Dispose%2A>, utilisez à la place une instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="56da3-157">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="56da3-158">Opérateurs && et &#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="56da3-158">&& and &#124;&#124; Operators</span></span>  
  
<span data-ttu-id="56da3-159">Pour éviter les exceptions et augmenter les [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) performances [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) en sautant des comparaisons inutiles, utilisez au lieu et [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) au lieu de [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) lorsque vous effectuez des comparaisons, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="56da3-159">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="56da3-160">New Operator</span><span class="sxs-lookup"><span data-stu-id="56da3-160">New Operator</span></span>  
  
- <span data-ttu-id="56da3-161">Utilisez la forme concise d'instanciation d'objets, avec un typage implicite, comme indiqué dans la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="56da3-161">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="56da3-162">La ligne précédente est équivalente à la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="56da3-162">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="56da3-163">Utilisez les initialiseurs d'objets pour simplifier la création d'objet.</span><span class="sxs-lookup"><span data-stu-id="56da3-163">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="56da3-164">Gestion des événements</span><span class="sxs-lookup"><span data-stu-id="56da3-164">Event Handling</span></span>  
  
<span data-ttu-id="56da3-165">Si vous définissez un gestionnaire d’événements que vous n’avez pas besoin de supprimer ultérieurement, utilisez une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="56da3-165">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="56da3-166">Membres static</span><span class="sxs-lookup"><span data-stu-id="56da3-166">Static Members</span></span>  
  
<span data-ttu-id="56da3-167">Appelez les membres [static](../../language-reference/keywords/static.md) en utilisant le nom de la classe : *Nom_classe.Membre_statique*.</span><span class="sxs-lookup"><span data-stu-id="56da3-167">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="56da3-168">Cette pratique rend le code plus lisible en clarifiant l'accès aux membres static.</span><span class="sxs-lookup"><span data-stu-id="56da3-168">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="56da3-169">Ne qualifiez pas un membre static défini dans une classe de base avec le nom d'une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="56da3-169">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="56da3-170">Lorsque ce code est compilé, la lisibilité du code est trompeuse et le code peut s'interrompre à l'avenir si vous ajoutez à la classe dérivée un membre static de même nom.</span><span class="sxs-lookup"><span data-stu-id="56da3-170">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="56da3-171">Requêtes LINQ</span><span class="sxs-lookup"><span data-stu-id="56da3-171">LINQ Queries</span></span>  
  
- <span data-ttu-id="56da3-172">Utilisez des noms explicites pour les variables de requête.</span><span class="sxs-lookup"><span data-stu-id="56da3-172">Use meaningful names for query variables.</span></span> <span data-ttu-id="56da3-173">L'exemple suivant utilise `seattleCustomers` pour les clients qui se trouvent à Seattle.</span><span class="sxs-lookup"><span data-stu-id="56da3-173">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="56da3-174">Utilisez des alias pour vous assurer que les noms de propriétés des types anonymes sont correctement écrits en majuscules à l'aide de la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="56da3-174">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="56da3-175">Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus.</span><span class="sxs-lookup"><span data-stu-id="56da3-175">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="56da3-176">Par exemple, si votre requête retourne un nom de client et un ID de distributeur, au lieu de les laisser sous la forme `Name` et `ID` dans le résultat, renommez-les pour montrer clairement que `Name` est le nom d'un client et `ID` l'ID d'un distributeur.</span><span class="sxs-lookup"><span data-stu-id="56da3-176">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="56da3-177">Utilisez le typage implicite dans la déclaration des variables de requête et des variables de portée.</span><span class="sxs-lookup"><span data-stu-id="56da3-177">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="56da3-178">Alignez les clauses de requête sous la clause [from](../../language-reference/keywords/from-clause.md), comme illustré dans les exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="56da3-178">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="56da3-179">Utilisez les clauses [where](../../language-reference/keywords/where-clause.md) avant les autres clauses de requête pour garantir que les clauses de requête ultérieures opèrent sur l’ensemble de données réduit et filtré.</span><span class="sxs-lookup"><span data-stu-id="56da3-179">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="56da3-180">Utilisez plusieurs clauses `from` au lieu d’une clause [join](../../language-reference/keywords/join-clause.md) pour accéder aux collections internes.</span><span class="sxs-lookup"><span data-stu-id="56da3-180">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="56da3-181">Par exemple, une collection d'objets `Student` peut contenir chacune une collection de scores de test.</span><span class="sxs-lookup"><span data-stu-id="56da3-181">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="56da3-182">Lorsque la requête suivante est exécutée, elle retourne chaque score supérieur à 90, avec le nom de l'étudiant correspondant.</span><span class="sxs-lookup"><span data-stu-id="56da3-182">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="56da3-183">Sécurité</span><span class="sxs-lookup"><span data-stu-id="56da3-183">Security</span></span>  

<span data-ttu-id="56da3-184">Suivez les instructions indiquées dans [Instructions de codage sécurisé](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="56da3-184">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56da3-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56da3-185">See also</span></span>

- [<span data-ttu-id="56da3-186">Conventions de codage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56da3-186">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="56da3-187">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="56da3-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
