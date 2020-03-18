---
title: Langage des expressions régulières - Aide-mémoire
ms.date: 03/30/2017
ms.technology: dotnet-standard
f1_keywords:
- VS.RegularExpressionBuilder
helpviewer_keywords:
- regex cheat sheet
- parsing text with regular expressions, language elements
- searching with regular expressions, language elements
- pattern-matching with regular expressions, language elements
- regular expressions, language elements
- regular expressions [.NET Framework]
- cheat sheet
- .NET Framework regular expressions, language elements
ms.assetid: 930653a6-95d2-4697-9d5a-52d11bb6fd4c
ms.openlocfilehash: 8acf0886215c2d31f949e38401c4705ac9e2aef5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124310"
---
# <a name="regular-expression-language---quick-reference"></a>Langage des expressions régulières - Aide-mémoire

Une expression régulière est un modèle que le moteur des expressions régulières tente de faire correspondre dans le texte d’entrée. Un modèle se compose d’un ou de plusieurs littéraux de caractère, opérateurs ou constructions. Pour obtenir une brève présentation, consultez [Expressions régulières .NET](regular-expressions.md).

Chaque section dans cette référence rapide répertorie une catégorie particulière de caractères, d’opérateurs et de constructions que vous pouvez utiliser pour définir des expressions régulières.

Nous avons également fourni ces informations en deux formats que vous pouvez télécharger et imprimer pour une référence facile :

