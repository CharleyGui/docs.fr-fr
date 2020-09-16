---
ms.openlocfilehash: 70b71fc55f76514dd17e5b9ba0e76151a966eebb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539463"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo et TextElementEnumerator sont désormais conformes à UAX29

Avant cette modification, <xref:System.Globalization.StringInfo?displayProperty=fullName> et <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> n’a pas correctement géré tous les clusters graphèmes. Certains graphemes étaient répartis dans leurs composants constitutifs au lieu d’être maintenus ensemble. Maintenant, <xref:System.Globalization.StringInfo> et <xref:System.Globalization.TextElementEnumerator> traitez les clusters graphèmes en fonction de la dernière version de la norme Unicode.

En outre, la <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> méthode, qui inverse les caractères d’une chaîne dans Visual Basic, est désormais également conforme à la norme Unicode pour les clusters graphèmes.

#### <a name="change-description"></a>Description de la modification

Un [cluster graphèmes](https://www.unicode.org/glossary/#extended_grapheme_cluster) [graphèmes](https://www.unicode.org/glossary/#grapheme) ou étendu est un caractère identifié par un utilisateur unique qui peut être composé de plusieurs points de code Unicode. Par exemple, la chaîne contenant le caractère thaï « Kam » ( :::no-loc text="กำ"::: ) se compose des deux caractères suivants :

- :::no-loc text="ก"::: (= ' \u0e01 ') CARACTÈRE THAÏ KO KAI
- :::no-loc text=" ำ"::: (= ' \u0e33 ') CARACTÈRE THAÏ SARA AM

Lorsqu’il est affiché à l’utilisateur, le système d’exploitation combine les deux caractères pour former le seul caractère d’affichage (ou graphèmes) « Kam » ou :::no-loc text="กำ"::: . L’Emoji peut également être constitué de plusieurs caractères combinés pour l’affichage de la même façon.

> [!TIP]
> La documentation .NET utilise parfois le terme « élément de texte » pour faire référence à un graphèmes.

Les <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> classes et inspectent les chaînes et retournent des informations sur les graphemes qu’elles contiennent. Dans .NET Framework (toutes les versions) et .NET Core 3. x et les versions antérieures, ces deux classes utilisent une logique personnalisée qui gère certaines classes d’association, mais n’est pas entièrement conforme à la [norme Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries). Par exemple, les <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> classes et fractionnent de manière incorrecte le caractère thaï unique « Kam » en ses composants constitutifs au lieu de les conserver ensemble. Ces classes divisent de manière incorrecte le caractère Emoji « 🤷🏽 ♀️ » en quatre clusters (personne shrugging, modificateur de tonalité de la peau, modificateur de sexe et combinateur invisible) au lieu de les conserver ensemble en tant que cluster graphèmes unique.

À compter de .NET 5, <xref:System.Globalization.StringInfo> les <xref:System.Globalization.TextElementEnumerator> classes et implémentent la norme Unicode telle que définie par la [norme Unicode annexe \# 29, Rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html). En particulier, elles retournent désormais des [clusters graphèmes étendus](https://www.unicode.org/glossary/#extended_grapheme_cluster) pour toutes les classes de combinaison.

Prenons le code C# suivant :

```csharp
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

Dans .NET Framework et .NET Core 3. x et les versions antérieures, les graphemes sont fractionnés et la sortie de la console est la suivante :

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

Dans .NET 5 et versions ultérieures, les graphemes sont conservés ensemble, et la sortie de la console est la suivante :

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

En outre, à compter de .NET 5, la <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> méthode, qui inverse les caractères d’une chaîne dans Visual Basic, est désormais également conforme à la norme Unicode pour les clusters graphèmes.

Ces modifications font partie d’un ensemble plus étendu d’améliorations Unicode et UTF-8 dans .NET, y compris une API d’énumération de cluster graphèmes étendue pour compléter les API d’énumération de valeurs scalaires Unicode qui ont été introduites avec le <xref:System.Text.Rune?displayProperty=fullName> type dans .net Core 3,0.

#### <a name="version-introduced"></a>Version introduite

.NET 5,0 Preview 1

#### <a name="recommended-action"></a>Action recommandée

Aucune action de votre part n’est nécessaire. Vos applications se comporteront automatiquement d’une manière plus conforme aux normes dans un large éventail de scénarios liés à la globalisation.

#### <a name="category"></a>Category

Globalisation

#### <a name="affected-apis"></a>API affectées

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
