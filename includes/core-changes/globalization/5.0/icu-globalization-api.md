---
ms.openlocfilehash: 02b5dc181abe384c1a5f47c042e475f67a0afe1c
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400802"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="5efcc-101">Les API de globalisation utilisent des bibliothèques ICU sur Windows</span><span class="sxs-lookup"><span data-stu-id="5efcc-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="5efcc-102">.NET 5,0 et les versions ultérieures utilisent des bibliothèques [ICU (International Components for Unicode)](http://site.icu-project.org/home) pour la globalisation lorsqu’elles s’exécutent sur Windows 10 mai 2019 Update ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5efcc-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5efcc-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="5efcc-103">Change description</span></span>

<span data-ttu-id="5efcc-104">Dans .NET Core 1,0-3,1 et .NET Framework 4 et versions ultérieures, les bibliothèques .NET utilisent les API [NLS (National Language Support)](/windows/win32/intl/national-language-support) pour la fonctionnalité de globalisation sur Windows.</span><span class="sxs-lookup"><span data-stu-id="5efcc-104">In .NET Core 1.0 - 3.1 and .NET Framework 4 and later, .NET libraries use [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality on Windows.</span></span> <span data-ttu-id="5efcc-105">Par exemple, les fonctions NLS ont été utilisées pour comparer des chaînes, obtenir des informations sur la culture et effectuer la casse des chaînes dans la culture appropriée.</span><span class="sxs-lookup"><span data-stu-id="5efcc-105">For example, NLS functions were used to compare strings, get culture information, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="5efcc-106">À compter de .NET 5,0, si une application s’exécute sur Windows 10 mai 2019 Update ou une version ultérieure, les bibliothèques .NET utilisent les API de globalisation [ICU](http://site.icu-project.org/home) , par défaut.</span><span class="sxs-lookup"><span data-stu-id="5efcc-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs, by default.</span></span>

> [!NOTE]
> <span data-ttu-id="5efcc-107">La mise à jour de Windows 10 mai 2019 et les versions ultérieures sont fournies avec la bibliothèque Native ICU.</span><span class="sxs-lookup"><span data-stu-id="5efcc-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="5efcc-108">Si le Runtime .NET ne peut pas charger ICU, il utilise NLS à la place.</span><span class="sxs-lookup"><span data-stu-id="5efcc-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

#### <a name="behavioral-differences"></a><span data-ttu-id="5efcc-109">Différences de comportement</span><span class="sxs-lookup"><span data-stu-id="5efcc-109">Behavioral differences</span></span>

<span data-ttu-id="5efcc-110">Vous pouvez voir les modifications apportées à votre application même si vous ne vous rendez pas compte que vous utilisez des fonctionnalités de globalisation.</span><span class="sxs-lookup"><span data-stu-id="5efcc-110">You might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="5efcc-111">Cette section répertorie quelques-unes des modifications comportementales que vous pouvez constater, mais il en existe d’autres.</span><span class="sxs-lookup"><span data-stu-id="5efcc-111">This section lists a couple of the behavioral changes you might see, but there are others too.</span></span>

##### <a name="stringindexof"></a><span data-ttu-id="5efcc-112">String.IndexOf</span><span class="sxs-lookup"><span data-stu-id="5efcc-112">String.IndexOf</span></span>

<span data-ttu-id="5efcc-113">Prenons le code suivant qui appelle <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> pour Rechercher l’index du caractère de saut de ligne dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5efcc-113">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="5efcc-114">Dans les versions précédentes de .NET sur Windows, l’extrait de code s’imprime `6` .</span><span class="sxs-lookup"><span data-stu-id="5efcc-114">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="5efcc-115">Dans .NET 5,0 et versions ultérieures sur Windows 19H1 et versions ultérieures, l’extrait de code s’imprime `-1` .</span><span class="sxs-lookup"><span data-stu-id="5efcc-115">In .NET 5.0 and later versions on Windows 19H1 and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="5efcc-116">Pour corriger ce code en effectuant une recherche ordinale au lieu d’une recherche dépendante de la culture, appelez la <xref:System.String.IndexOf(System.String,System.StringComparison)> surcharge et transmettez-la <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="5efcc-116">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="5efcc-117">Vous pouvez exécuter les règles [d’analyse du code CA1307 : spécifiez StringComparison pour plus de clarté](../../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) et [Ca1309 : utiliser StringComparison](../../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) avec la valeur ordinale pour rechercher ces sites d’appel dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5efcc-117">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="5efcc-118">Pour plus d’informations, consultez [changements de comportement lors de la comparaison de chaînes sur .net 5 +](../../../../docs/standard/base-types/string-comparison-net-5-plus.md).</span><span class="sxs-lookup"><span data-stu-id="5efcc-118">For more information, see [Behavior changes when comparing strings on .NET 5+](../../../../docs/standard/base-types/string-comparison-net-5-plus.md).</span></span>

##### <a name="currency-symbol"></a><span data-ttu-id="5efcc-119">Symbole monétaire</span><span class="sxs-lookup"><span data-stu-id="5efcc-119">Currency symbol</span></span>

<span data-ttu-id="5efcc-120">Considérez le code suivant qui met en forme une chaîne à l’aide du spécificateur de format monétaire `C` .</span><span class="sxs-lookup"><span data-stu-id="5efcc-120">Consider the following code that formats a string using the currency format specifier `C`.</span></span> <span data-ttu-id="5efcc-121">La culture du thread actuel est définie sur une culture qui comprend uniquement la langue et non le pays.</span><span class="sxs-lookup"><span data-stu-id="5efcc-121">The current thread's culture is set to a culture that includes only the language and not the country.</span></span>

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- <span data-ttu-id="5efcc-122">Dans les versions précédentes de .NET sur Windows, la valeur de texte est `"100,00 €"` .</span><span class="sxs-lookup"><span data-stu-id="5efcc-122">In previous versions of .NET on Windows, the value of text is `"100,00 €"`.</span></span>
- <span data-ttu-id="5efcc-123">Dans .NET 5,0 et versions ultérieures sur Windows 19H1 et versions ultérieures, la valeur de Text est `"100,00 ¤"` , qui utilise le symbole monétaire international au lieu de l’euro.</span><span class="sxs-lookup"><span data-stu-id="5efcc-123">In .NET 5.0 and later versions on Windows 19H1 and later versions, the value of text is `"100,00 ¤"`, which uses the international currency symbol instead of the euro.</span></span> <span data-ttu-id="5efcc-124">Dans ICU, la conception est qu’une devise est une propriété d’un pays ou d’une région, et non d’une langue.</span><span class="sxs-lookup"><span data-stu-id="5efcc-124">In ICU, the design is that a currency is a property of a country or region, not a language.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5efcc-125">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="5efcc-125">Reason for change</span></span>

<span data-ttu-id="5efcc-126">Cette modification a été introduite pour unifier. Comportement de la globalisation du réseau sur tous les systèmes d’exploitation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5efcc-126">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="5efcc-127">Il offre également la possibilité pour les applications de regrouper leurs propres bibliothèques de globalisation plutôt que de dépendre des bibliothèques intégrées du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="5efcc-127">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the operating system's built-in libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5efcc-128">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5efcc-128">Version introduced</span></span>

<span data-ttu-id="5efcc-129">.NET 5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="5efcc-129">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5efcc-130">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5efcc-130">Recommended action</span></span>

<span data-ttu-id="5efcc-131">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="5efcc-131">No action is required on the part of the developer.</span></span> <span data-ttu-id="5efcc-132">Toutefois, si vous souhaitez continuer à utiliser les API de globalisation NLS, vous pouvez définir un [commutateur au moment](../../../../docs/core/run-time-config/globalization.md#nls) de l’exécution pour revenir à ce comportement.</span><span class="sxs-lookup"><span data-stu-id="5efcc-132">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="5efcc-133">Pour plus d’informations sur les commutateurs disponibles, consultez l’article présentation de la [globalisation et de la bibliothèque .net](../../../../docs/standard/globalization-localization/globalization-icu.md) .</span><span class="sxs-lookup"><span data-stu-id="5efcc-133">For more information about the available switches, see the [.NET globalization and ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) article.</span></span>

#### <a name="category"></a><span data-ttu-id="5efcc-134">Category</span><span class="sxs-lookup"><span data-stu-id="5efcc-134">Category</span></span>

- <span data-ttu-id="5efcc-135">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="5efcc-135">Core .NET libraries</span></span>
- <span data-ttu-id="5efcc-136">Globalisation</span><span class="sxs-lookup"><span data-stu-id="5efcc-136">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5efcc-137">API affectées</span><span class="sxs-lookup"><span data-stu-id="5efcc-137">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="5efcc-138">La plupart des types dans l' <xref:System.Globalization?displayProperty=fullName> espace de noms</span><span class="sxs-lookup"><span data-stu-id="5efcc-138">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>
- <span data-ttu-id="5efcc-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (lors du tri d’un tableau de chaînes)</span><span class="sxs-lookup"><span data-stu-id="5efcc-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting an array of strings)</span></span>
- <span data-ttu-id="5efcc-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (lorsque les éléments de la liste sont des chaînes)</span><span class="sxs-lookup"><span data-stu-id="5efcc-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="5efcc-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (lorsque les clés sont des chaînes)</span><span class="sxs-lookup"><span data-stu-id="5efcc-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="5efcc-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (lorsque les clés sont des chaînes)</span><span class="sxs-lookup"><span data-stu-id="5efcc-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="5efcc-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (lorsque l’ensemble contient des chaînes)</span><span class="sxs-lookup"><span data-stu-id="5efcc-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

-->
