---
title: Séparer les chaînes en sous-chaînes
description: Découvrez les différentes techniques permettant d’extraire des parties d’une chaîne, notamment String. Split, les expressions régulières et String. Substring.
ms.date: 10/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: 88947c4576b0496e4b4e45042d665e3ca5857c53
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403615"
---
# <a name="extract-substrings-from-a-string"></a><span data-ttu-id="219d1-103">Extraire les sous-chaînes d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="219d1-103">Extract substrings from a string</span></span>

<span data-ttu-id="219d1-104">Cet article présente des techniques différentes pour l’extraction de parties d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="219d1-104">This article covers some different techniques for extracting parts of a string.</span></span>

- <span data-ttu-id="219d1-105">Utilisez la [méthode Split](#stringsplit-method) lorsque les sous-chaînes que vous souhaitez sont séparées par un ou des caractères de délimitation connus.</span><span class="sxs-lookup"><span data-stu-id="219d1-105">Use the [Split method](#stringsplit-method) when the substrings you want are separated by a known delimiting character (or characters).</span></span>
- <span data-ttu-id="219d1-106">Les [expressions régulières](#regular-expressions) sont utiles lorsque la chaîne est conforme à un modèle fixe.</span><span class="sxs-lookup"><span data-stu-id="219d1-106">[Regular expressions](#regular-expressions) are useful when the string conforms to a fixed pattern.</span></span>
- <span data-ttu-id="219d1-107">Utilisez les [méthodes IndexOf et substring](#stringindexof-and-stringsubstring-methods) conjointement lorsque vous ne souhaitez pas extraire *toutes* les sous-chaînes d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="219d1-107">Use the [IndexOf and Substring methods](#stringindexof-and-stringsubstring-methods) in conjunction when you don't want to extract *all* of the substrings in a string.</span></span>

## <a name="stringsplit-method"></a><span data-ttu-id="219d1-108">String. Split, méthode</span><span class="sxs-lookup"><span data-stu-id="219d1-108">String.Split method</span></span>

<span data-ttu-id="219d1-109"><xref:System.String.Split%2A?displayProperty=nameWithType> fournit quelques surcharges pour vous aider à diviser une chaîne en un groupe de sous-chaînes en fonction d’un ou de plusieurs caractères de délimitation que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="219d1-109"><xref:System.String.Split%2A?displayProperty=nameWithType> provides a handful of overloads to help you break up a string into a group of substrings based on one or more delimiting characters that you specify.</span></span> <span data-ttu-id="219d1-110">Vous pouvez choisir de limiter le nombre total de sous-chaînes dans le résultat final, de supprimer les espaces blancs des sous-chaînes ou d’exclure les sous-chaînes vides.</span><span class="sxs-lookup"><span data-stu-id="219d1-110">You can choose to limit the total number of substrings in the final result, trim white-space characters from substrings, or exclude empty substrings.</span></span>

<span data-ttu-id="219d1-111">Les exemples suivants illustrent trois surcharges différentes de `String.Split()` .</span><span class="sxs-lookup"><span data-stu-id="219d1-111">The following examples show three different overloads of `String.Split()`.</span></span> <span data-ttu-id="219d1-112">Le premier exemple appelle la <xref:System.String.Split(System.Char[])> surcharge sans passer de caractères de séparation.</span><span class="sxs-lookup"><span data-stu-id="219d1-112">The first example calls the <xref:System.String.Split(System.Char[])> overload without passing any separator characters.</span></span> <span data-ttu-id="219d1-113">Lorsque vous ne spécifiez pas de caractères de délimitation, `String.Split()` utilise des délimiteurs par défaut, qui sont des espaces blancs, pour fractionner la chaîne.</span><span class="sxs-lookup"><span data-stu-id="219d1-113">When you don't specify any delimiting characters, `String.Split()` uses default delimiters, which are white-space characters, to split up the string.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

<span data-ttu-id="219d1-114">Comme vous pouvez le voir, les caractères de période ( `.` ) sont inclus dans deux des sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="219d1-114">As you can see, the period characters (`.`) are included in two of the substrings.</span></span> <span data-ttu-id="219d1-115">Si vous souhaitez exclure les caractères de période, vous pouvez ajouter le point comme caractère de délimitation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="219d1-115">If you want to exclude the period characters, you can add the period character as an additional delimiting character.</span></span> <span data-ttu-id="219d1-116">L’exemple suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="219d1-116">The next example shows how to do this.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

<span data-ttu-id="219d1-117">Les points sont supprimés des sous-chaînes, mais maintenant deux sous-chaînes vides supplémentaires ont été incluses.</span><span class="sxs-lookup"><span data-stu-id="219d1-117">The periods are gone from the substrings, but now two extra empty substrings have been included.</span></span> <span data-ttu-id="219d1-118">Ces sous-chaînes vides représentent la sous-chaîne entre le mot et le point qui le suit.</span><span class="sxs-lookup"><span data-stu-id="219d1-118">These empty substring represent the substring between the word and the period that follows it.</span></span> <span data-ttu-id="219d1-119">Pour omettre les sous-chaînes vides du tableau résultant, vous pouvez appeler la <xref:System.String.Split(System.Char[],System.StringSplitOptions)> surcharge et spécifier <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> pour le `options` paramètre.</span><span class="sxs-lookup"><span data-stu-id="219d1-119">To omit empty substrings from the resulting array, you can call the <xref:System.String.Split(System.Char[],System.StringSplitOptions)> overload and specify <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> for the `options` parameter.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a><span data-ttu-id="219d1-120">Expressions régulières</span><span class="sxs-lookup"><span data-stu-id="219d1-120">Regular expressions</span></span>

<span data-ttu-id="219d1-121">Si votre chaîne est conforme à un modèle fixe, vous pouvez utiliser une expression régulière pour extraire et gérer ses éléments.</span><span class="sxs-lookup"><span data-stu-id="219d1-121">If your string conforms to a fixed pattern, you can use a regular expression to extract and handle its elements.</span></span> <span data-ttu-id="219d1-122">Par exemple, si les chaînes prennent la forme « *Number* *Operand* *Number* », vous pouvez utiliser une [expression régulière](regular-expressions.md) pour extraire et gérer les éléments de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="219d1-122">For example, if strings take the form " *number* *operand* *number* ", you can use a [regular expression](regular-expressions.md) to extract and handle the string's elements.</span></span> <span data-ttu-id="219d1-123">Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="219d1-123">Here's an example:</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

<span data-ttu-id="219d1-124">Le modèle d’expression régulière `(\d+)\s+([-+*/])\s+(\d+)` est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="219d1-124">The regular expression pattern `(\d+)\s+([-+*/])\s+(\d+)` is defined like this:</span></span>

|<span data-ttu-id="219d1-125">Modèle</span><span class="sxs-lookup"><span data-stu-id="219d1-125">Pattern</span></span>|<span data-ttu-id="219d1-126">Description</span><span class="sxs-lookup"><span data-stu-id="219d1-126">Description</span></span>|
|-------------|-----------------|
|`(\d+)`|<span data-ttu-id="219d1-127">Mettre en correspondance un ou plusieurs chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="219d1-127">Match one or more decimal digits.</span></span> <span data-ttu-id="219d1-128">Il s'agit du premier groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="219d1-128">This is the first capturing group.</span></span>|
|`\s+`|<span data-ttu-id="219d1-129">Correspond à un ou plusieurs espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="219d1-129">Match one or more white-space characters.</span></span>|
|`([-+*/])`|<span data-ttu-id="219d1-130">Correspond à un signe d’opérateur arithmétique (+,-, \* ou/).</span><span class="sxs-lookup"><span data-stu-id="219d1-130">Match an arithmetic operator sign (+, -, \*, or /).</span></span> <span data-ttu-id="219d1-131">Il s'agit du deuxième groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="219d1-131">This is the second capturing group.</span></span>|
|`\s+`|<span data-ttu-id="219d1-132">Correspond à un ou plusieurs espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="219d1-132">Match one or more white-space characters.</span></span>|
|`(\d+)`|<span data-ttu-id="219d1-133">Mettre en correspondance un ou plusieurs chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="219d1-133">Match one or more decimal digits.</span></span> <span data-ttu-id="219d1-134">Il s'agit du troisième groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="219d1-134">This is the third capturing group.</span></span>|

<span data-ttu-id="219d1-135">Vous pouvez également utiliser une expression régulière pour extraire des sous-chaînes d’une chaîne basée sur un modèle plutôt qu’un ensemble fixe de caractères.</span><span class="sxs-lookup"><span data-stu-id="219d1-135">You can also use a regular expression to extract substrings from a string based on a pattern rather than a fixed set of characters.</span></span> <span data-ttu-id="219d1-136">Il s’agit d’un scénario courant lorsque l’une des conditions suivantes se produit :</span><span class="sxs-lookup"><span data-stu-id="219d1-136">This is a common scenario when either of these conditions occurs:</span></span>

- <span data-ttu-id="219d1-137">Un ou plusieurs des caractères de délimiteur ne servent pas *toujours* de délimiteur dans l' <xref:System.String> instance.</span><span class="sxs-lookup"><span data-stu-id="219d1-137">One or more of the delimiter characters does not *always* serve as a delimiter in the <xref:System.String> instance.</span></span>

- <span data-ttu-id="219d1-138">La séquence et le nombre de caractères de délimitation est variable ou inconnu.</span><span class="sxs-lookup"><span data-stu-id="219d1-138">The sequence and number of delimiter characters is variable or unknown.</span></span>

<span data-ttu-id="219d1-139">Par exemple, la <xref:System.String.Split%2A> méthode ne peut pas être utilisée pour fractionner la chaîne suivante, car le nombre de `\n` caractères (de saut de ligne) est variable et ils ne servent pas toujours de délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="219d1-139">For example, the <xref:System.String.Split%2A> method cannot be used to split the following string, because the number of `\n` (newline) characters is variable, and they don't always serve as delimiters.</span></span>

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

<span data-ttu-id="219d1-140">Une expression régulière peut fractionner cette chaîne facilement, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="219d1-140">A regular expression can split this string easily, as the following example shows.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

<span data-ttu-id="219d1-141">Le modèle d’expression régulière `\[([^\[\]]+)\]` est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="219d1-141">The regular expression pattern `\[([^\[\]]+)\]` is defined like this:</span></span>

|<span data-ttu-id="219d1-142">Modèle</span><span class="sxs-lookup"><span data-stu-id="219d1-142">Pattern</span></span>|<span data-ttu-id="219d1-143">Description</span><span class="sxs-lookup"><span data-stu-id="219d1-143">Description</span></span>|
|-------------|-----------------|
|`\[`|<span data-ttu-id="219d1-144">Mettre en correspondance un crochet ouvrant.</span><span class="sxs-lookup"><span data-stu-id="219d1-144">Match an opening bracket.</span></span>|
|`([^\[\]]+)`|<span data-ttu-id="219d1-145">Correspond à n’importe quel caractère qui n’est pas une ouverture ou un crochet fermant une ou plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="219d1-145">Match any character that is not an opening or a closing bracket one or more times.</span></span> <span data-ttu-id="219d1-146">Il s'agit du premier groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="219d1-146">This is the first capturing group.</span></span>|
|`\]`|<span data-ttu-id="219d1-147">Mettre en correspondance un crochet fermant.</span><span class="sxs-lookup"><span data-stu-id="219d1-147">Match a closing bracket.</span></span>|

<span data-ttu-id="219d1-148">La <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> méthode est presque identique à <xref:System.String.Split%2A?displayProperty=nameWithType> , à ceci près qu’elle fractionne une chaîne basée sur un modèle d’expression régulière au lieu d’un jeu de caractères fixe.</span><span class="sxs-lookup"><span data-stu-id="219d1-148">The <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method is almost identical to <xref:System.String.Split%2A?displayProperty=nameWithType>, except that it splits a string based on a regular expression pattern instead of a fixed character set.</span></span> <span data-ttu-id="219d1-149">Par exemple, l’exemple suivant utilise la <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> méthode pour fractionner une chaîne qui contient des sous-chaînes délimitées par différentes combinaisons de tirets et d’autres caractères.</span><span class="sxs-lookup"><span data-stu-id="219d1-149">For example, the following example uses the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to split a string that contains substrings delimited by various combinations of hyphens and other characters.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

<span data-ttu-id="219d1-150">Le modèle d’expression régulière `\s-\s?[+*]?\s?-\s` est défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="219d1-150">The regular expression pattern `\s-\s?[+*]?\s?-\s` is defined like this:</span></span>

|<span data-ttu-id="219d1-151">Modèle</span><span class="sxs-lookup"><span data-stu-id="219d1-151">Pattern</span></span>|<span data-ttu-id="219d1-152">Description</span><span class="sxs-lookup"><span data-stu-id="219d1-152">Description</span></span>|
|-------------|-----------------|
|`\s-`|<span data-ttu-id="219d1-153">Correspond à un espace blanc suivi d’un trait d’Union.</span><span class="sxs-lookup"><span data-stu-id="219d1-153">Match a white-space character followed by a hyphen.</span></span>|
|`\s?`|<span data-ttu-id="219d1-154">Mettre en correspondance zéro ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="219d1-154">Match zero or one white-space character.</span></span>|
|`[+*]?`|<span data-ttu-id="219d1-155">Correspond à zéro ou à une occurrence du caractère + ou \*.</span><span class="sxs-lookup"><span data-stu-id="219d1-155">Match zero or one occurrence of either the + or \* character.</span></span>|
|`\s?`|<span data-ttu-id="219d1-156">Mettre en correspondance zéro ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="219d1-156">Match zero or one white-space character.</span></span>|
|`-\s`|<span data-ttu-id="219d1-157">Faire correspondre un trait d’Union suivi d’un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="219d1-157">Match a hyphen followed by a white-space character.</span></span>|

## <a name="stringindexof-and-stringsubstring-methods"></a><span data-ttu-id="219d1-158">Méthodes String. IndexOf et String. Substring</span><span class="sxs-lookup"><span data-stu-id="219d1-158">String.IndexOf and String.Substring methods</span></span>

<span data-ttu-id="219d1-159">Si vous n’êtes pas intéressé par toutes les sous-chaînes d’une chaîne, vous préférerez peut-être utiliser l’une des méthodes de comparaison de chaînes qui retourne l’index auquel la correspondance commence.</span><span class="sxs-lookup"><span data-stu-id="219d1-159">If you aren't interested in all of the substrings in a string, you might prefer to work with one of the string comparison methods that returns the index at which the match begins.</span></span> <span data-ttu-id="219d1-160">Vous pouvez ensuite appeler la <xref:System.String.Substring%2A> méthode pour extraire la sous-chaîne de votre choix.</span><span class="sxs-lookup"><span data-stu-id="219d1-160">You can then call the <xref:System.String.Substring%2A> method to extract the substring that you want.</span></span> <span data-ttu-id="219d1-161">Les méthodes de comparaison de chaînes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="219d1-161">The string comparison methods include:</span></span>

- <span data-ttu-id="219d1-162"><xref:System.String.IndexOf%2A>, qui retourne l’index de base zéro de la première occurrence d’un caractère ou d’une chaîne dans une instance de chaîne.</span><span class="sxs-lookup"><span data-stu-id="219d1-162"><xref:System.String.IndexOf%2A>, which returns the zero-based index of the first occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="219d1-163"><xref:System.String.IndexOfAny%2A>, qui retourne l’index de base zéro dans l’instance de chaîne actuelle de la première occurrence d’un caractère dans un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="219d1-163"><xref:System.String.IndexOfAny%2A>, which returns the zero-based index in the current string instance of the first occurrence of any character in a character array.</span></span>

- <span data-ttu-id="219d1-164"><xref:System.String.LastIndexOf%2A>, qui retourne l’index de base zéro de la dernière occurrence d’un caractère ou d’une chaîne dans une instance de chaîne.</span><span class="sxs-lookup"><span data-stu-id="219d1-164"><xref:System.String.LastIndexOf%2A>, which returns the zero-based index of the last occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="219d1-165"><xref:System.String.LastIndexOfAny%2A>, qui retourne un index de base zéro dans l’instance de chaîne actuelle de la dernière occurrence d’un caractère dans un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="219d1-165"><xref:System.String.LastIndexOfAny%2A>, which returns a zero-based index in the current string instance of the last occurrence of any character in a character array.</span></span>

<span data-ttu-id="219d1-166">L’exemple suivant utilise la <xref:System.String.IndexOf%2A> méthode pour rechercher les points dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="219d1-166">The following example uses the <xref:System.String.IndexOf%2A> method to find the periods in a string.</span></span> <span data-ttu-id="219d1-167">Il utilise ensuite la <xref:System.String.Substring%2A> méthode pour retourner des phrases complètes.</span><span class="sxs-lookup"><span data-stu-id="219d1-167">It then uses the <xref:System.String.Substring%2A> method to return full sentences.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a><span data-ttu-id="219d1-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="219d1-168">See also</span></span>

- [<span data-ttu-id="219d1-169">Opérations de chaînes de base dans .NET</span><span class="sxs-lookup"><span data-stu-id="219d1-169">Basic string operations in .NET</span></span>](basic-string-operations.md)
- [<span data-ttu-id="219d1-170">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="219d1-170">.NET regular expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="219d1-171">Comment analyser des chaînes à l’aide de String. Split en C #</span><span class="sxs-lookup"><span data-stu-id="219d1-171">How to parse strings using String.Split in C#</span></span>](../../csharp/how-to/parse-strings-using-split.md)
