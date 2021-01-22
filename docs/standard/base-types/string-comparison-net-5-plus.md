---
title: Changements de comportement lors de la comparaison de chaînes sur .NET 5 +
description: En savoir plus sur les changements de comportement de comparaison de chaînes dans .NET 5 et versions ultérieures sur Windows.
ms.topic: conceptual
ms.date: 12/07/2020
ms.openlocfilehash: 0db8477ce4e8c3a7167c719e2a29a32e5346a8e7
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692693"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a><span data-ttu-id="25470-103">Changements de comportement lors de la comparaison de chaînes sur .NET 5 +</span><span class="sxs-lookup"><span data-stu-id="25470-103">Behavior changes when comparing strings on .NET 5+</span></span>

<span data-ttu-id="25470-104">.NET 5,0 introduit un changement de comportement au moment de l’exécution où les API de globalisation [utilisent désormais ICU par défaut](../../core/compatibility/globalization/5.0/icu-globalization-api.md) sur toutes les plateformes prises en charge.</span><span class="sxs-lookup"><span data-stu-id="25470-104">.NET 5.0 introduces a runtime behavioral change where globalization APIs [now use ICU by default](../../core/compatibility/globalization/5.0/icu-globalization-api.md) across all supported platforms.</span></span> <span data-ttu-id="25470-105">Il s’agit d’une nouveauté par rapport aux versions antérieures de .NET Core et de .NET Framework, qui utilisent la fonctionnalité NLS (National Language Support) du système d’exploitation lors de l’exécution sous Windows.</span><span class="sxs-lookup"><span data-stu-id="25470-105">This is a departure from earlier versions of .NET Core and from .NET Framework, which utilize the operating system's national language support (NLS) functionality when running on Windows.</span></span> <span data-ttu-id="25470-106">Pour plus d’informations sur ces modifications, y compris les commutateurs de compatibilité qui peuvent rétablir le changement de comportement, consultez [globalisation et ICU .net](../globalization-localization/globalization-icu.md).</span><span class="sxs-lookup"><span data-stu-id="25470-106">For more information on these changes, including compatibility switches that can revert the behavior change, see [.NET globalization and ICU](../globalization-localization/globalization-icu.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="25470-107">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="25470-107">Reason for change</span></span>

<span data-ttu-id="25470-108">Cette modification a été introduite pour unifier. Comportement de la globalisation du réseau sur tous les systèmes d’exploitation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="25470-108">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="25470-109">Il offre également la possibilité pour les applications de regrouper leurs propres bibliothèques de globalisation plutôt que de dépendre des bibliothèques intégrées du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="25470-109">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the OS's built-in libraries.</span></span> <span data-ttu-id="25470-110">Pour plus d’informations, consultez [la notification de modification avec rupture](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span><span class="sxs-lookup"><span data-stu-id="25470-110">For more information, see [the breaking change notification](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="25470-111">Différences de comportement</span><span class="sxs-lookup"><span data-stu-id="25470-111">Behavioral differences</span></span>

<span data-ttu-id="25470-112">Si vous utilisez des fonctions comme si vous `string.IndexOf(string)` n’appelez pas la surcharge qui prend un <xref:System.StringComparison> argument, vous pouvez envisager d’effectuer une recherche *ordinale* , mais au lieu de cela, vous prenez par inadvertance une dépendance vis-à-vis du comportement propre à la culture.</span><span class="sxs-lookup"><span data-stu-id="25470-112">If you use functions like `string.IndexOf(string)` without calling the overload that takes a <xref:System.StringComparison> argument, you might intend to perform an *ordinal* search, but instead you inadvertently take a dependency on culture-specific behavior.</span></span> <span data-ttu-id="25470-113">Dans la mesure où NLS et ICU implémentent une logique différente dans leurs comparateurs linguistiques, les résultats de méthodes comme `string.IndexOf(string)` peuvent retourner des valeurs inattendues.</span><span class="sxs-lookup"><span data-stu-id="25470-113">Since NLS and ICU implement different logic in their linguistic comparers, the results of methods like `string.IndexOf(string)` can return unexpected values.</span></span>

<span data-ttu-id="25470-114">Cela peut se manifester même à des endroits où vous n’êtes pas toujours en mesure d’activer les fonctionnalités de globalisation.</span><span class="sxs-lookup"><span data-stu-id="25470-114">This can manifest itself even in places where you aren't always expecting globalization facilities to be active.</span></span> <span data-ttu-id="25470-115">Par exemple, le code suivant peut produire une réponse différente selon le runtime actuel.</span><span class="sxs-lookup"><span data-stu-id="25470-115">For example, the following code can produce a different answer depending on the current runtime.</span></span>

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a><span data-ttu-id="25470-116">Protection contre les comportements inattendus</span><span class="sxs-lookup"><span data-stu-id="25470-116">Guard against unexpected behavior</span></span>

<span data-ttu-id="25470-117">Cette section fournit deux options pour traiter les changements de comportement inattendus dans .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="25470-117">This section provides two options for dealing with unexpected behavior changes in .NET 5.0.</span></span>

### <a name="enable-code-analyzers"></a><span data-ttu-id="25470-118">Activer les analyseurs de code</span><span class="sxs-lookup"><span data-stu-id="25470-118">Enable code analyzers</span></span>

<span data-ttu-id="25470-119">Les [analyseurs de code](../../fundamentals/code-analysis/overview.md) peuvent détecter les sites d’appel éventuellement bogués.</span><span class="sxs-lookup"><span data-stu-id="25470-119">[Code analyzers](../../fundamentals/code-analysis/overview.md) can detect possibly buggy call sites.</span></span> <span data-ttu-id="25470-120">Pour vous protéger contre les comportements étonnants, nous vous recommandons d’activer les analyseurs de la plateforme du compilateur .NET (Roslyn) dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="25470-120">To help guard against any surprising behaviors, we recommend enabling .NET compiler platform (Roslyn) analyzers in your project.</span></span> <span data-ttu-id="25470-121">Les analyseurs aident à marquer le code qui peut utiliser par inadvertance un comparateur linguistique lorsqu’un comparateur ordinal était probablement prévu.</span><span class="sxs-lookup"><span data-stu-id="25470-121">The analyzers help flag code that might inadvertently be using a linguistic comparer when an ordinal comparer was likely intended.</span></span> <span data-ttu-id="25470-122">Les règles suivantes doivent vous aider à signaler ces problèmes :</span><span class="sxs-lookup"><span data-stu-id="25470-122">The following rules should help flag these issues:</span></span>

