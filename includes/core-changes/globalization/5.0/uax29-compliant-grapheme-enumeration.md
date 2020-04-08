---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888166"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo et TextElementEnumerator sont maintenant conformes à la

Avant ce <xref:System.Globalization.StringInfo?displayProperty=fullName> changement, <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> et n’a pas correctement gérer tous les clusters de grapheme. Certains graphemes ont été divisés en leurs composants constitutifs au lieu d’être maintenus ensemble. Maintenant, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> et les clusters de grapheme de processus selon la dernière version de la norme Unicode.

En outre, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> la méthode, qui inverse les caractères dans une chaîne dans Visual Basic, suit maintenant également la norme Unicode pour les clusters de grapheme.

#### <a name="change-description"></a>Description de la modification

Un [graphème](https://www.unicode.org/glossary/#grapheme) ou [un cluster de grapheme étendu](https://www.unicode.org/glossary/#extended_grapheme_cluster) est un seul personnage perçu par l’utilisateur qui peut être composé de plusieurs points de code Unicode. Par exemple, la chaîne contenant le:::no-loc text="กำ":::caractère thaïlandais "kam" ( ) se compose des deux personnages suivants:

- :::no-loc text="ก":::(U0e01)) CARACTÈRE THAÏLANDAIS KO KAI
- :::no-loc text=" ำ":::(u0e33') CARACTÈRE THAÏLANDAIS SARA AM

Lorsqu’il est affiché à l’utilisateur, le système d’exploitation combine les deux :::no-loc text="กำ":::caractères pour former le caractère d’affichage unique (ou grapheme) "kam" ou . Emoji peut également se composer de plusieurs caractères qui sont combinés pour l’affichage d’une manière similaire.

> [!TIP]
> La documentation .NET utilise parfois le terme « élément texte » lorsqu’il s’agit d’un grapheme.

Les <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> chaînes et les classes inspectent les chaînes et renvoient des informations sur les graphemes qu’elles contiennent. Dans .NET Framework (toutes versions) et .NET Core 3.x et plus tôt, ces deux classes utilisent une logique personnalisée qui gère certaines classes combinées, mais ne se conforme pas entièrement à la [norme Unicode](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries). Par exemple, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> le caractère thaïlandais unique "kam" a divisé à tort le caractère thaïlandais unique "kam" dans ses composants constitutifs au lieu de les garder ensemble. Ces classes divisent également à tort le caractère emoji "🤷🏽 ♀️" en quatre grappes (personne haussant les épaules, modificateur de teint, modificateur de genre, et un combine invisible) au lieu de les garder ensemble comme un seul cluster de grapheme.

En commençant par .NET <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> 5, les classes et les classes implémentent la norme Unicode telle que définie par [Unicode Standard Annexe \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html). En particulier, ils retournent maintenant [des clusters de grapheme étendus](https://www.unicode.org/glossary/#extended_grapheme_cluster) pour toutes les classes combinant.

Considérez le code C suivant :

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

Dans .NET Framework et .NET Core 3.x et les versions antérieures, les graphemes sont divisés, et la sortie de la console est la suivante:

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

Dans .NET 5 et les versions ultérieures, les graphemes sont maintenus ensemble, et la sortie de la console est la suivante:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

En outre, à partir de <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> .NET 5, la méthode, qui inverse les caractères dans une chaîne dans Visual Basic, suit maintenant également la norme Unicode pour les clusters de grapheme.

Ces changements font partie d’un ensemble plus large d’améliorations d’Unicode et UTF-8 dans .NET, y compris une API de recensement <xref:System.Text.Rune?displayProperty=fullName> de cluster de grapheme prolongée pour compléter les API d’énumération de valeur scalaire d’Unicode qui ont été introduites avec le type dans .NET Core 3.0.

#### <a name="version-introduced"></a>Version introduite

.NET 5.0 Aperçu 1

### <a name="recommended-action"></a>Action recommandée

Aucune action de votre part n’est nécessaire. Vos applications se comporteront automatiquement d’une manière plus conforme aux normes dans une variété de scénarios liés à la mondialisation.

### <a name="category"></a>Category

Globalisation

### <a name="affected-apis"></a>API affectées

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
