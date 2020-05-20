---
ms.openlocfilehash: c0c1c9c9d8e3aeb6f689f754d09b50b208b54112
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702317"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="e2eaa-101">StringInfo et TextElementEnumerator sont désormais conformes à UAX29</span><span class="sxs-lookup"><span data-stu-id="e2eaa-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="e2eaa-102">Avant cette modification, <xref:System.Globalization.StringInfo?displayProperty=fullName> et <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> n’a pas correctement géré tous les clusters graphèmes.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="e2eaa-103">Certains graphemes étaient répartis dans leurs composants constitutifs au lieu d’être maintenus ensemble.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="e2eaa-104">Maintenant, <xref:System.Globalization.StringInfo> et <xref:System.Globalization.TextElementEnumerator> traitez les clusters graphèmes en fonction de la dernière version de la norme Unicode.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="e2eaa-105">En outre, la <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> méthode, qui inverse les caractères d’une chaîne dans Visual Basic, est désormais également conforme à la norme Unicode pour les clusters graphèmes.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e2eaa-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e2eaa-106">Change description</span></span>

<span data-ttu-id="e2eaa-107">Un [cluster graphèmes](https://www.unicode.org/glossary/#extended_grapheme_cluster) [graphèmes](https://www.unicode.org/glossary/#grapheme) ou étendu est un caractère identifié par un utilisateur unique qui peut être composé de plusieurs points de code Unicode.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="e2eaa-108">Par exemple, la chaîne contenant le caractère thaï « Kam » ( :::no-loc text="กำ"::: ) se compose des deux caractères suivants :</span><span class="sxs-lookup"><span data-stu-id="e2eaa-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="e2eaa-109">:::no-loc text="ก":::(= ' \u0e01 ') CARACTÈRE THAÏ KO KAI</span><span class="sxs-lookup"><span data-stu-id="e2eaa-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="e2eaa-110">:::no-loc text=" ำ":::(= ' \u0e33 ') CARACTÈRE THAÏ SARA AM</span><span class="sxs-lookup"><span data-stu-id="e2eaa-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="e2eaa-111">Lorsqu’il est affiché à l’utilisateur, le système d’exploitation combine les deux caractères pour former le seul caractère d’affichage (ou graphèmes) « Kam » ou :::no-loc text="กำ"::: .</span><span class="sxs-lookup"><span data-stu-id="e2eaa-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="e2eaa-112">L’Emoji peut également être constitué de plusieurs caractères combinés pour l’affichage de la même façon.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="e2eaa-113">La documentation .NET utilise parfois le terme « élément de texte » pour faire référence à un graphèmes.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="e2eaa-114">Les <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> classes et inspectent les chaînes et retournent des informations sur les graphemes qu’elles contiennent.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="e2eaa-115">Dans .NET Framework (toutes les versions) et .NET Core 3. x et les versions antérieures, ces deux classes utilisent une logique personnalisée qui gère certaines classes d’association, mais n’est pas entièrement conforme à la [norme Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="e2eaa-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="e2eaa-116">Par exemple, les <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> classes et fractionnent de manière incorrecte le caractère thaï unique « Kam » en ses composants constitutifs au lieu de les conserver ensemble.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="e2eaa-117">Ces classes divisent de manière incorrecte le caractère Emoji « 🤷🏽 ♀️ » en quatre clusters (personne shrugging, modificateur de tonalité de la peau, modificateur de sexe et combinateur invisible) au lieu de les conserver ensemble en tant que cluster graphèmes unique.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="e2eaa-118">À compter de .NET 5, <xref:System.Globalization.StringInfo> les <xref:System.Globalization.TextElementEnumerator> classes et implémentent la norme Unicode telle que définie par la [norme Unicode annexe \# 29, Rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="e2eaa-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="e2eaa-119">En particulier, elles retournent désormais des [clusters graphèmes étendus](https://www.unicode.org/glossary/#extended_grapheme_cluster) pour toutes les classes de combinaison.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="e2eaa-120">Prenons le code C# suivant :</span><span class="sxs-lookup"><span data-stu-id="e2eaa-120">Consider the following C# code:</span></span>

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

<span data-ttu-id="e2eaa-121">Dans .NET Framework et .NET Core 3. x et les versions antérieures, les graphemes sont fractionnés et la sortie de la console est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e2eaa-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="e2eaa-122">Dans .NET 5 et versions ultérieures, les graphemes sont conservés ensemble, et la sortie de la console est la suivante :</span><span class="sxs-lookup"><span data-stu-id="e2eaa-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="e2eaa-123">En outre, à compter de .NET 5, la <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> méthode, qui inverse les caractères d’une chaîne dans Visual Basic, est désormais également conforme à la norme Unicode pour les clusters graphèmes.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="e2eaa-124">Ces modifications font partie d’un ensemble plus étendu d’améliorations Unicode et UTF-8 dans .NET, y compris une API d’énumération de cluster graphèmes étendue pour compléter les API d’énumération de valeurs scalaires Unicode qui ont été introduites avec le <xref:System.Text.Rune?displayProperty=fullName> type dans .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e2eaa-125">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e2eaa-125">Version introduced</span></span>

<span data-ttu-id="e2eaa-126">.NET 5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="e2eaa-126">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e2eaa-127">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e2eaa-127">Recommended action</span></span>

<span data-ttu-id="e2eaa-128">Aucune action de votre part n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-128">You don't need to take any action.</span></span> <span data-ttu-id="e2eaa-129">Vos applications se comporteront automatiquement d’une manière plus conforme aux normes dans un large éventail de scénarios liés à la globalisation.</span><span class="sxs-lookup"><span data-stu-id="e2eaa-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

#### <a name="category"></a><span data-ttu-id="e2eaa-130">Category</span><span class="sxs-lookup"><span data-stu-id="e2eaa-130">Category</span></span>

<span data-ttu-id="e2eaa-131">Globalisation</span><span class="sxs-lookup"><span data-stu-id="e2eaa-131">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2eaa-132">API affectées</span><span class="sxs-lookup"><span data-stu-id="e2eaa-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