- [<span data-ttu-id="25470-123">CA1307 : Spécifier StringComparison pour clarifier</span><span class="sxs-lookup"><span data-stu-id="25470-123">CA1307: Specify StringComparison for clarity</span></span>](../../fundamentals/code-analysis/quality-rules/ca1307.md)
- [<span data-ttu-id="25470-124">CA1309 : Utiliser StringComparison avec la valeur Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-124">CA1309: Use ordinal StringComparison</span></span>](../../fundamentals/code-analysis/quality-rules/ca1309.md)
- [<span data-ttu-id="25470-125">CA1310 : Spécifier StringComparison pour corriger</span><span class="sxs-lookup"><span data-stu-id="25470-125">CA1310: Specify StringComparison for correctness</span></span>](../../fundamentals/code-analysis/quality-rules/ca1310.md)

<span data-ttu-id="25470-126">Ces règles spécifiques ne sont pas activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="25470-126">These specific rules aren't enabled by default.</span></span> <span data-ttu-id="25470-127">Pour les activer et afficher les violations comme des erreurs de build, définissez les propriétés suivantes dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="25470-127">To enable them and show any violations as build errors, set the following properties in your project file:</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
  <WarningsAsErrors>$(WarningsAsErrors);CA1307;CA1309;CA1310</WarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="25470-128">L’extrait de code suivant montre des exemples de code qui produit les avertissements ou erreurs de l’analyseur de code appropriés.</span><span class="sxs-lookup"><span data-stu-id="25470-128">The following snippet shows examples of code that produces the relevant code analyzer warnings or errors.</span></span>

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1310 for string; CA1307 matches on char ','
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

<span data-ttu-id="25470-129">De même, lors de l’instanciation d’une collection triée de chaînes ou du tri d’une collection de chaînes existante, spécifiez un comparateur explicite.</span><span class="sxs-lookup"><span data-stu-id="25470-129">Similarly, when instantiating a sorted collection of strings or sorting an existing string-based collection, specify an explicit comparer.</span></span>

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

### <a name="revert-back-to-nls-behaviors"></a><span data-ttu-id="25470-130">Revenir aux comportements NLS</span><span class="sxs-lookup"><span data-stu-id="25470-130">Revert back to NLS behaviors</span></span>

<span data-ttu-id="25470-131">Pour restaurer les applications .NET 5 à des comportements NLS plus anciens lors de l’exécution sous Windows, suivez les étapes de la section [globalisation et ICU de .net](../globalization-localization/globalization-icu.md).</span><span class="sxs-lookup"><span data-stu-id="25470-131">To revert .NET 5 applications back to older NLS behaviors when running on Windows, follow the steps in [.NET Globalization and ICU](../globalization-localization/globalization-icu.md).</span></span> <span data-ttu-id="25470-132">Ce commutateur de compatibilité à l’échelle de l’application doit être défini au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="25470-132">This application-wide compatibility switch must be set at the application level.</span></span> <span data-ttu-id="25470-133">Les bibliothèques individuelles ne peuvent pas accepter ou refuser ce comportement.</span><span class="sxs-lookup"><span data-stu-id="25470-133">Individual libraries cannot opt-in or opt-out of this behavior.</span></span>

> [!TIP]
> <span data-ttu-id="25470-134">Nous vous recommandons vivement d’activer les règles d’analyse du code [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md), [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md)et [ca1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) pour aider à améliorer l’hygiène du code et découvrir les bogues latentes existants.</span><span class="sxs-lookup"><span data-stu-id="25470-134">We strongly recommend you enable the [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md), [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), and [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) code analysis rules to help improve code hygiene and discover any existing latent bugs.</span></span> <span data-ttu-id="25470-135">Pour plus d’informations, consultez [activer les analyseurs de code](#enable-code-analyzers).</span><span class="sxs-lookup"><span data-stu-id="25470-135">For more information, see [Enable code analyzers](#enable-code-analyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="25470-136">API affectées</span><span class="sxs-lookup"><span data-stu-id="25470-136">Affected APIs</span></span>

<span data-ttu-id="25470-137">La plupart des applications .NET ne rencontrent pas de comportements inattendus en raison des modifications apportées à .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="25470-137">Most .NET applications won't encounter any unexpected behaviors due to the changes in .NET 5.0.</span></span> <span data-ttu-id="25470-138">Toutefois, en raison du nombre d’API affectées et de la façon dont ces API sont les plus larges de l’écosystème .NET, vous devez être conscient du potentiel de .NET 5,0 pour introduire des comportements indésirables ou pour exposer des bogues latentes qui existent déjà dans votre application.</span><span class="sxs-lookup"><span data-stu-id="25470-138">However, due to the number of affected APIs and how foundational these APIs are to the wider .NET ecosystem, you should be aware of the potential for .NET 5.0 to introduce unwanted behaviors or to expose latent bugs that already exist in your application.</span></span>

<span data-ttu-id="25470-139">Les API affectées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="25470-139">The affected APIs include:</span></span>

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <span data-ttu-id="25470-140"><xref:System.Globalization.TextInfo?displayProperty=fullName> (la plupart des membres)</span><span class="sxs-lookup"><span data-stu-id="25470-140"><xref:System.Globalization.TextInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="25470-141"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (la plupart des membres)</span><span class="sxs-lookup"><span data-stu-id="25470-141"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="25470-142"><xref:System.Array.Sort%2A?displayProperty=fullName> (lors du tri de tableaux de chaînes)</span><span class="sxs-lookup"><span data-stu-id="25470-142"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting arrays of strings)</span></span>
- <span data-ttu-id="25470-143"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (lorsque les éléments de la liste sont des chaînes)</span><span class="sxs-lookup"><span data-stu-id="25470-143"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="25470-144"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (lorsque les clés sont des chaînes)</span><span class="sxs-lookup"><span data-stu-id="25470-144"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="25470-145"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (lorsque les clés sont des chaînes)</span><span class="sxs-lookup"><span data-stu-id="25470-145"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="25470-146"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (lorsque l’ensemble contient des chaînes)</span><span class="sxs-lookup"><span data-stu-id="25470-146"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

> [!NOTE]
> <span data-ttu-id="25470-147">Il ne s’agit pas d’une liste exhaustive des API affectées.</span><span class="sxs-lookup"><span data-stu-id="25470-147">This is not an exhaustive list of affected APIs.</span></span>

<span data-ttu-id="25470-148">Toutes les API ci-dessus utilisent la recherche et la comparaison de chaînes *linguistiques* à l’aide de la [culture actuelle](xref:System.Threading.Thread.CurrentCulture)du thread, par défaut.</span><span class="sxs-lookup"><span data-stu-id="25470-148">All of the above APIs use *linguistic* string searching and comparison using the thread's [current culture](xref:System.Threading.Thread.CurrentCulture), by default.</span></span> <span data-ttu-id="25470-149">Les différences entre la recherche *linguistique* et *ordinale* et la comparaison sont appelées dans la [recherche ordinale et la recherche et la comparaison linguistiques](#ordinal-vs-linguistic-search-and-comparison).</span><span class="sxs-lookup"><span data-stu-id="25470-149">The differences between *linguistic* and *ordinal* search and comparison are called out in the [Ordinal vs. linguistic search and comparison](#ordinal-vs-linguistic-search-and-comparison).</span></span>

<span data-ttu-id="25470-150">Étant donné que ICU implémente les comparaisons de chaînes linguistiques différemment de NLS, les applications Windows qui effectuent la mise à niveau vers .NET 5,0 à partir d’une version antérieure de .NET Core ou de .NET Framework et qui appellent une des API affectées peuvent remarquer que les API commencent à présenter des comportements différents.</span><span class="sxs-lookup"><span data-stu-id="25470-150">Because ICU implements linguistic string comparisons differently from NLS, Windows-based applications that upgrade to .NET 5.0 from an earlier version of .NET Core or .NET Framework and that call one of the affected APIs may notice that the APIs begin exhibiting different behaviors.</span></span>

### <a name="exceptions"></a><span data-ttu-id="25470-151">Exceptions</span><span class="sxs-lookup"><span data-stu-id="25470-151">Exceptions</span></span>

* <span data-ttu-id="25470-152">Si une API accepte un `StringComparison` paramètre ou explicite `CultureInfo` , ce paramètre remplace le comportement par défaut de l’API.</span><span class="sxs-lookup"><span data-stu-id="25470-152">If an API accepts an explicit `StringComparison` or `CultureInfo` parameter, that parameter overrides the API's default behavior.</span></span>
* <span data-ttu-id="25470-153">`System.String` les membres où le premier paramètre est de type `char` (par exemple, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType> ) utilisent la recherche ordinale, sauf si l’appelant passe un `StringComparison` argument explicite qui spécifie `CurrentCulture[IgnoreCase]` ou `InvariantCulture[IgnoreCase]` .</span><span class="sxs-lookup"><span data-stu-id="25470-153">`System.String` members where the first parameter is of type `char` (for example, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>) use ordinal searching, unless the caller passes an explicit `StringComparison` argument that specifies `CurrentCulture[IgnoreCase]` or `InvariantCulture[IgnoreCase]`.</span></span>

<span data-ttu-id="25470-154">Pour une analyse plus détaillée du comportement par défaut de chaque <xref:System.String> API, consultez la section [types de comparaison et de recherche par défaut](#default-search-and-comparison-types) .</span><span class="sxs-lookup"><span data-stu-id="25470-154">For a more detailed analysis of the default behavior of each <xref:System.String> API, see the [Default search and comparison types](#default-search-and-comparison-types) section.</span></span>

## <a name="ordinal-vs-linguistic-search-and-comparison"></a><span data-ttu-id="25470-155">Comparaison entre les comparaisons ordinale et linguistique</span><span class="sxs-lookup"><span data-stu-id="25470-155">Ordinal vs. linguistic search and comparison</span></span>

<span data-ttu-id="25470-156">La recherche et la comparaison *ordinale* (également appelée *non linguistique*) décomposent une chaîne en `char` éléments individuels et effectuent une recherche de type char-by-char ou une comparaison.</span><span class="sxs-lookup"><span data-stu-id="25470-156">*Ordinal* (also known as *non-linguistic*) search and comparison decomposes a string into its individual `char` elements and performs a char-by-char search or comparison.</span></span> <span data-ttu-id="25470-157">Par exemple, les chaînes `"dog"` et `"dog"` sont considérées comme *égales* sous un `Ordinal` comparateur, étant donné que les deux chaînes se composent exactement de la même séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="25470-157">For example, the strings `"dog"` and `"dog"` compare as *equal* under an `Ordinal` comparer, since the two strings consist of the exact same sequence of chars.</span></span> <span data-ttu-id="25470-158">Toutefois, `"dog"` et `"Dog"` sont considérés comme *n’étant pas égaux* sous un `Ordinal` comparateur, car ils ne se composent pas exactement de la même séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="25470-158">However, `"dog"` and `"Dog"` compare as *not equal* under an `Ordinal` comparer, because they don't consist of the exact same sequence of chars.</span></span> <span data-ttu-id="25470-159">Autrement dit, le `'D'` point de code en majuscules `U+0044` se produit avant le `'d'` point de code en minuscules `U+0064` , ce qui entraîne un `"dog"` Tri avant `"Dog"` .</span><span class="sxs-lookup"><span data-stu-id="25470-159">That is, uppercase `'D'`'s code point `U+0044` occurs before lowercase `'d'`'s code point `U+0064`, resulting in `"dog"` sorting before `"Dog"`.</span></span>

<span data-ttu-id="25470-160">Un `OrdinalIgnoreCase` comparateur continue de fonctionner en fonction du caractère par caractère, mais il élimine les différences de casse lors de l’exécution de l’opération.</span><span class="sxs-lookup"><span data-stu-id="25470-160">An `OrdinalIgnoreCase` comparer still operates on a char-by-char basis, but it eliminates case differences while performing the operation.</span></span> <span data-ttu-id="25470-161">Sous un `OrdinalIgnoreCase` comparateur, les paires de caractères `'d'` et `'D'` sont considérées comme *égales*, comme les paires de caractères `'á'` et `'Á'` .</span><span class="sxs-lookup"><span data-stu-id="25470-161">Under an `OrdinalIgnoreCase` comparer, the char pairs `'d'` and `'D'` compare as *equal*, as do the char pairs `'á'` and `'Á'`.</span></span> <span data-ttu-id="25470-162">Toutefois, le caractère non accentué `'a'` *n’est pas* comparé au caractère accentué `'á'` .</span><span class="sxs-lookup"><span data-stu-id="25470-162">But the unaccented char `'a'` compares as *not equal* to the accented char `'á'`.</span></span>

<span data-ttu-id="25470-163">Des exemples sont fournis dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="25470-163">Some examples of this are provided in the following table:</span></span>

| <span data-ttu-id="25470-164">Chaîne 1</span><span class="sxs-lookup"><span data-stu-id="25470-164">String 1</span></span> | <span data-ttu-id="25470-165">Chaîne 2</span><span class="sxs-lookup"><span data-stu-id="25470-165">String 2</span></span> | <span data-ttu-id="25470-166">`Ordinal` considèrent</span><span class="sxs-lookup"><span data-stu-id="25470-166">`Ordinal` comparison</span></span> | <span data-ttu-id="25470-167">`OrdinalIgnoreCase` considèrent</span><span class="sxs-lookup"><span data-stu-id="25470-167">`OrdinalIgnoreCase` comparison</span></span> |
|---|---|---|---|
| `"dog"` | `"dog"` | <span data-ttu-id="25470-168">equal</span><span class="sxs-lookup"><span data-stu-id="25470-168">equal</span></span> | <span data-ttu-id="25470-169">equal</span><span class="sxs-lookup"><span data-stu-id="25470-169">equal</span></span> |
| `"dog"` | `"Dog"` | <span data-ttu-id="25470-170">différent de</span><span class="sxs-lookup"><span data-stu-id="25470-170">not equal</span></span> | <span data-ttu-id="25470-171">equal</span><span class="sxs-lookup"><span data-stu-id="25470-171">equal</span></span> |
| `"resume"` | `"Resume"` | <span data-ttu-id="25470-172">différent de</span><span class="sxs-lookup"><span data-stu-id="25470-172">not equal</span></span> | <span data-ttu-id="25470-173">equal</span><span class="sxs-lookup"><span data-stu-id="25470-173">equal</span></span> |
| `"resume"` | `"résumé"` | <span data-ttu-id="25470-174">différent de</span><span class="sxs-lookup"><span data-stu-id="25470-174">not equal</span></span> | <span data-ttu-id="25470-175">différent de</span><span class="sxs-lookup"><span data-stu-id="25470-175">not equal</span></span> |

<span data-ttu-id="25470-176">Unicode permet également aux chaînes d’avoir plusieurs représentations en mémoire différentes.</span><span class="sxs-lookup"><span data-stu-id="25470-176">Unicode also allows strings to have several different in-memory representations.</span></span> <span data-ttu-id="25470-177">Par exemple, un e-aigu (é) peut être représenté de deux manières :</span><span class="sxs-lookup"><span data-stu-id="25470-177">For example, an e-acute (é) can be represented in two possible ways:</span></span>

* <span data-ttu-id="25470-178">Caractère littéral unique `'é'` (également écrit comme `'\u00E9'` ).</span><span class="sxs-lookup"><span data-stu-id="25470-178">A single literal `'é'` character (also written as `'\u00E9'`).</span></span>
* <span data-ttu-id="25470-179">Caractère non accentué littéral `'e'` , suivi d’un caractère modificateur d’accentuation de combinaison `'\u0301'` .</span><span class="sxs-lookup"><span data-stu-id="25470-179">A literal unaccented `'e'` character, followed by a combining accent modifier character `'\u0301'`.</span></span>

<span data-ttu-id="25470-180">Cela signifie que les _quatre_ chaînes suivantes sont toutes générées `"résumé"` lorsqu’elles sont affichées, même si leurs éléments constitutifs sont différents.</span><span class="sxs-lookup"><span data-stu-id="25470-180">This means that the following _four_ strings all result in `"résumé"` when displayed, even though their constituent pieces are different.</span></span> <span data-ttu-id="25470-181">Les chaînes utilisent une combinaison de caractères littéraux `'é'` ou de caractères non accentués littéraux `'e'` plus le modificateur d’accent de combinaison `'\u0301'` .</span><span class="sxs-lookup"><span data-stu-id="25470-181">The strings use a combination of literal `'é'` characters or literal unaccented `'e'` characters plus the combining accent modifier `'\u0301'`.</span></span>

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

<span data-ttu-id="25470-182">Dans un comparateur ordinal, aucune de ces chaînes n’est comparée les unes aux autres.</span><span class="sxs-lookup"><span data-stu-id="25470-182">Under an ordinal comparer, none of these strings compare as equal to each other.</span></span> <span data-ttu-id="25470-183">Cela est dû au fait qu’ils contiennent tous des séquences de caractères sous-jacentes différentes, même si elles sont toutes affichées à l’écran.</span><span class="sxs-lookup"><span data-stu-id="25470-183">This is because they all contain different underlying char sequences, even though when they're rendered to the screen, they all look the same.</span></span>

<span data-ttu-id="25470-184">Lors de l’exécution d’une `string.IndexOf(..., StringComparison.Ordinal)` opération, le runtime recherche une correspondance exacte de sous-chaînes.</span><span class="sxs-lookup"><span data-stu-id="25470-184">When performing a `string.IndexOf(..., StringComparison.Ordinal)` operation, the runtime looks for an exact substring match.</span></span> <span data-ttu-id="25470-185">Les résultats sont les suivants.</span><span class="sxs-lookup"><span data-stu-id="25470-185">The results are as follows.</span></span>

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

<span data-ttu-id="25470-186">Les routines de recherche ordinale et de comparaison ne sont jamais affectées par le paramètre de culture du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="25470-186">Ordinal search and comparison routines are never affected by the current thread's culture setting.</span></span>

<span data-ttu-id="25470-187">Les routines de recherche *linguistique* et de comparaison décomposent une chaîne en *éléments de classement* et effectuent des recherches ou des comparaisons sur ces éléments.</span><span class="sxs-lookup"><span data-stu-id="25470-187">*Linguistic* search and comparison routines decompose a string into *collation elements* and perform searches or comparisons on these elements.</span></span> <span data-ttu-id="25470-188">Il n’y a pas nécessairement un mappage de 1:1 entre les caractères d’une chaîne et ses éléments de classement constitutifs.</span><span class="sxs-lookup"><span data-stu-id="25470-188">There's not necessarily a 1:1 mapping between a string's characters and its constituent collation elements.</span></span> <span data-ttu-id="25470-189">Par exemple, une chaîne de longueur 2 peut se composer d’un seul élément de classement.</span><span class="sxs-lookup"><span data-stu-id="25470-189">For example, a string of length 2 may consist of only a single collation element.</span></span> <span data-ttu-id="25470-190">Lorsque deux chaînes sont comparées selon un mode de prise en charge linguistique, le comparateur vérifie si les deux éléments de classement des chaînes ont la même signification sémantique, même si les caractères littéraux de la chaîne sont différents.</span><span class="sxs-lookup"><span data-stu-id="25470-190">When two strings are compared in a linguistic-aware fashion, the comparer checks whether the two strings' collation elements have the same semantic meaning, even if the string's literal characters are different.</span></span>

<span data-ttu-id="25470-191">Reprenons la chaîne `"résumé"` et ses quatre représentations différentes.</span><span class="sxs-lookup"><span data-stu-id="25470-191">Consider again the string `"résumé"` and its four different representations.</span></span> <span data-ttu-id="25470-192">Le tableau suivant présente chaque représentation décomposée en ses éléments de classement.</span><span class="sxs-lookup"><span data-stu-id="25470-192">The following table shows each representation broken down into its collation elements.</span></span>

| <span data-ttu-id="25470-193">String</span><span class="sxs-lookup"><span data-stu-id="25470-193">String</span></span> | <span data-ttu-id="25470-194">En tant qu’éléments de classement</span><span class="sxs-lookup"><span data-stu-id="25470-194">As collation elements</span></span> |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

<span data-ttu-id="25470-195">Un élément de classement correspond vaguement à ce que les lecteurs considèrent comme un caractère unique ou un cluster de caractères.</span><span class="sxs-lookup"><span data-stu-id="25470-195">A collation element corresponds loosely to what readers would think of as a single character or cluster of characters.</span></span> <span data-ttu-id="25470-196">Son concept est similaire à celui d’un [cluster graphèmes](character-encoding-introduction.md#grapheme-clusters) , mais il englobe un parapluie un peu plus grand.</span><span class="sxs-lookup"><span data-stu-id="25470-196">It's conceptually similar to a [grapheme cluster](character-encoding-introduction.md#grapheme-clusters) but encompasses a somewhat larger umbrella.</span></span>

<span data-ttu-id="25470-197">Sous un comparateur linguistique, les correspondances exactes ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="25470-197">Under a linguistic comparer, exact matches aren't necessary.</span></span> <span data-ttu-id="25470-198">Les éléments de classement sont comparés en fonction de leur signification sémantique.</span><span class="sxs-lookup"><span data-stu-id="25470-198">Collation elements are instead compared based on their semantic meaning.</span></span> <span data-ttu-id="25470-199">Par exemple, un comparateur linguistique traite les sous-chaînes `"\u00E9"` et `"e\u0301"` comme étant égales, car elles sont à la fois sémantiquement moyennes « un e minuscule avec un modificateur d’accent aigu ».</span><span class="sxs-lookup"><span data-stu-id="25470-199">For example, a linguistic comparer treats the substrings `"\u00E9"` and `"e\u0301"` as equal since they both semantically mean "a lowercase e with an acute accent modifier."</span></span> <span data-ttu-id="25470-200">Cela permet `IndexOf` à la méthode de correspondre à la sous-chaîne `"e\u0301"` dans une chaîne plus grande qui contient la sous-chaîne sémantiquement équivalente `"\u00E9"` , comme illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="25470-200">This allows the `IndexOf` method to match the substring `"e\u0301"` within a larger string that contains the semantically equivalent substring `"\u00E9"`, as shown in the following code sample.</span></span>

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

<span data-ttu-id="25470-201">Par conséquent, deux chaînes de longueurs différentes peuvent être considérées comme égales si une comparaison linguistique est utilisée.</span><span class="sxs-lookup"><span data-stu-id="25470-201">As a consequence of this, two strings of different lengths may compare as equal if a linguistic comparison is used.</span></span> <span data-ttu-id="25470-202">Les appelants doivent s’occuper de la logique à cas spécial qui traite la longueur des chaînes dans de tels scénarios.</span><span class="sxs-lookup"><span data-stu-id="25470-202">Callers should take care not to special-case logic that deals with string length in such scenarios.</span></span>

<span data-ttu-id="25470-203">Les routines de recherche et de comparaison *prenant en compte la culture* sont une forme spéciale de routines de recherche linguistique et de comparaison.</span><span class="sxs-lookup"><span data-stu-id="25470-203">*Culture-aware* search and comparison routines are a special form of linguistic search and comparison routines.</span></span> <span data-ttu-id="25470-204">Sous un comparateur dépendant de la culture, le concept d’élément de classement est étendu pour inclure des informations spécifiques à la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="25470-204">Under a culture-aware comparer, the concept of a collation element is extended to include information specific to the specified culture.</span></span>

<span data-ttu-id="25470-205">Par exemple, [dans l’alphabet hongrois](https://en.wikipedia.org/wiki/Hungarian_alphabet), lorsque les deux caractères \<dz\> apparaissent en arrière-plan, ils sont considérés comme des lettres uniques distinctes de \<d\> ou \<z\> .</span><span class="sxs-lookup"><span data-stu-id="25470-205">For example, [in the Hungarian alphabet](https://en.wikipedia.org/wiki/Hungarian_alphabet), when the two characters \<dz\> appear back-to-back, they are considered their own unique letter distinct from either \<d\> or \<z\>.</span></span> <span data-ttu-id="25470-206">Cela signifie que lorsque \<dz\> est visible dans une chaîne, un comparateur prenant en charge la culture hongrois le traite comme un élément de classement unique.</span><span class="sxs-lookup"><span data-stu-id="25470-206">This means that when \<dz\> is seen in a string, a Hungarian culture-aware comparer treats it as a single collation element.</span></span>

| <span data-ttu-id="25470-207">String</span><span class="sxs-lookup"><span data-stu-id="25470-207">String</span></span> | <span data-ttu-id="25470-208">En tant qu’éléments de classement</span><span class="sxs-lookup"><span data-stu-id="25470-208">As collation elements</span></span> | <span data-ttu-id="25470-209">Notes</span><span class="sxs-lookup"><span data-stu-id="25470-209">Remarks</span></span> |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | <span data-ttu-id="25470-210">(à l’aide d’un comparateur linguistique standard)</span><span class="sxs-lookup"><span data-stu-id="25470-210">(using a standard linguistic comparer)</span></span> |
| `"endz"` | `"e" + "n" + "dz"` | <span data-ttu-id="25470-211">(à l’aide d’un comparateur prenant en charge la culture hongrois)</span><span class="sxs-lookup"><span data-stu-id="25470-211">(using a Hungarian culture-aware comparer)</span></span> |

<span data-ttu-id="25470-212">Lors de l’utilisation d’un comparateur prenant en charge la culture hongrois, cela signifie que la chaîne `"endz"` *ne* se termine pas par la sous-chaîne `"z"` , car < \dz \> et < \z \> sont considérés comme des éléments de classement ayant une signification sémantique différente.</span><span class="sxs-lookup"><span data-stu-id="25470-212">When using a Hungarian culture-aware comparer, this means that the string `"endz"` *does not* end with the substring `"z"`, as <\dz\> and <\z\> are considered collation elements with different semantic meaning.</span></span>

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - <span data-ttu-id="25470-213">Comportement : les comparateurs de langue et de culture peuvent subir des ajustements de comportement de temps à autre.</span><span class="sxs-lookup"><span data-stu-id="25470-213">Behavior: Linguistic and culture-aware comparers can undergo behavioral adjustments from time to time.</span></span> <span data-ttu-id="25470-214">ICU et l’ancienne fonctionnalité Windows NLS sont mises à jour pour tenir compte de la façon dont les langues changent.</span><span class="sxs-lookup"><span data-stu-id="25470-214">Both ICU and the older Windows NLS facility are updated to account for how world languages change.</span></span> <span data-ttu-id="25470-215">Pour plus d’informations, consultez le billet de blog [évolution des données de paramètres régionaux (culture)](/archive/blogs/shawnste/locale-culture-data-churn).</span><span class="sxs-lookup"><span data-stu-id="25470-215">For more information, see the blog post [Locale (culture) data churn](/archive/blogs/shawnste/locale-culture-data-churn).</span></span> <span data-ttu-id="25470-216">Le comportement du comparateur *ordinal* ne changera jamais, car il effectue une recherche et une comparaison de bits exactes.</span><span class="sxs-lookup"><span data-stu-id="25470-216">The *Ordinal* comparer's behavior will never change since it performs exact bitwise searching and comparison.</span></span> <span data-ttu-id="25470-217">Toutefois, le comportement du comparateur *OrdinalIgnoreCase* peut changer à mesure que Unicode augmente pour englober davantage de jeux de caractères et corriger les omissions dans les données de casse existantes.</span><span class="sxs-lookup"><span data-stu-id="25470-217">However, the *OrdinalIgnoreCase* comparer's behavior may change as Unicode grows to encompass more character sets and corrects omissions in existing casing data.</span></span>
> - <span data-ttu-id="25470-218">Utilisation : les comparateurs `StringComparison.InvariantCulture` et `StringComparison.InvariantCultureIgnoreCase` sont des comparateurs linguistiques qui ne prennent pas en charge la culture.</span><span class="sxs-lookup"><span data-stu-id="25470-218">Usage: The comparers `StringComparison.InvariantCulture` and `StringComparison.InvariantCultureIgnoreCase` are linguistic comparers that are not culture-aware.</span></span> <span data-ttu-id="25470-219">Autrement dit, ces comparateurs comprennent des concepts tels que le caractère d’accentuation e ayant plusieurs représentations sous-jacentes possibles, et que toutes ces représentations doivent être considérées comme égales.</span><span class="sxs-lookup"><span data-stu-id="25470-219">That is, these comparers understand concepts such as the accented character é having multiple possible underlying representations, and that all such representations should be treated equal.</span></span> <span data-ttu-id="25470-220">Toutefois, les comparateurs linguistiques qui ne prennent pas en charge la culture ne contiendront pas de traitement spécial pour \<dz\> distinct de \<d\> ou \<z\> , comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="25470-220">But non-culture-aware linguistic comparers won't contain special handling for \<dz\> as distinct from \<d\> or \<z\>, as shown above.</span></span> <span data-ttu-id="25470-221">Elles ne sont pas non plus des caractères spéciaux tels que le Eszett allemand (ß).</span><span class="sxs-lookup"><span data-stu-id="25470-221">They also won't special-case characters like the German Eszett (ß).</span></span>

<span data-ttu-id="25470-222">.NET offre également le *mode de globalisation invariant*.</span><span class="sxs-lookup"><span data-stu-id="25470-222">.NET also offers the *invariant globalization mode*.</span></span> <span data-ttu-id="25470-223">Ce mode d’abonnement désactive les chemins de code qui traitent des routines de recherche linguistique et de comparaison.</span><span class="sxs-lookup"><span data-stu-id="25470-223">This opt-in mode disables code paths that deal with linguistic search and comparison routines.</span></span> <span data-ttu-id="25470-224">Dans ce mode, toutes les opérations utilisent des comportements *ordinal* ou *OrdinalIgnoreCase* , quel que `CultureInfo` soit `StringComparison` l’argument ou l’appelant fourni par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="25470-224">In this mode, all operations use *Ordinal* or *OrdinalIgnoreCase* behaviors, regardless of what `CultureInfo` or `StringComparison` argument the caller provides.</span></span> <span data-ttu-id="25470-225">Pour plus d’informations, consultez [options de configuration au moment de l’exécution pour la globalisation](../../core/run-time-config/globalization.md) et [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="25470-225">For more information, see [Run-time configuration options for globalization](../../core/run-time-config/globalization.md) and [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

<span data-ttu-id="25470-226">Pour plus d’informations, consultez [meilleures pratiques pour la comparaison de chaînes dans .net](best-practices-strings.md).</span><span class="sxs-lookup"><span data-stu-id="25470-226">For more information, see [Best practices for comparing strings in .NET](best-practices-strings.md).</span></span>

## <a name="security-implications"></a><span data-ttu-id="25470-227">Implications en matière de sécurité</span><span class="sxs-lookup"><span data-stu-id="25470-227">Security implications</span></span>

<span data-ttu-id="25470-228">Si votre application utilise une API affectée pour le filtrage, nous vous recommandons d’activer les règles d’analyse du code CA1307 et CA1309 pour faciliter la localisation des emplacements où une recherche linguistique peut avoir été utilisée par inadvertance à la place d’une recherche ordinale.</span><span class="sxs-lookup"><span data-stu-id="25470-228">If your app uses an affected API for filtering, we recommend enabling the CA1307 and CA1309 code analysis rules to help locate places where a linguistic search may have inadvertently been used instead of an ordinal search.</span></span> <span data-ttu-id="25470-229">Les modèles de code comme ceux-ci peuvent être vulnérables aux failles de sécurité.</span><span class="sxs-lookup"><span data-stu-id="25470-229">Code patterns like the following may be susceptible to security exploits.</span></span>

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

<span data-ttu-id="25470-230">Étant donné que la `string.IndexOf(string)` méthode utilise une recherche linguistique par défaut, il est possible qu’une chaîne contienne un littéral `'<'` ou un `'&'` caractère et `string.IndexOf(string)` que la routine retourne `-1` , indiquant que la sous-chaîne de recherche est introuvable.</span><span class="sxs-lookup"><span data-stu-id="25470-230">Because the `string.IndexOf(string)` method uses a linguistic search by default, it's possible for a string to contain a literal `'<'` or `'&'` character and for the `string.IndexOf(string)` routine to return `-1`, indicating that the search substring was not found.</span></span> <span data-ttu-id="25470-231">Les règles d’analyse du code CA1307 et CA1309 signalent ces sites d’appel et alertent le développeur qu’il y a un problème potentiel.</span><span class="sxs-lookup"><span data-stu-id="25470-231">Code analysis rules CA1307 and CA1309 flag such call sites and alert the developer that there's a potential problem.</span></span>

## <a name="default-search-and-comparison-types"></a><span data-ttu-id="25470-232">Types de comparaison et de recherche par défaut</span><span class="sxs-lookup"><span data-stu-id="25470-232">Default search and comparison types</span></span>

<span data-ttu-id="25470-233">Le tableau suivant répertorie les types de comparaison et de recherche par défaut pour diverses API de chaîne et de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="25470-233">The following table lists the default search and comparison types for various string and string-like APIs.</span></span> <span data-ttu-id="25470-234">Si l’appelant fournit un `CultureInfo` paramètre ou explicite `StringComparison` , ce paramètre sera respecté sur n’importe quelle valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="25470-234">If the caller provides an explicit `CultureInfo` or `StringComparison` parameter, that parameter will be honored over any default.</span></span>

| <span data-ttu-id="25470-235">API</span><span class="sxs-lookup"><span data-stu-id="25470-235">API</span></span> | <span data-ttu-id="25470-236">Comportement par défaut</span><span class="sxs-lookup"><span data-stu-id="25470-236">Default behavior</span></span> | <span data-ttu-id="25470-237">Notes</span><span class="sxs-lookup"><span data-stu-id="25470-237">Remarks</span></span> |
|---|---|---|
| `string.Compare` | <span data-ttu-id="25470-238">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-238">CurrentCulture</span></span> | |
| `string.CompareTo` | <span data-ttu-id="25470-239">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-239">CurrentCulture</span></span> | |
| `string.Contains` | <span data-ttu-id="25470-240">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-240">Ordinal</span></span> | |
| `string.EndsWith` | <span data-ttu-id="25470-241">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-241">Ordinal</span></span> | <span data-ttu-id="25470-242">(lorsque le premier paramètre est un `char` )</span><span class="sxs-lookup"><span data-stu-id="25470-242">(when the first parameter is a `char`)</span></span> |
| `string.EndsWith` | <span data-ttu-id="25470-243">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-243">CurrentCulture</span></span> | <span data-ttu-id="25470-244">(lorsque le premier paramètre est un `string` )</span><span class="sxs-lookup"><span data-stu-id="25470-244">(when the first parameter is a `string`)</span></span> |
| `string.Equals` | <span data-ttu-id="25470-245">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-245">Ordinal</span></span> | |
| `string.GetHashCode` | <span data-ttu-id="25470-246">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-246">Ordinal</span></span> | |
| `string.IndexOf` | <span data-ttu-id="25470-247">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-247">Ordinal</span></span> | <span data-ttu-id="25470-248">(lorsque le premier paramètre est un `char` )</span><span class="sxs-lookup"><span data-stu-id="25470-248">(when the first parameter is a `char`)</span></span> |
| `string.IndexOf` | <span data-ttu-id="25470-249">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-249">CurrentCulture</span></span> | <span data-ttu-id="25470-250">(lorsque le premier paramètre est un `string` )</span><span class="sxs-lookup"><span data-stu-id="25470-250">(when the first parameter is a `string`)</span></span> |
| `string.IndexOfAny` | <span data-ttu-id="25470-251">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-251">Ordinal</span></span> | |
| `string.LastIndexOf` | <span data-ttu-id="25470-252">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-252">Ordinal</span></span> | <span data-ttu-id="25470-253">(lorsque le premier paramètre est un `char` )</span><span class="sxs-lookup"><span data-stu-id="25470-253">(when the first parameter is a `char`)</span></span> |
| `string.LastIndexOf` | <span data-ttu-id="25470-254">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-254">CurrentCulture</span></span> | <span data-ttu-id="25470-255">(lorsque le premier paramètre est un `string` )</span><span class="sxs-lookup"><span data-stu-id="25470-255">(when the first parameter is a `string`)</span></span> |
| `string.LastIndexOfAny` | <span data-ttu-id="25470-256">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-256">Ordinal</span></span> | |
| `string.Replace` | <span data-ttu-id="25470-257">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-257">Ordinal</span></span> | |
| `string.Split` | <span data-ttu-id="25470-258">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-258">Ordinal</span></span> | |
| `string.StartsWith` | <span data-ttu-id="25470-259">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-259">Ordinal</span></span> | <span data-ttu-id="25470-260">(lorsque le premier paramètre est un `char` )</span><span class="sxs-lookup"><span data-stu-id="25470-260">(when the first parameter is a `char`)</span></span> |
| `string.StartsWith` | <span data-ttu-id="25470-261">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-261">CurrentCulture</span></span> | <span data-ttu-id="25470-262">(lorsque le premier paramètre est un `string` )</span><span class="sxs-lookup"><span data-stu-id="25470-262">(when the first parameter is a `string`)</span></span> |
| `string.ToLower` | <span data-ttu-id="25470-263">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-263">CurrentCulture</span></span> | |
| `string.ToLowerInvariant` | <span data-ttu-id="25470-264">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="25470-264">InvariantCulture</span></span> | |
| `string.ToUpper` | <span data-ttu-id="25470-265">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-265">CurrentCulture</span></span> | |
| `string.ToUpperInvariant` | <span data-ttu-id="25470-266">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="25470-266">InvariantCulture</span></span> | |
| `string.Trim` | <span data-ttu-id="25470-267">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-267">Ordinal</span></span> | |
| `string.TrimEnd` | <span data-ttu-id="25470-268">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-268">Ordinal</span></span> | |
| `string.TrimStart` | <span data-ttu-id="25470-269">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-269">Ordinal</span></span> | |
| `string == string` | <span data-ttu-id="25470-270">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-270">Ordinal</span></span> | |
| `string != string` | <span data-ttu-id="25470-271">Ordinal</span><span class="sxs-lookup"><span data-stu-id="25470-271">Ordinal</span></span> | |

<span data-ttu-id="25470-272">Contrairement aux `string` API, toutes les `MemoryExtensions` API effectuent des recherches *ordinales* et des comparaisons par défaut, avec les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="25470-272">Unlike `string` APIs, all `MemoryExtensions` APIs perform *Ordinal* searches and comparisons by default, with the following exceptions.</span></span>

| <span data-ttu-id="25470-273">API</span><span class="sxs-lookup"><span data-stu-id="25470-273">API</span></span> | <span data-ttu-id="25470-274">Comportement par défaut</span><span class="sxs-lookup"><span data-stu-id="25470-274">Default behavior</span></span> | <span data-ttu-id="25470-275">Notes</span><span class="sxs-lookup"><span data-stu-id="25470-275">Remarks</span></span> |
|---|---|---|
| `MemoryExtensions.ToLower` | <span data-ttu-id="25470-276">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-276">CurrentCulture</span></span> | <span data-ttu-id="25470-277">(lorsqu’un argument null est passé `CultureInfo` )</span><span class="sxs-lookup"><span data-stu-id="25470-277">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToLowerInvariant` | <span data-ttu-id="25470-278">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="25470-278">InvariantCulture</span></span> | |
| `MemoryExtensions.ToUpper` | <span data-ttu-id="25470-279">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="25470-279">CurrentCulture</span></span> | <span data-ttu-id="25470-280">(lorsqu’un argument null est passé `CultureInfo` )</span><span class="sxs-lookup"><span data-stu-id="25470-280">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToUpperInvariant` | <span data-ttu-id="25470-281">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="25470-281">InvariantCulture</span></span> | |

<span data-ttu-id="25470-282">Par conséquent, lors de la conversion de code de consommation `string` en consommation `ReadOnlySpan<char>` , des changements de comportement peuvent être introduits par inadvertance.</span><span class="sxs-lookup"><span data-stu-id="25470-282">A consequence is that when converting code from consuming `string` to consuming `ReadOnlySpan<char>`, behavioral changes may be introduced inadvertently.</span></span> <span data-ttu-id="25470-283">Voici un exemple de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="25470-283">An example of this follows.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

<span data-ttu-id="25470-284">Pour résoudre ce cas, il est recommandé de passer un `StringComparison` paramètre explicite à ces API.</span><span class="sxs-lookup"><span data-stu-id="25470-284">The recommended way to address this is to pass an explicit `StringComparison` parameter to these APIs.</span></span> <span data-ttu-id="25470-285">Les règles d’analyse du code CA1307 et CA1309 peuvent vous aider.</span><span class="sxs-lookup"><span data-stu-id="25470-285">The code analysis rules CA1307 and CA1309 can assist with this.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a><span data-ttu-id="25470-286">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25470-286">See also</span></span>

- [<span data-ttu-id="25470-287">Modifications avec rupture de la globalisation</span><span class="sxs-lookup"><span data-stu-id="25470-287">Globalization breaking changes</span></span>](../../core/compatibility/globalization.md)
- [<span data-ttu-id="25470-288">Meilleures pratiques pour la comparaison de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="25470-288">Best practices for comparing strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="25470-289">Comment comparer des chaînes en C#</span><span class="sxs-lookup"><span data-stu-id="25470-289">How to compare strings in C#</span></span>](../../csharp/how-to/compare-strings.md)
- [<span data-ttu-id="25470-290">Globalisation et ICU .NET</span><span class="sxs-lookup"><span data-stu-id="25470-290">.NET globalization and ICU</span></span>](../globalization-localization/globalization-icu.md)
- [<span data-ttu-id="25470-291">Opérations de chaînes ordinales et dépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="25470-291">Ordinal vs. culture-sensitive string operations</span></span>](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [<span data-ttu-id="25470-292">Vue d’ensemble de l’analyse du code source .NET</span><span class="sxs-lookup"><span data-stu-id="25470-292">Overview of .NET source code analysis</span></span>](../../fundamentals/code-analysis/overview.md)
