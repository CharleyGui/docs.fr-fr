---
title: Changements de comportement lors de la comparaison de chaînes sur .NET 5 +
description: En savoir plus sur les changements de comportement de comparaison de chaînes dans .NET 5 et versions ultérieures sur Windows.
ms.date: 11/04/2020
ms.openlocfilehash: fa1a1d12f45e5b41877a674d7b8747bb2b2f9658
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734229"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a>Changements de comportement lors de la comparaison de chaînes sur .NET 5 +

.NET 5,0 introduit un changement de comportement au moment de l’exécution où les API de globalisation [utilisent désormais ICU par défaut](../../core/compatibility/globalization/5.0/icu-globalization-api.md) sur toutes les plateformes prises en charge. Il s’agit d’une nouveauté par rapport aux versions antérieures de .NET Core et de .NET Framework, qui utilisent la fonctionnalité NLS (National Language Support) du système d’exploitation lors de l’exécution sous Windows. Pour plus d’informations sur ces modifications, y compris les commutateurs de compatibilité qui peuvent rétablir le changement de comportement, consultez [globalisation et ICU .net](../globalization-localization/globalization-icu.md).

## <a name="reason-for-change"></a>Motif de modification

Cette modification a été introduite pour unifier. Comportement de la globalisation du réseau sur tous les systèmes d’exploitation pris en charge. Il offre également la possibilité pour les applications de regrouper leurs propres bibliothèques de globalisation plutôt que de dépendre des bibliothèques intégrées du système d’exploitation. Pour plus d’informations, consultez [la notification de modification avec rupture](../../core/compatibility/globalization/5.0/icu-globalization-api.md).

## <a name="behavioral-differences"></a>Différences de comportement

Si vous utilisez des fonctions comme si vous `string.IndexOf(string)` n’appelez pas la surcharge qui prend un <xref:System.StringComparison> argument, vous pouvez envisager d’effectuer une recherche *ordinale* , mais au lieu de cela, vous prenez par inadvertance une dépendance vis-à-vis du comportement propre à la culture. Dans la mesure où NLS et ICU implémentent une logique différente dans leurs comparateurs linguistiques, les résultats de méthodes comme `string.IndexOf(string)` peuvent retourner des valeurs inattendues.

Cela peut se manifester même à des endroits où vous n’êtes pas toujours en mesure d’activer les fonctionnalités de globalisation. Par exemple, le code suivant peut produire une réponse différente selon le runtime actuel.

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

## <a name="guard-against-unexpected-behavior"></a>Protection contre les comportements inattendus

Cette section fournit deux options pour traiter les changements de comportement inattendus dans .NET 5,0.

### <a name="enable-code-analyzers"></a>Activer les analyseurs de code

Les [analyseurs de code](../../fundamentals/code-analysis/overview.md) peuvent détecter les sites d’appel éventuellement bogués. Pour vous protéger contre les comportements étonnants, nous vous recommandons d’installer [le package NuGet __Microsoft. CodeAnalysis. FxCopAnalyzers__](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) dans votre projet. Ce package comprend les règles d’analyse du code [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) et [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), qui permettent d’identifier le code susceptible d’utiliser par inadvertance un comparateur linguistique lorsqu’un comparateur ordinal était probablement prévu.

Par exemple :

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1307.
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

De même, lors de l’instanciation d’une collection triée de chaînes ou du tri d’une collection de chaînes existante, spécifiez un comparateur explicite.

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

Pour plus d’informations sur ces règles d’analyseur de code, notamment le moment où il peut être approprié de supprimer ces règles dans votre propre base de code, consultez les articles suivants :

* [CA1307 : Spécifier StringComparison pour clarifier](../../fundamentals/code-analysis/quality-rules/ca1307.md)
* [CA1309 : Utiliser StringComparison avec la valeur Ordinal](../../fundamentals/code-analysis/quality-rules/ca1309.md)

### <a name="revert-back-to-nls-behaviors"></a>Revenir aux comportements NLS