- [Télécharger au format Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Télécharger au format PDF (.pdf)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

## <a name="character-escapes"></a>Caractères d’échappement

La barre oblique inverse (\\) dans une expression régulière indique que le caractère qui le suit est un caractère spécial (comme indiqué dans le tableau suivant), ou qu’il doit être interprété littéralement. Pour plus d’informations, consultez [Caractères d’échappement](character-escapes-in-regular-expressions.md).

|Caractère d’échappement|Description|Modèle|Correspondances|
|-----------------------|-----------------|-------------|-------------|
|`\a`|Correspond à un caractère de cloche, \u0007.|`\a`|`"\u0007"` dans `"Error!" + '\u0007'`|
|`\b`|Dans une classe de caractères, correspond à un retour arrière, \u0008.|`[\b]{3,}`|`"\b\b\b\b"` dans `"\b\b\b\b"`|
|`\t`|Correspond à une tabulation, \u0009.|`(\w+)\t`|`"item1\t"`, `"item2\t"` dans `"item1\titem2\t"`|
|`\r`|Correspond à un retour chariot, \u000D. (`\r` n’est pas équivalent au caractère de saut de ligne, `\n`.)|`\r\n(\w+)`|`"\r\nThese"` dans `"\r\nThese are\ntwo lines."`|
|`\v`|Correspond à une tabulation verticale, \u000B.|`[\v]{2,}`|`"\v\v\v"` dans `"\v\v\v"`|
|`\f`|Correspond à un saut de page, \u000C.|`[\f]{2,}`|`"\f\f\f"` dans `"\f\f\f"`|
|`\n`|Correspond à une nouvelle ligne, \u000A.|`\r\n(\w+)`|`"\r\nThese"` dans `"\r\nThese are\ntwo lines."`|
|`\e`|Correspond à un caractère d’échappement, \u001B.|`\e`|`"\x001B"` dans `"\x001B"`|
|`\` *nnn*|Utilise la représentation octale pour spécifier un caractère (*nnn* se compose de deux ou trois chiffres).|`\w\040\w`|`"a b"`, `"c d"` dans `"a bc d"`|
|`\x` *nn*|Utilise une représentation hexadécimale pour spécifier un caractère (*nn* se compose de deux chiffres exactement).|`\w\x20\w`|`"a b"`, `"c d"` dans `"a bc d"`|
|`\c`*X X*<br /><br /> `\c`*x*|Correspond au caractère de contrôle ASCII spécifié par *X* ou *x*, où *X* ou *x* représente la lettre du caractère de contrôle.|`\cC`|`"\x0003"` dans `"\x0003"` (Ctrl-C)|
|`\u` *nnnn*|Correspond à un caractère Unicode en utilisant la représentation hexadécimale (quatre chiffres exactement, représentés par *nnnn*).|`\w\u0020\w`|`"a b"`, `"c d"` dans `"a bc d"`|
|`\`|Lorsque ce caractère d'échappement est suivi d'un caractère non identifié comme caractère d'échappement, correspond au caractère lui-même. Par exemple, `\*` est identique à `\x2A`et `\.` est identique à `\x2E`. Cela permet au moteur des expressions régulières de lever l’ambiguïté d’éléments de langage (tels que \* ou ?) et de caractères littéraux (représentés par `\*` ou `\?`).|`\d+[\+-x\*]\d+`|`"2+2"` et `"3*9"` dans `"(2+2) * 3*9"`|

## <a name="character-classes"></a>Classes de caractères

Une classe de caractères fait correspondre tout caractère d’un jeu de caractères. Les classes de caractères incluent les éléments de langage répertoriés dans le tableau suivant. Pour plus d’informations, voir [Catégories de personnages](character-classes-in-regular-expressions.md).

|Classe de caractères|Description|Modèle|Correspondances|
|---------------------|-----------------|-------------|-------------|
|`[`*character_group*`]`|Correspond à n’importe quel personnage dans *character_group*. Par défaut, la correspondance respecte la casse.|`[ae]`|`"a"` dans `"gray"`<br /><br /> `"a"`, `"e"` dans `"lane"`|
|`[^`*character_group*`]`|Négation : correspond à n'importe quel caractère unique qui ne se trouve pas dans *groupe_caractères*. Par défaut, les caractères de *groupe_caractères* respectent la casse.|`[^aei]`|`"r"`, `"g"`, `"n"` dans `"reign"`|
|`[` *premier* `-` *last* `]`|Plage de caractères : correspond à n'importe quel caractère unique dans la plage comprise entre *premier* et *dernier*.|`[A-Z]`|`"A"`, `"B"` dans `"AB123"`|
|`.`|Caractère générique : correspond à tout caractère à l'exception de \n.<br /><br /> Pour faire correspondre un caractère littéral « point » (. ou `\u002E`), vous devez le faire précéder du caractère d'échappement (`\.`).|`a.e`|`"ave"` dans `"nave"`<br /><br /> `"ate"` dans `"water"`|
|`\p{`*nom*`}`|Correspond à n’importe quel caractère unique de la catégorie générale Unicode ou du bloc nommé spécifié par *name*.|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|`"C"`, `"L"` dans `"City Lights"`<br /><br /> `"Д"`, `"Ж"` dans `"ДЖem"`|
|`\P{`*nom*`}`|Correspond à n'importe quel caractère unique qui ne se trouve pas dans la catégorie générale Unicode ou le bloc nommé spécifié par *name*.|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|`"i"`, `"t"`, `"y"` dans `"City"`<br /><br /> `"e"`, `"m"` dans `"ДЖem"`|
|`\w`|Correspond à n’importe quel caractère alphabétique.|`\w`|`"I"`, `"D"`, `"A"`, `"1"`, `"3"` dans `"ID A1.3"`|
|`\W`|Correspond à tout caractère autre qu’un caractère de mot.|`\W`|`" "`, `"."` dans `"ID A1.3"`|
|`\s`|Correspond à tout caractère espace blanc.|`\w\s`|`"D "` dans `"ID A1.3"`|
|`\S`|Correspond à tout caractère autre qu’un espace blanc.|`\s\S`|`" _"` dans `"int __ctr"`|
|`\d`|Correspond à n’importe quel chiffre décimal.|`\d`|`"4"` dans `"4 = IV"`|
|`\D`|Correspond à n’importe quel caractère autre qu’un chiffre décimal.|`\D`|`" "`, `"="`, `" "`, `"I"`, `"V"` dans `"4 = IV"`|

## <a name="anchors"></a>Ancres

Les ancres, ou assertions de largeur nulle atomiques, entraînent le succès ou l’échec d’une correspondance en fonction de la position actuelle dans la chaîne, mais elles n’entraînent pas l’avancement du moteur à travers la chaîne ou la consommation de caractères. Les métacaractères répertoriés dans le tableau suivant sont des ancres. Pour plus d’informations, consultez [Ancres](anchors-in-regular-expressions.md).

|Assertion|Description|Modèle|Correspondances|
|---------------|-----------------|-------------|-------------|
|`^`|Par défaut, la correspondance doit commencer au début de la chaîne ; en mode multiligne, elle doit commencer au début de la ligne.|`^\d{3}`|`"901"` dans `"901-333-"`|
|`$`|Par défaut, la correspondance doit se produire à la fin de la chaîne ou avant `\n` à la fin de la chaîne ; en mode multiligne, elle doit se produire avant la fin de la ligne ou avant `\n` à la fin de la ligne.|`-\d{3}$`|`"-333"` dans `"-901-333"`|
|`\A`|La correspondance doit se produire au début de la chaîne.|`\A\d{3}`|`"901"` dans `"901-333-"`|
|`\Z`|La correspondance doit se produire à la fin de la chaîne ou avant `\n` à la fin de la chaîne.|`-\d{3}\Z`|`"-333"` dans `"-901-333"`|
|`\z`|La correspondance doit se produire à la fin de la chaîne.|`-\d{3}\z`|`"-333"` dans `"-901-333"`|
|`\G`|La correspondance doit se produire à l’emplacement où la correspondance précédente s’est terminée.|`\G\(\d\)`|`"(1)"`, `"(3)"`, `"(5)"` dans `"(1)(3)(5)[7](9)"`|
|`\b`|La correspondance doit se produire sur une limite entre un caractère `\w` (alphanumérique) et un caractère `\W` (non alphanumériques).|`\b\w+\s\w+\b`|`"them theme"`, `"them them"` dans `"them theme them them"`|
|`\B`|La correspondance ne doit pas se produire sur une limite `\b`.|`\Bend\w*\b`|`"ends"`, `"ender"` dans `"end sends endure lender"`|

## <a name="grouping-constructs"></a>Constructions de regroupement

Les constructions de regroupement délimitent les sous-expressions d’une expression régulière et capturent généralement les sous-chaînes d’une chaîne d’entrée. Les constructions de regroupement incluent les éléments de langage répertoriés dans le tableau suivant. Pour plus d’informations, consultez [Constructions de regroupement](grouping-constructs-in-regular-expressions.md).

|Construction de regroupement|Description|Modèle|Correspondances|
|------------------------|-----------------|-------------|-------------|
|`(`*sous-expression*`)`|Capture la sous-expression mise en correspondance et lui assigne un nombre ordinal de base un.|`(\w)\1`|`"ee"` dans `"deep"`|
|`(?<` *name* `>` *sous-expression* `)`|Capture la sous-expression mise en correspondance dans un groupe nommé.|`(?<double>\w)\k<double>`|`"ee"` dans `"deep"`|
|`(?<` *nom1* `-` *nom2* `>` *sous-expression* `)`|Définit un équilibre de définition de groupe. Pour plus d’informations, consultez la section « Équilibre de définition de groupe » dans [Constructions de regroupement](grouping-constructs-in-regular-expressions.md).|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|`"((1-3)*(3-1))"` dans `"3+2^((1-3)*(3-1))"`|
|`(?:`*sous-expression*`)`|Définit un groupe sans capture.|`Write(?:Line)?`|`"WriteLine"` dans `"Console.WriteLine()"`<br /><br /> `"Write"` dans `"Console.Write(value)"`|
|`(?imnsx-imnsx:`*sous-expression*`)`|Active ou désactive les options spécifiées dans *sous-expression*. Pour plus d’informations, consultez [Options des expressions régulières](regular-expression-options.md).|`A\d{2}(?i:\w+)\b`|`"A12xl"`, `"A12XL"` dans `"A12xl A12XL a12xl"`|
|`(?=`*sous-expression*`)`|Assertion de préanalyse positive de largeur nulle.|`\w+(?=\.)`|`"is"`, `"ran"` et `"out"` dans `"He is. The dog ran. The sun is out."`|
|`(?!`*sous-expression*`)`|Assertion de préanalyse négative de largeur nulle.|`\b(?!un)\w+\b`|`"sure"`, `"used"` dans `"unsure sure unity used"`|
|`(?<=`*sous-expression*`)`|Assertion de postanalyse positive de largeur nulle.|`(?<=19)\d{2}\b`|`"99"`, `"50"`, `"05"` dans `"1851 1999 1950 1905 2003"`|
|`(?<!`*sous-expression*`)`|Assertion de postanalyse négative de largeur nulle.|`(?<!19)\d{2}\b`|`"51"`, `"03"` dans `"1851 1999 1950 1905 2003"`|
|`(?>`*sous-expression*`)`|Groupe atomique.|`[13579](?>A+B+)`|`"1ABB"`, `"3ABB"` et `"5AB"` dans `"1ABB 3ABBC 5AB 5AC"`|

## <a name="quantifiers"></a>Quantificateurs

Un quantificateur indique combien d’instances de l’élément précédent (qui peut être un caractère, un groupe ou une classe de caractères) doivent être présentes dans la chaîne d’entrée pour qu’il y ait correspondance. Les quantificateurs incluent les éléments de langage répertoriés dans le tableau suivant. Pour plus d’informations, consultez [Quantificateurs](quantifiers-in-regular-expressions.md).

|Quantificateur|Description|Modèle|Correspondances|
|----------------|-----------------|-------------|-------------|
|`*`|Correspond zéro, une ou plusieurs fois à l’élément précédent.|`\d*\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+`|Correspond une ou plusieurs fois à l’élément précédent.|`"be+"`|`"bee"` dans `"been"`, `"be"` dans `"bent"`|
|`?`|Correspond zéro ou une fois à l’élément précédent.|`"rai?n"`|`"ran"`, `"rain"`|
|`{`*n*`}`|Correspond à l’élément précédent exactement *n* fois.|`",\d{3}"`|`",043"` dans `"1,043.6"`, `",876"`, `",543"` et `",210"` dans `"9,876,543,210"`|
|`{`*n*`,}`|Correspond à l’élément précédent au moins *n* fois.|`"\d{2,}"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *m*`}`|Correspond à l'élément précédent au moins *n* fois, mais pas plus de *m* fois.|`"\d{3,5}"`|`"166"`, `"17668"`<br /><br /> `"19302"` dans `"193024"`|
|`*?`|Correspond zéro fois ou plus à l’élément précédent, mais le moins de fois possible.|`\d*?\.\d`|`".0"`, `"19.9"`, `"219.9"`|
|`+?`|Correspond une ou plusieurs fois à l’élément précédent, mais le moins de fois possible.|`"be+?"`|`"be"` dans `"been"`, `"be"` dans `"bent"`|
|`??`|Correspond zéro ou une fois à l’élément précédent, mais le moins de fois possible.|`"rai??n"`|`"ran"`, `"rain"`|
|`{`*n*`}?`|Correspond exactement *n* fois à l’élément précédent.|`",\d{3}?"`|`",043"` dans `"1,043.6"`, `",876"`, `",543"` et `",210"` dans `"9,876,543,210"`|
|`{`*n*`,}?`|Correspond au moins *n* fois à l’élément précédent, mais le moins de fois possible.|`"\d{2,}?"`|`"166"`, `"29"`, `"1930"`|
|`{`*n* `,` *m*`}?`|Correspond entre *n* et *m* fois à l'élément précédent, mais le moins de fois possible.|`"\d{3,5}?"`|`"166"`, `"17668"`<br /><br /> `"193"`, `"024"` dans `"193024"`|

## <a name="backreference-constructs"></a>Constructions de référence arrière

Une backreference permet qu’une sous-expression précédemment mise en correspondance soit ensuite identifiée dans la même expression régulière. Le tableau suivant répertorie les constructions de backreference prises en charge par les expressions régulières dans .NET. Pour plus d'informations, consultez [Backreference Constructs](backreference-constructs-in-regular-expressions.md).

|Construction de backreference|Description|Modèle|Correspondances|
|-----------------------------|-----------------|-------------|-------------|
|`\`*nombre*|Backreference. Correspond à la valeur d’une sous-expression numérotée.|`(\w)\1`|`"ee"` dans `"seek"`|
|`\k<`*nom*`>`|Backreference nommée. Correspond à la valeur d’une expression nommée.|`(?<char>\w)\k<char>`|`"ee"` dans `"seek"`|

## <a name="alternation-constructs"></a>Constructions d’alternative

Les constructions d’alternative modifient une expression régulière pour permettre la correspondance de type inclusif/exclusif. Ces constructions incluent les éléments de langage répertoriés dans le tableau suivant. Pour plus d’informations, consultez [Constructions d’alternative](alternation-constructs-in-regular-expressions.md).

|Construction d’alternative|Description|Modèle|Correspondances|
|---------------------------|-----------------|-------------|-------------|
|<code>&#124;</code>|Correspond à tout élément séparé par le caractère barre verticale (<code>&#124;</code>).|<code>th(e&#124;is&#124;at)</code>|`"the"`, `"this"` dans `"this is the day."`|
|`(?(`*expression* `)` *oui* <code>&#124;</code> *non*`)`|Correspond à *oui* si le modèle d’expression régulière indiqué par *expression* correspond ; sinon, correspond à *no* (facultatif). *expression* est interprétée comme une assertion de largeur nulle.|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|`"A10"`, `"910"` dans `"A10 C103 910"`|
|`(?(` *name* `)` *oui* <code>&#124;</code> *non* `)`|Correspond à *oui* si *nom*, un groupe de capture nommé ou numéroté, a une correspondance ; sinon, correspond à *non* (facultatif).|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|`"Dogs.jpg "`, `"\"Yiska playing.jpg\""` dans `"Dogs.jpg \"Yiska playing.jpg\""`|

## <a name="substitutions"></a>Substitutions

Les substitutions sont des éléments de langage d’expression régulière pris en charge dans les modèles de remplacement. Pour plus d’informations, consultez [Substitutions](substitutions-in-regular-expressions.md). Les métacaractères répertoriés dans le tableau suivant sont des assertions de largeur nulle atomiques.

|Caractère|Description|Modèle|Modèle de remplacement|Chaîne d’entrée|Chaîne de résultat|
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|
|`$`*nombre*|Remplace la sous-chaîne mise en correspondance par le groupe *nombre*.|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|`"one two"`|`"two one"`|
|`${`*nom*`}`|Remplace la sous-chaîne mise en correspondance par le groupe nommé *nom*.|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|`"one two"`|`"two one"`|
|`$$`|Remplace un "$" littéral.|`\b(\d+)\s?USD`|`$$$1`|`"103 USD"`|`"$103"`|
|`$&`|Remplace une copie de la totalité de la correspondance.|`\$?\d*\.?\d+`|`**$&**`|`"$1.30"`|`"**$1.30**"`|
|``$` ``|Remplace tout le texte de la chaîne d'entrée avant la correspondance.|`B+`|``$` ``|`"AABBCC"`|`"AAAACC"`|
|`$'`|Remplace tout le texte de la chaîne d’entrée après la correspondance.|`B+`|`$'`|`"AABBCC"`|`"AACCCC"`|
|`$+`|Remplace le dernier groupe qui a été capturé.|`B+(C+)`|`$+`|`"AABBCCDD"`|`"AACCDD"`|
|`$_`|Remplace la chaîne d’entrée entière.|`B+`|`$_`|`"AABBCC"`|`"AAAABBCCCC"`|

## <a name="regular-expression-options"></a>Options des expressions régulières

Vous pouvez définir des options qui contrôlent comment le moteur des expressions régulières interprète un modèle d’expression régulière. Bon nombre de ces options peuvent être spécifiées inline (dans le modèle d’expression régulière) ou sous la forme d’une ou de plusieurs constantes <xref:System.Text.RegularExpressions.RegexOptions>. Cette référence rapide répertorie uniquement les options inline. Pour plus d’informations sur les options inline et <xref:System.Text.RegularExpressions.RegexOptions>, consultez l’article [Options des expressions régulières](regular-expression-options.md).

Vous pouvez spécifier une option inline de deux façons :

- À l’aide d’une [construction diverse](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`, où un signe moins (-) devant une option ou un jeu d’options désactive ces options. Par exemple, `(?i-mn)` active la correspondance qui ne respecte pas la casse (`i`), désactive le mode multiligne (`m`) et désactive les captures de groupe sans nom (`n`). L’option s’applique au modèle d’expression régulière depuis le point au niveau duquel l’option est définie et est effective jusqu’à la fin du modèle ou jusqu’au point au niveau duquel une autre construction inverse l’option.
- En utilisant la*sous-exposition*`)` [de construction de](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`groupement , qui définit les options pour le groupe spécifié seulement.

Le moteur d’expression régulière .NET prend en charge les options en ligne suivantes :

|Option|Description|Modèle|Correspondances|
|------------|-----------------|-------------|-------------|
|`i`|Utilise la correspondance qui ne respecte pas la casse.|`\b(?i)a(?-i)a\w+\b`|`"aardvark"`, `"aaaAuto"` dans `"aardvark AAAuto aaaAuto Adam breakfast"`|
|`m`|Utilise le mode multiligne. `^` et `$` correspondent au début et à la fin d’une ligne, au lieu du début et de la fin d’une chaîne.|Pour obtenir un exemple, consultez la section « Mode multiligne » dans [Options des expressions régulières](regular-expression-options.md).||
|`n`|Ne capture aucun groupe sans nom.|Pour obtenir un exemple, consultez la section « Captures explicites uniquement » dans [Options des expressions régulières](regular-expression-options.md).||
|`s`|Utilise le mode à ligne simple.|Pour obtenir un exemple, consultez la section « Mode à ligne simple » dans [Options des expressions régulières](regular-expression-options.md).||
|`x`|Ignore l’espace blanc sans séquence d’échappement dans le modèle d’expression régulière.|`\b(?x) \d+ \s \w+`|`"1 aardvark"`, `"2 cats"` dans `"1 aardvark 2 cats IV centurions"`|

## <a name="miscellaneous-constructs"></a>Constructions diverses

Diverses constructions modifient un modèle d’expression régulière ou fournissent des informations le concernant. Le tableau suivant répertorie les diverses constructions prises en charge par .NET. Pour plus d'informations, consultez [Miscellaneous Constructs](miscellaneous-constructs-in-regular-expressions.md).

|Construction|Définition| Exemple|
|---------------|----------------|-------------|
|`(?imnsx-imnsx)`|Active ou désactive des options telles que le non-respect de la casse au milieu d’un modèle. Pour plus d’informations, consultez [Options des expressions régulières](regular-expression-options.md).|`\bA(?i)b\w+\b` correspond à `"ABA"`, `"Able"` dans `"ABA Able Act"`|
|`(?#`*commentaire*`)`|Commentaire inline. Le commentaire se termine à la première parenthèse fermante.|`\bA(?#Matches words starting with A)\w+\b`|
|`#` [to end of line]|Commentaire en mode X. Le commentaire commence au caractère `#` sans séquence d'échappement et se poursuit jusqu'à la fin de la ligne.|`(?x)\bA\w+\b#Matches words starting with A`|

## <a name="see-also"></a>Voir aussi

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Expressions régulières](regular-expressions.md)
- [Classes d’expressions régulières](the-regular-expression-object-model.md)
- [Exemples d'expressions régulières](regular-expression-examples.md)
- [Expressions régulières - Aide-mémoire (téléchargement au format Word)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
- [Expressions régulières - Aide-mémoire (téléchargement au format PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
