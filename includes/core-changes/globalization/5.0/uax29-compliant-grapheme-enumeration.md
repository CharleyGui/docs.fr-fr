---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888166"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="35c90-101">StringInfo et TextElementEnumerator sont maintenant conformes à la</span><span class="sxs-lookup"><span data-stu-id="35c90-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="35c90-102">Avant ce <xref:System.Globalization.StringInfo?displayProperty=fullName> changement, <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> et n’a pas correctement gérer tous les clusters de grapheme.</span><span class="sxs-lookup"><span data-stu-id="35c90-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="35c90-103">Certains graphemes ont été divisés en leurs composants constitutifs au lieu d’être maintenus ensemble.</span><span class="sxs-lookup"><span data-stu-id="35c90-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="35c90-104">Maintenant, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> et les clusters de grapheme de processus selon la dernière version de la norme Unicode.</span><span class="sxs-lookup"><span data-stu-id="35c90-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="35c90-105">En outre, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> la méthode, qui inverse les caractères dans une chaîne dans Visual Basic, suit maintenant également la norme Unicode pour les clusters de grapheme.</span><span class="sxs-lookup"><span data-stu-id="35c90-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="35c90-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="35c90-106">Change description</span></span>

<span data-ttu-id="35c90-107">Un [graphème](https://www.unicode.org/glossary/#grapheme) ou [un cluster de grapheme étendu](https://www.unicode.org/glossary/#extended_grapheme_cluster) est un seul personnage perçu par l’utilisateur qui peut être composé de plusieurs points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="35c90-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="35c90-108">Par exemple, la chaîne contenant le:::no-loc text="กำ":::caractère thaïlandais "kam" ( ) se compose des deux personnages suivants:</span><span class="sxs-lookup"><span data-stu-id="35c90-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="35c90-109">:::no-loc text="ก":::(U0e01)) CARACTÈRE THAÏLANDAIS KO KAI</span><span class="sxs-lookup"><span data-stu-id="35c90-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="35c90-110">:::no-loc text=" ำ":::(u0e33') CARACTÈRE THAÏLANDAIS SARA AM</span><span class="sxs-lookup"><span data-stu-id="35c90-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="35c90-111">Lorsqu’il est affiché à l’utilisateur, le système d’exploitation combine les deux :::no-loc text="กำ":::caractères pour former le caractère d’affichage unique (ou grapheme) "kam" ou .</span><span class="sxs-lookup"><span data-stu-id="35c90-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="35c90-112">Emoji peut également se composer de plusieurs caractères qui sont combinés pour l’affichage d’une manière similaire.</span><span class="sxs-lookup"><span data-stu-id="35c90-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="35c90-113">La documentation .NET utilise parfois le terme « élément texte » lorsqu’il s’agit d’un grapheme.</span><span class="sxs-lookup"><span data-stu-id="35c90-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="35c90-114">Les <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> chaînes et les classes inspectent les chaînes et renvoient des informations sur les graphemes qu’elles contiennent.</span><span class="sxs-lookup"><span data-stu-id="35c90-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="35c90-115">Dans .NET Framework (toutes versions) et .NET Core 3.x et plus tôt, ces deux classes utilisent une logique personnalisée qui gère certaines classes combinées, mais ne se conforme pas entièrement à la [norme Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="35c90-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="35c90-116">Par exemple, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> le caractère thaïlandais unique "kam" a divisé à tort le caractère thaïlandais unique "kam" dans ses composants constitutifs au lieu de les garder ensemble.</span><span class="sxs-lookup"><span data-stu-id="35c90-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="35c90-117">Ces classes divisent également à tort le caractère emoji "🤷🏽 ♀️" en quatre grappes (personne haussant les épaules, modificateur de teint, modificateur de genre, et un combine invisible) au lieu de les garder ensemble comme un seul cluster de grapheme.</span><span class="sxs-lookup"><span data-stu-id="35c90-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="35c90-118">En commençant par .NET <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> 5, les classes et les classes implémentent la norme Unicode telle que définie par [Unicode Standard Annexe \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="35c90-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="35c90-119">En particulier, ils retournent maintenant [des clusters de grapheme étendus](https://www.unicode.org/glossary/#extended_grapheme_cluster) pour toutes les classes combinant.</span><span class="sxs-lookup"><span data-stu-id="35c90-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="35c90-120">Considérez le code C suivant :</span><span class="sxs-lookup"><span data-stu-id="35c90-120">Consider the following C# code:</span></span>

```cs
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

<span data-ttu-id="35c90-121">Dans .NET Framework et .NET Core 3.x et les versions antérieures, les graphemes sont divisés, et la sortie de la console est la suivante:</span><span class="sxs-lookup"><span data-stu-id="35c90-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

<span data-ttu-id="35c90-122">Dans .NET 5 et les versions ultérieures, les graphemes sont maintenus ensemble, et la sortie de la console est la suivante:</span><span class="sxs-lookup"><span data-stu-id="35c90-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="35c90-123">En outre, à partir de <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> .NET 5, la méthode, qui inverse les caractères dans une chaîne dans Visual Basic, suit maintenant également la norme Unicode pour les clusters de grapheme.</span><span class="sxs-lookup"><span data-stu-id="35c90-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="35c90-124">Ces changements font partie d’un ensemble plus large d’améliorations d’Unicode et UTF-8 dans .NET, y compris une API de recensement <xref:System.Text.Rune?displayProperty=fullName> de cluster de grapheme prolongée pour compléter les API d’énumération de valeur scalaire d’Unicode qui ont été introduites avec le type dans .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="35c90-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="35c90-125">Version introduite</span><span class="sxs-lookup"><span data-stu-id="35c90-125">Version introduced</span></span>

<span data-ttu-id="35c90-126">.NET 5.0 Aperçu 1</span><span class="sxs-lookup"><span data-stu-id="35c90-126">.NET 5.0 Preview 1</span></span>

### <a name="recommended-action"></a><span data-ttu-id="35c90-127">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="35c90-127">Recommended action</span></span>

<span data-ttu-id="35c90-128">Aucune action de votre part n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="35c90-128">You don't need to take any action.</span></span> <span data-ttu-id="35c90-129">Vos applications se comporteront automatiquement d’une manière plus conforme aux normes dans une variété de scénarios liés à la mondialisation.</span><span class="sxs-lookup"><span data-stu-id="35c90-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

### <a name="category"></a><span data-ttu-id="35c90-130">Category</span><span class="sxs-lookup"><span data-stu-id="35c90-130">Category</span></span>

<span data-ttu-id="35c90-131">Globalisation</span><span class="sxs-lookup"><span data-stu-id="35c90-131">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="35c90-132">API affectées</span><span class="sxs-lookup"><span data-stu-id="35c90-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