Pour restaurer les applications .NET 5 à des comportements NLS plus anciens lors de l’exécution sous Windows, suivez les étapes de la section [globalisation et ICU de .net](../globalization-localization/globalization-icu.md). Ce commutateur de compatibilité à l’échelle de l’application doit être défini au niveau de l’application. Les bibliothèques individuelles ne peuvent pas accepter ou refuser ce comportement.

> [!TIP]
> Nous vous recommandons vivement d’activer les règles d’analyse du code [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) et [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) pour aider à améliorer l’hygiène du code et découvrir les bogues latentes existants. Pour plus d’informations, consultez [activer les analyseurs de code](#enable-code-analyzers).

## <a name="affected-apis"></a>API affectées

La plupart des applications .NET ne rencontrent pas de comportements inattendus en raison des modifications apportées à .NET 5,0. Toutefois, en raison du nombre d’API affectées et de la façon dont ces API sont les plus larges de l’écosystème .NET, vous devez être conscient du potentiel de .NET 5,0 pour introduire des comportements indésirables ou pour exposer des bogues latentes qui existent déjà dans votre application.

Les API affectées sont les suivantes :

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <xref:System.Globalization.TextInfo?displayProperty=fullName> (la plupart des membres)
- <xref:System.Globalization.CompareInfo?displayProperty=fullName> (la plupart des membres)
- <xref:System.Array.Sort%2A?displayProperty=fullName> (lors du tri de tableaux de chaînes)
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (lorsque les éléments de la liste sont des chaînes)
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (lorsque les clés sont des chaînes)
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (lorsque les clés sont des chaînes)
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (lorsque l’ensemble contient des chaînes)

> [!NOTE]
> Il ne s’agit pas d’une liste exhaustive des API affectées.

Toutes les API ci-dessus utilisent la recherche et la comparaison de chaînes *linguistiques* à l’aide de la [culture actuelle](xref:System.Threading.Thread.CurrentCulture)du thread, par défaut. Les différences entre la recherche *linguistique* et *ordinale* et la comparaison sont appelées dans la [recherche ordinale et la recherche et la comparaison linguistiques](#ordinal-vs-linguistic-search-and-comparison).

Étant donné que ICU implémente les comparaisons de chaînes linguistiques différemment de NLS, les applications Windows qui effectuent la mise à niveau vers .NET 5,0 à partir d’une version antérieure de .NET Core ou de .NET Framework et qui appellent une des API affectées peuvent remarquer que les API commencent à présenter des comportements différents.

### <a name="exceptions"></a>Exceptions

* Si une API accepte un `StringComparison` paramètre ou explicite `CultureInfo` , ce paramètre remplace le comportement par défaut de l’API.
* `System.String` les membres où le premier paramètre est de type `char` (par exemple, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType> ) utilisent la recherche ordinale, sauf si l’appelant passe un `StringComparison` argument explicite qui spécifie `CurrentCulture[IgnoreCase]` ou `InvariantCulture[IgnoreCase]` .

Pour une analyse plus détaillée du comportement par défaut de chaque <xref:System.String> API, consultez la section [types de comparaison et de recherche par défaut](#default-search-and-comparison-types) .

## <a name="ordinal-vs-linguistic-search-and-comparison"></a>Comparaison entre les comparaisons ordinale et linguistique

La recherche et la comparaison *ordinale* (également appelée *non linguistique*) décomposent une chaîne en `char` éléments individuels et effectuent une recherche de type char-by-char ou une comparaison. Par exemple, les chaînes `"dog"` et `"dog"` sont considérées comme *égales* sous un `Ordinal` comparateur, étant donné que les deux chaînes se composent exactement de la même séquence de caractères. Toutefois, `"dog"` et `"Dog"` sont considérés comme *n’étant pas égaux* sous un `Ordinal` comparateur, car ils ne se composent pas exactement de la même séquence de caractères. Autrement dit, le `'D'` point de code en majuscules `U+0044` se produit avant le `'d'` point de code en minuscules `U+0064` , ce qui entraîne un `"dog"` Tri avant `"Dog"` .

Un `OrdinalIgnoreCase` comparateur continue de fonctionner en fonction du caractère par caractère, mais il élimine les différences de casse lors de l’exécution de l’opération. Sous un `OrdinalIgnoreCase` comparateur, les paires de caractères `'d'` et `'D'` sont considérées comme *égales*, comme les paires de caractères `'á'` et `'Á'` . Toutefois, le caractère non accentué `'a'` *n’est pas* comparé au caractère accentué `'á'` .

Des exemples sont fournis dans le tableau suivant :

| Chaîne 1 | Chaîne 2 | `Ordinal` considèrent | `OrdinalIgnoreCase` considèrent |
|---|---|---|---|
| `"dog"` | `"dog"` | equal | equal |
| `"dog"` | `"Dog"` | différent de | equal |
| `"resume"` | `"Resume"` | différent de | equal |
| `"resume"` | `"résumé"` | différent de | différent de |

Unicode permet également aux chaînes d’avoir plusieurs représentations en mémoire différentes. Par exemple, un e-aigu (é) peut être représenté de deux manières :

* Caractère littéral unique `'é'` (également écrit comme `'\u00E9'` ).
* Caractère non accentué littéral `'e'` , suivi d’un caractère modificateur d’accentuation de combinaison `'\u0301'` .

Cela signifie que les _quatre_ chaînes suivantes sont toutes générées `"résumé"` lorsqu’elles sont affichées, même si leurs éléments constitutifs sont différents. Les chaînes utilisent une combinaison de caractères littéraux `'é'` ou de caractères non accentués littéraux `'e'` plus le modificateur d’accent de combinaison `'\u0301'` .

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

Dans un comparateur ordinal, aucune de ces chaînes n’est comparée les unes aux autres. Cela est dû au fait qu’ils contiennent tous des séquences de caractères sous-jacentes différentes, même si elles sont toutes affichées à l’écran.

Lors de l’exécution d’une `string.IndexOf(..., StringComparison.Ordinal)` opération, le runtime recherche une correspondance exacte de sous-chaînes. Les résultats sont les suivants.

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

Les routines de recherche ordinale et de comparaison ne sont jamais affectées par le paramètre de culture du thread actuel.

Les routines de recherche *linguistique* et de comparaison décomposent une chaîne en *éléments de classement* et effectuent des recherches ou des comparaisons sur ces éléments. Il n’y a pas nécessairement un mappage de 1:1 entre les caractères d’une chaîne et ses éléments de classement constitutifs. Par exemple, une chaîne de longueur 2 peut se composer d’un seul élément de classement. Lorsque deux chaînes sont comparées selon un mode de prise en charge linguistique, le comparateur vérifie si les deux éléments de classement des chaînes ont la même signification sémantique, même si les caractères littéraux de la chaîne sont différents.

Reprenons la chaîne `"résumé"` et ses quatre représentations différentes. Le tableau suivant présente chaque représentation décomposée en ses éléments de classement.

| String | En tant qu’éléments de classement |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

Un élément de classement correspond vaguement à ce que les lecteurs considèrent comme un caractère unique ou un cluster de caractères. Son concept est similaire à celui d’un [cluster graphèmes](character-encoding-introduction.md#grapheme-clusters) , mais il englobe un parapluie un peu plus grand.

Sous un comparateur linguistique, les correspondances exactes ne sont pas nécessaires. Les éléments de classement sont comparés en fonction de leur signification sémantique. Par exemple, un comparateur linguistique tsreat les sous-chaînes `"\u00E9"` et `"e\u0301"` comme égal, car il s’agit de la sémantique « un e minuscule avec un modificateur d’accent aigu ». Cela permet `IndexOf` à la méthode de correspondre à la sous-chaîne `"e\u0301"` dans une chaîne plus grande qui contient la sous-chaîne sémantiquement équivalente `"\u00E9"` , comme illustré dans l’exemple de code suivant.

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

Par conséquent, deux chaînes de longueurs différentes peuvent être considérées comme égales si une comparaison linguistique est utilisée. Les appelants doivent s’occuper de la logique à cas spécial qui traite la longueur des chaînes dans de tels scénarios.

Les routines de recherche et de comparaison *prenant en compte la culture* sont une forme spéciale de routines de recherche linguistique et de comparaison. Sous un comparateur dépendant de la culture, le concept d’élément de classement est étendu pour inclure des informations spécifiques à la culture spécifiée.

Par exemple, [dans l’alphabet hongrois](https://en.wikipedia.org/wiki/Hungarian_alphabet), lorsque les deux caractères \<dz\> apparaissent en arrière-plan, ils sont considérés comme des lettres uniques distinctes de \<d\> ou \<z\> . Cela signifie que lorsque \<dz\> est visible dans une chaîne, un comparateur prenant en charge la culture hongrois le traite comme un élément de classement unique.

| String | En tant qu’éléments de classement | Remarques |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | (à l’aide d’un comparateur linguistique standard) |
| `"endz"` | `"e" + "n" + "dz"` | (à l’aide d’un comparateur prenant en charge la culture hongrois) |

Lors de l’utilisation d’un comparateur prenant en charge la culture hongrois, cela signifie que la chaîne `"endz"` *ne* se termine pas par la sous-chaîne `"z"` , car < \dz \> et < \z \> sont considérés comme des éléments de classement ayant une signification sémantique différente.

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
> - Comportement : les comparateurs de langue et de culture peuvent subir des ajustements de comportement de temps à autre. ICU et l’ancienne fonctionnalité Windows NLS sont mises à jour pour tenir compte de la façon dont les langues changent. Pour plus d’informations, consultez le billet de blog [évolution des données de paramètres régionaux (culture)](/archive/blogs/shawnste/locale-culture-data-churn). Le comportement du comparateur *ordinal* ne changera jamais, car il effectue une recherche et une comparaison de bits exactes. Toutefois, le comportement du comparateur *OrdinalIgnoreCase* peut changer à mesure que Unicode augmente pour englober davantage de jeux de caractères et corriger les omissions dans les données de casse existantes.
> - Utilisation : les comparateurs `StringComparison.InvariantCulture` et `StringComparison.InvariantCultureIgnoreCase` sont des comparateurs linguistiques qui ne prennent pas en charge la culture. Autrement dit, ces comparateurs comprennent des concepts tels que le caractère d’accentuation e ayant plusieurs représentations sous-jacentes possibles, et que toutes ces représentations doivent être considérées comme égales. Toutefois, les comparateurs linguistiques qui ne prennent pas en charge la culture ne contiendront pas de traitement spécial pour \<dz\> distinct de \<d\> ou \<z\> , comme indiqué ci-dessus. Elles ne sont pas non plus des caractères spéciaux tels que le Eszett allemand (ß).

.NET offre également le *mode de globalisation invariant*. Ce mode d’abonnement désactive les chemins de code qui traitent des routines de recherche linguistique et de comparaison. Dans ce mode, toutes les opérations utilisent des comportements *ordinal* ou *OrdinalIgnoreCase* , quel que `CultureInfo` soit `StringComparison` l’argument ou l’appelant fourni par l’appelant. Pour plus d’informations, consultez [options de configuration au moment de l’exécution pour la globalisation](../../core/run-time-config/globalization.md) et [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

Pour plus d’informations, consultez [meilleures pratiques pour la comparaison de chaînes dans .net](best-practices-strings.md).

## <a name="security-implications"></a>Implications en matière de sécurité

Si votre application utilise une API affectée pour le filtrage, nous vous recommandons d’activer les règles d’analyse du code CA1307 et CA1309 pour faciliter la localisation des emplacements où une recherche linguistique peut avoir été utilisée par inadvertance à la place d’une recherche ordinale. Les modèles de code comme ceux-ci peuvent être vulnérables aux failles de sécurité.

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

Étant donné que la `string.IndexOf(string)` méthode utilise une recherche linguistique par défaut, il est possible qu’une chaîne contienne un littéral `'<'` ou un `'&'` caractère et `string.IndexOf(string)` que la routine retourne `-1` , indiquant que la sous-chaîne de recherche est introuvable. Les règles d’analyse du code CA1307 et CA1309 signalent ces sites d’appel et alertent le développeur qu’il y a un problème potentiel.

## <a name="default-search-and-comparison-types"></a>Types de comparaison et de recherche par défaut

Le tableau suivant répertorie les types de comparaison et de recherche par défaut pour diverses API de chaîne et de type chaîne. Si l’appelant fournit un `CultureInfo` paramètre ou explicite `StringComparison` , ce paramètre sera respecté sur n’importe quelle valeur par défaut.

| API | Comportement par défaut | Remarques |
|---|---|---|
| `string.Compare` | CurrentCulture | |
| `string.CompareTo` | CurrentCulture | |
| `string.Contains` | Ordinal | |
| `string.EndsWith` | Ordinal | (lorsque le premier paramètre est un `char` ) |
| `string.EndsWith` | CurrentCulture | (lorsque le premier paramètre est un `string` ) |
| `string.Equals` | Ordinal | |
| `string.GetHashCode` | Ordinal | |
| `string.IndexOf` | Ordinal | (lorsque le premier paramètre est un `char` ) |
| `string.IndexOf` | CurrentCulture | (lorsque le premier paramètre est un `string` ) |
| `string.IndexOfAny` | Ordinal | |
| `string.LastIndexOf` | Ordinal | (lorsque le premier paramètre est un `char` ) |
| `string.LastIndexOf` | CurrentCulture | (lorsque le premier paramètre est un `string` ) |
| `string.LastIndexOfAny` | Ordinal | |
| `string.Replace` | Ordinal | |
| `string.Split` | Ordinal | |
| `string.StartsWith` | Ordinal | (lorsque le premier paramètre est un `char` ) |
| `string.StartsWith` | CurrentCulture | (lorsque le premier paramètre est un `string` ) |
| `string.ToLower` | CurrentCulture | |
| `string.ToLowerInvariant` | InvariantCulture | |
| `string.ToUpper` | CurrentCulture | |
| `string.ToUpperInvariant` | InvariantCulture | |
| `string.Trim` | Ordinal | |
| `string.TrimEnd` | Ordinal | |
| `string.TrimStart` | Ordinal | |
| `string == string` | Ordinal | |
| `string != string` | Ordinal | |

Contrairement aux `string` API, toutes les `MemoryExtensions` API effectuent des recherches *ordinales* et des comparaisons par défaut, avec les exceptions suivantes.

| API | Comportement par défaut | Remarques |
|---|---|---|
| `MemoryExtensions.ToLower` | CurrentCulture | (lorsqu’un argument null est passé `CultureInfo` ) |
| `MemoryExtensions.ToLowerInvariant` | InvariantCulture | |
| `MemoryExtensions.ToUpper` | CurrentCulture | (lorsqu’un argument null est passé `CultureInfo` ) |
| `MemoryExtensions.ToUpperInvariant` | InvariantCulture | |

Par conséquent, lors de la conversion de code de consommation `string` en consommation `ReadOnlySpan<char>` , des changements de comportement peuvent être introduits par inadvertance. Voici un exemple de cette procédure.

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

Pour résoudre ce cas, il est recommandé de passer un `StringComparison` paramètre explicite à ces API. Les règles d’analyse du code CA1307 et CA1309 peuvent vous aider.

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a>Voir aussi

- [Modifications avec rupture de la globalisation](../../core/compatibility/globalization.md)
- [Meilleures pratiques pour la comparaison de chaînes dans .NET](best-practices-strings.md)
- [Comment comparer des chaînes en C#](../../csharp/how-to/compare-strings.md)
- [Globalisation et ICU .NET](../globalization-localization/globalization-icu.md)
- [Opérations de chaînes ordinales et dépendantes de la culture](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [Vue d’ensemble de l’analyse du code source .NET](../../fundamentals/code-analysis/overview.md)
