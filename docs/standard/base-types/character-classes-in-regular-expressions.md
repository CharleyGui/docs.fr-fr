---
title: Classes de caractères dans les expressions régulières .NET
description: Découvrez comment utiliser les classes de caractères pour représenter un jeu de caractères dans les expressions régulières .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
ms.openlocfilehash: 85107bf2234eda1705126e524acd5b35952094bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292096"
---
# <a name="character-classes-in-regular-expressions"></a>Classes de caractères dans les expressions régulières

Une classe de caractères définit un jeu de caractères, chacun d'entre eux pouvant apparaître dans une chaîne d'entrée pour aboutir à une correspondance. Le langage d’expression régulière dans .NET prend en charge les classes de caractères suivantes :  
  
- Groupes de caractères positifs. Un caractère de la chaîne d'entrée doit correspondre à l'un des jeux de caractères spécifié. Pour plus d’informations, consultez [groupe de caractères positif](#PositiveGroup).  
  
- Groupes de caractères négatifs. Un caractère de la chaîne d'entrée ne doit pas correspondre à l'un des jeux de caractères spécifié. Pour plus d’informations, consultez [groupe de caractères négatif](#NegativeGroup).  
  
- Tout caractère. Le caractère `.` (point) dans une expression régulière est un caractère générique qui correspond à n'importe quel caractère sauf `\n`. Pour plus d’informations, consultez [tout caractère](#AnyCharacter).  
  
- Catégorie Unicode générale ou bloc nommé. Un caractère de la chaîne d'entrée doit être membre d'une catégorie Unicode particulière ou doit figurer dans une plage contiguë de caractères Unicode pour aboutir à une correspondance. Pour plus d’informations, consultez la rubrique [catégorie Unicode ou bloc Unicode](#CategoryOrBlock).  
  
- Catégorie Unicode générale négative ou bloc nommé. Un caractère de la chaîne d'entrée ne doit pas être membre d'une catégorie Unicode particulière ou ne doit pas figurer dans une plage contiguë de caractères Unicode pour aboutir à une correspondance. Pour plus d’informations, consultez [catégorie Unicode négative ou bloc Unicode](#NegativeCategoryOrBlock).  
  
- Caractère de mot. Un caractère de la chaîne d'entrée peut appartenir à l'une des catégories Unicode appropriées aux caractères contenus dans les mots. Pour plus d’informations, consultez [caractère de mot](#WordCharacter).  
  
- Caractère autre qu'un caractère de mot. Un caractère de la chaîne d'entrée peut appartenir à n'importe quelle catégorie Unicode qui n'est pas un caractère de mot. Pour plus d’informations, consultez [caractère autre qu’un mot](#NonWordCharacter).  
  
- Espace blanc. Un caractère de la chaîne d'entrée peut être n'importe quel caractère Unicode de séparation, ainsi que n'importe quel nombre de caractères de contrôle. Pour plus d’informations, consultez [espace blanc](#WhitespaceCharacter).  
  
- Caractère autre qu'un espace blanc. Un caractère de la chaîne d'entrée peut être n'importe quel caractère qui n'est pas un espace blanc. Pour plus d’informations, consultez [caractère autre qu’un espace blanc](#NonWhitespaceCharacter).  
  
- Chiffre décimal. Un caractère de la chaîne d'entrée peut être n'importe quel nombre de caractères classifiés en tant que chiffres décimaux Unicode. Pour plus d’informations, consultez [caractère décimal digit](#DigitCharacter).  
  
- Chiffre non décimal. Un caractère de la chaîne d'entrée peut correspondre à autre chose qu'un chiffre décimal Unicode. Pour plus d’informations, consultez [caractère décimal digit](#NonDigitCharacter).  
  
 .NET prend en charge les expressions de soustraction de classe de caractères, ce qui vous permet de définir un jeu de caractères comme résultat de l’exclusion d’une classe de caractères d’une autre classe de caractères. Pour plus d’informations, consultez [soustraction de classe de caractères](#CharacterClassSubtraction).  
  
> [!NOTE]
> Les classes de caractères qui font correspondre les caractères par catégorie, comme [\w](#WordCharacter) pour faire correspondre les caractères alphabétiques, ou [\p{}](#CategoryOrBlock) pour les faire correspondre à une catégorie Unicode, s’appuient sur la classe <xref:System.Globalization.CharUnicodeInfo> pour fournir des informations sur les catégories de caractères.  À compter de .NET Framework 4.6.2, les catégories de caractères sont basées sur la [norme Unicode version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). De .NET Framework 4 à .NET Framework 4.6.1, elles sont basées sur la [norme Unicode version 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/).  
  
<a name="PositiveGroup"></a>
## <a name="positive-character-group--"></a>Groupe de caractères positif : [ ]  
 Un groupe de caractères positif spécifie une liste de caractères, chacun d'entre eux pouvant apparaître dans une chaîne d'entrée pour produire une correspondance. Cette liste de caractères peut être spécifiée individuellement, comme une plage, ou les deux à la fois.  
  
 La syntaxe de la spécification d'une liste de différents caractères est comme suit :  

`[*character_group*]`

 où *groupe_caractères* est la liste des différents caractères pouvant apparaître dans la chaîne d’entrée pour qu’une correspondance soit établie. *character_group* peut être constitué de n’importe quelle combinaison d’un ou plusieurs caractères littéraux, de [caractères d’échappement](character-escapes-in-regular-expressions.md)ou de classes de caractères.  
  
 La syntaxe de la spécification d'une plage de caractères est comme suit :  
  
`[firstCharacter-lastCharacter]`  
  
 où *premiercaractère* est le caractère qui commence la plage et *derniercaractère* est le caractère qui termine la plage. Une plage de caractères est une série contiguë de caractères définie par la spécification du premier caractère de la série, d'un trait d'union (-), puis du dernier caractère de la série. Deux caractères sont contigus s'ils présentent des points de code Unicode adjacents. *premierCaractère* doit être le caractère avec le code de caractère le plus faible et *dernierCaractère* doit être le caractère avec le code de caractère le plus élevé.

> [!NOTE]
> Étant donné qu’un groupe de caractères positif peut inclure à la fois un jeu de caractères et une plage de caractères, un trait d’union (`-`) est toujours interprété comme le séparateur de plage, sauf s’il s’agit du premier ou dernier caractère du groupe.

Quelques modèles d'expressions régulières courants qui contiennent des classes de caractères positifs apparaissent dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`[aeiou]`|Mettre en correspondance toutes les voyelles.|  
|`[\p{P}\d]`|Mettre en correspondance tous les signes de ponctuation et chiffres décimaux.|  
|`[\s\p{P}]`|Mettre en correspondance tous les espaces blancs et signes de ponctuation.|  
  
 L'exemple suivant définit un groupe de caractères positif qui contient les caractères « a » et « e » afin que la chaîne d'entrée contienne les mots « grey » ou « gray » suivis par un autre mot pour produire une correspondance.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 L'expression régulière `gr[ae]y\s\S+?[\s|\p{P}]` est définie comme suit :  
  
|Modèle|Description|  
|-------------|-----------------|  
|`gr`|Mettre en correspondance les caractères littéraux « gr ».|  
|`[ae]`|Mettre en correspondance un « a » ou un « e ».|  
|`y\s`|Mettre en correspondance le caractère littéral « y » suivi d'un espace blanc.|  
|`\S+?`|Mettre en correspondance un ou plusieurs caractères autres que des espaces blancs, mais le moins possible.|  
|`[\s\p{P}]`|Mettre en correspondance un espace blanc ou un signe de ponctuation.|  
  
 L'exemple suivant correspond aux mots qui commencent par une majuscule. Il utilise la sous-expression `[A-Z]` pour représenter la plage de majuscules de A à Z.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 L'expression régulière `\b[A-Z]\w*\b` est définie comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`[A-Z]`|Mettre en correspondance une majuscule de A à Z.|  
|`\w*`|Mettre en correspondance zéro, un ou plusieurs caractères alphabétiques.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
  
<a name="NegativeGroup"></a>
## <a name="negative-character-group-"></a>Groupe de caractères négatif : [^]  
 Un groupe de caractères négatifs spécifie une liste de caractères qui ne doivent pas s'afficher dans une chaîne d'entrée pour produire une correspondance. La liste de caractères peut être spécifiée individuellement, comme une plage, ou les deux à la fois.  
  
La syntaxe de la spécification d'une liste de différents caractères est comme suit :  

`[*^character_group*]`

 où *groupe_caractères* est la liste des différents caractères qui ne peuvent pas apparaître dans la chaîne d’entrée pour qu’une correspondance soit établie. *character_group* peut être constitué de n’importe quelle combinaison d’un ou plusieurs caractères littéraux, de [caractères d’échappement](character-escapes-in-regular-expressions.md)ou de classes de caractères.  
  
 La syntaxe de la spécification d'une plage de caractères est comme suit :  

`[^*firstCharacter*-*lastCharacter*]`

où *premiercaractère* est le caractère qui commence la plage et *derniercaractère* est le caractère qui termine la plage. Une plage de caractères est une série contiguë de caractères définie par la spécification du premier caractère de la série, d'un trait d'union (-), puis du dernier caractère de la série. Deux caractères sont contigus s'ils présentent des points de code Unicode adjacents. *premierCaractère* doit être le caractère avec le code de caractère le plus faible et *dernierCaractère* doit être le caractère avec le code de caractère le plus élevé.

> [!NOTE]
> Étant donné qu’un groupe de caractères négatif peut inclure à la fois un jeu de caractères et une plage de caractères, un trait d’union (`-`) est toujours interprété comme le séparateur de plage, sauf s’il s’agit du premier ou dernier caractère du groupe.
  
 Deux ou plusieurs plages de caractères peuvent être concaténées. Par exemple, pour spécifier la plage de chiffres décimaux de « 0 » à « 9 », la plage de lettres minuscules de « a » à « f » et la plage de lettres majuscules de « A » à « F », utilisez `[0-9a-fA-F]`.  
  
 Le caractère de signe insertion de début ( `^` ) dans un groupe de caractères négatif est obligatoire et indique que le groupe de caractères est un groupe de caractères négatif et non un groupe de caractères positif.  
  
> [!IMPORTANT]
> Un groupe de caractères négatifs d'un plus grand modèle d'expressions régulières n'est pas une assertion de largeur nulle. Autrement dit, après avoir évalué le groupe de caractères négatif, le moteur des expressions régulières avance d'un caractère dans la chaîne d'entrée.  
  
 Quelques modèles d'expressions régulières courants qui contiennent des groupes de caractères négatifs apparaissent dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`[^aeiou]`|Mettre en correspondance tous les caractères, à l'exception des voyelles.|  
|`[^\p{P}\d]`|Mettre en correspondance tous les caractères, à l'exception des signes de ponctuation et des chiffres décimaux.|  
  
 L'exemple suivant correspond à un mot commençant par les caractères « th » et n'étant pas suivi d'un « o ».  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 L'expression régulière `\bth[^o]\w+\b` est définie comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`th`|Mettre en correspondance les caractères littéraux « th ».|  
|`[^o]`|Mettre en correspondance n'importe quel caractère autre que « o ».|  
|`\w+`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
|`\b`|Terminer à une limite de mot.|  
  
<a name="AnyCharacter"></a>
## <a name="any-character-"></a>N’importe quel caractère : .  
 Le point (.) correspond à n'importe quel caractère à l'exception de `\n` (caractère de saut de ligne, \u000A), avec les deux qualifications suivantes :  
  
- Si un modèle d'expression régulière est modifié par l'option <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> ou si la partie du modèle qui contient la classe de caractères `.` est modifiée par l'option `s`, `.` correspond à n'importe quel caractère. Pour plus d’informations, consultez [Options des expressions régulières](regular-expression-options.md).  
  
     L'exemple suivant illustre le comportement différent de la classe de caractères `.` par défaut et avec l'option <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>. L'expression régulière `^.+` commence au début de la chaîne et correspond à tous les caractères. Par défaut, la correspondance se termine à la fin de la première ligne ; le modèle d'expression régulière correspond au retour chariot, à `\r` ou à \u000D, mais il ne correspond pas à `\n`. Étant donné que l'option <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> interprète la chaîne d'entrée entière comme une ligne unique, il correspond à chaque caractère de la chaîne d'entrée, notamment `\n`.  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
> Étant donné qu'elle correspond à n'importe quel caractère sauf `\n`, la classe de caractères `.` correspond également à `\r` (retour chariot, \u000D).  
  
- Dans un groupe de caractères négatif ou positif, un point est traité comme un caractère littéral de point, et non pas comme une classe de caractères. Pour plus d'informations, consultez [Groupe de caractères positif](#PositiveGroup) et [Groupe de caractères négatif](#NegativeGroup) plus haut dans cette rubrique. L'exemple suivant en propose une illustration. Il définit une expression régulière qui inclut le point (`.`) à la fois en tant que classe de caractères et en tant que membre d'un groupe de caractères positif. L’expression régulière `\b.*[.?!;:](\s|\z)` commence à une limite de mot, correspond à n’importe quel caractère tant qu’elle ne rencontre pas l’un des cinq signes de ponctuation, y compris le point, puis correspond à un espace blanc ou à la fin de la chaîne.  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
> Étant donné qu'il correspond à n'importe quel caractère, l'élément de langage `.` est souvent utilisé avec un quantificateur limitatif si un modèle d'expression régulière essaie de correspondre plusieurs fois à n'importe quel caractère. Pour plus d’informations, consultez [Quantificateurs](quantifiers-in-regular-expressions.md).  
  
<a name="CategoryOrBlock"></a>
## <a name="unicode-category-or-unicode-block-p"></a>Catégorie Unicode ou bloc Unicode : \p{}  
 La norme Unicode assigne une catégorie générale à chaque caractère. Par exemple, un caractère particulier peut être une lettre majuscule (représenté par la catégorie `Lu`), un chiffre décimal (catégorie `Nd`), un symbole mathématique (catégorie `Sm`) ou un séparateur de paragraphe (catégorie `Zl`). Les jeux de caractères spécifiques de la norme Unicode occupent également une plage spécifique ou un bloc de points de code consécutifs. Par exemple, l'alphabet latin de base se trouve de \u0000 à \u007F, alors que le jeu de caractères arabe se trouve de \u0600 à \u06FF.  
  
 La construction d'expression régulière  
  
 `\p{`*nom*`}`  
  
 correspond à n’importe quel caractère qui appartient à une catégorie Unicode générale ou à un bloc nommé, où *nom* est l’abréviation de la catégorie ou le nom du bloc nommé. Pour obtenir la liste des abréviations des catégories, consultez la section [catégories générales Unicode prises en charge](#SupportedUnicodeGeneralCategories) plus loin dans cette rubrique. Pour obtenir la liste des blocs nommés, consultez la section [blocs nommés pris en charge](#SupportedNamedBlocks) plus loin dans cette rubrique.  
  
 L’exemple suivant utilise la `\p{` *name* `}` construction de nom pour faire correspondre à la fois une catégorie Unicode générale (dans ce cas, la `Pd` catégorie, ou la ponctuation, la catégorie de tirets) et un bloc nommé (les `IsGreek` `IsBasicLatin` blocs nommés et).  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 L'expression régulière `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` est définie comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`\p{IsGreek}+`|Mettre en correspondance un ou plusieurs caractères grecs.|  
|`(\s)?`|Mettre en correspondance zéro ou un espace blanc.|  
|`(\p{IsGreek}+(\s)?)+`|Mettre en correspondance le modèle d’un ou plusieurs caractères grecs, suivis de zéro ou d’un espace blanc, une ou plusieurs fois.|  
|`\p{Pd}`|Mettre en correspondance un signe de ponctuation tiret.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`\p{IsBasicLatin}+`|Mettre en correspondance un ou plusieurs caractères latins de base.|  
|`(\s)?`|Mettre en correspondance zéro ou un espace blanc.|  
|`(\p{IsBasicLatin}+(\s)?)+`|Mettre en correspondance un ou plusieurs caractères latins de base suivis de zéro ou d’un espace blanc, une ou plusieurs fois.|  
  
<a name="NegativeCategoryOrBlock"></a>
## <a name="negative-unicode-category-or-unicode-block-p"></a>Catégorie Unicode négative ou bloc Unicode : \P{}  
 La norme Unicode assigne une catégorie générale à chaque caractère. Par exemple, un caractère particulier peut être une lettre majuscule (représenté par la catégorie `Lu`), un chiffre décimal (catégorie `Nd`), un symbole mathématique (catégorie `Sm`) ou un séparateur de paragraphe (catégorie `Zl`). Les jeux de caractères spécifiques de la norme Unicode occupent également une plage spécifique ou un bloc de points de code consécutifs. Par exemple, l'alphabet latin de base se trouve de \u0000 à \u007F, alors que le jeu de caractères arabe se trouve de \u0600 à \u06FF.  
  
 La construction d'expression régulière  
  
 `\P{`*nom*`}`  
  
 correspond à n'importe quel caractère qui n'appartient pas à une catégorie générale Unicode ou à un bloc nommé, où *nom* est l'abréviation de la catégorie ou le nom du bloc nommé. Pour obtenir la liste des abréviations des catégories, consultez la section [catégories générales Unicode prises en charge](#SupportedUnicodeGeneralCategories) plus loin dans cette rubrique. Pour obtenir la liste des blocs nommés, consultez la section [blocs nommés pris en charge](#SupportedNamedBlocks) plus loin dans cette rubrique.  
  
 L’exemple suivant utilise la `\P{` *name* `}` construction de nom pour supprimer tous les symboles monétaires (dans ce cas, le `Sc` symbole, ou, la catégorie Currency) des chaînes numériques.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 Le modèle d'expression régulière `(\P{Sc})+` correspond à un ou plusieurs caractères qui ne sont pas des symboles monétaires ; il supprime efficacement tout symbole monétaire de la chaîne du résultat.  
  
<a name="WordCharacter"></a>
## <a name="word-character-w"></a>Caractère de mot : \w  
 `\w` correspond à n'importe quel caractère alphabétique. Un caractère de mot est un membre d'une des catégories Unicode répertoriées dans le tableau suivant.  
  
|Category|Description|  
|--------------|-----------------|  
|Ll|Letter, Lowercase|  
|Lu|Letter, Uppercase|  
|Lt|Letter, Titlecase|  
|Lo|Letter, Other|  
|Lm|Letter, Modifier|  
|Mn|Mark, Nonspacing|  
|Nd|Number, Decimal Digit|  
|Pc|Punctuation, Connector. Cette catégorie inclut dix caractères dont le plus souvent utilisé est le caractère LOWLINE (_), u+005F.|  
  
 Si un comportement conforme à ECMAScript est spécifié, `\w` est équivalent à `[a-zA-Z_0-9]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section « comportement de correspondance ECMAScript » dans [Options des expressions régulières](regular-expression-options.md).  
  
> [!NOTE]
> Étant donné qu'il correspond à n'importe quel caractère alphabétique, l'élément de langage `\w` est souvent utilisé avec un quantificateur limitatif si un modèle d'expression régulière essaie de correspondre plusieurs fois à n'importe quel caractère alphabétique, suivi par un caractère alphabétique spécifique. Pour plus d’informations, consultez [Quantificateurs](quantifiers-in-regular-expressions.md).  
  
 L'exemple suivant utilise l'élément de langage `\w` pour le faire corresponde à des caractères en double dans un mot. L'exemple définit un modèle d'expression régulière, `(\w)\1`, qui peut être interprété comme suit.  
  
|Élément|Description|  
|-------------|-----------------|  
|(\w)|Mettre en correspondance un caractère de mot. Il s'agit du premier groupe de capture.|  
|\1|Mettre en correspondance la valeur de la première capture.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
<a name="NonWordCharacter"></a>
## <a name="non-word-character-w"></a>Caractère autre qu’un mot : \W  
 `\W` correspond à tout caractère autre qu'un caractère alphabétique. L'élément de langage \W est équivalent à la classe de caractères suivante :  
  
`[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]`  
  
 En d’autres termes, il correspond à n’importe quel caractère à l’exception de ceux inclus dans les catégories Unicode répertoriées dans le tableau suivant.  
  
|Category|Description|  
|--------------|-----------------|  
|Ll|Letter, Lowercase|  
|Lu|Letter, Uppercase|  
|Lt|Letter, Titlecase|  
|Lo|Letter, Other|  
|Lm|Letter, Modifier|  
|Mn|Mark, Nonspacing|  
|Nd|Number, Decimal Digit|  
|Pc|Punctuation, Connector. Cette catégorie inclut dix caractères dont le plus souvent utilisé est le caractère LOWLINE (_), u+005F.|  
  
 Si un comportement conforme à ECMAScript est spécifié, `\W` est équivalent à `[^a-zA-Z_0-9]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section « comportement de correspondance ECMAScript » dans [Options des expressions régulières](regular-expression-options.md).  
  
> [!NOTE]
> Étant donné qu'il correspond à n'importe quel caractère non alphabétique, l'élément de langage `\W` est souvent utilisé avec un quantificateur limitatif si un modèle d'expression régulière essaie de correspondre plusieurs fois à n'importe quel caractère non alphabétique suivi d'un caractère non alphabétique spécifique. Pour plus d’informations, consultez [Quantificateurs](quantifiers-in-regular-expressions.md).  
  
 L'exemple suivant illustre la classe de caractères `\W`.  Il définit un modèle d'expression régulière, `\b(\w+)(\W){1,2}`, qui correspond à un mot suivi d'un ou deux caractères non alphabétiques, comme un espace ou un signe de ponctuation. L'expression régulière est interprétée comme indiqué dans le tableau suivant.  
  
|Élément|Description|  
|-------------|-----------------|  
|\b|Commencer la correspondance à la limite d'un mot.|  
|(\w+)|Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.|  
|(\W){1,2}|Mettre en correspondance un caractère autre qu'un mot une ou deux fois. Il s'agit du deuxième groupe de capture.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 Étant donné que l'objet <xref:System.Text.RegularExpressions.Group> du deuxième groupe de capture ne contient qu'un seul caractère autre qu'un mot capturé, l'exemple extrait tous les caractères autres que des mots capturés de l'objet <xref:System.Text.RegularExpressions.CaptureCollection> retourné par la propriété <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>.  
  
<a name="WhitespaceCharacter"></a>
## <a name="whitespace-character-s"></a>Espace : \s  
 `\s` correspond à n'importe quel espace. Il est équivalent aux séquences d'échappement et catégories Unicode répertoriées dans le tableau suivant.  
  
|Category|Description|  
|--------------|-----------------|  
|`\f`|Saut de page, \u000C.|  
|`\n`|Saut de ligne, \u000A.|  
|`\r`|Retour chariot, \u000D.|  
|`\t`|Tabulation, \u0009.|  
|`\v`|Tabulation verticale, \u000B.|  
|`\x85`|Points de suspension ou caractère À LA LIGNE (NEL) (…), \u0085.|  
|`\p{Z}`|Correspond à n'importe quel caractère de séparation.|  
  
 Si un comportement conforme à ECMAScript est spécifié, `\s` est équivalent à `[ \f\n\r\t\v]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section « comportement de correspondance ECMAScript » dans [Options des expressions régulières](regular-expression-options.md).  
  
 L'exemple suivant illustre la classe de caractères `\s`. Il définit un modèle d'expression régulière, `\b\w+(e)?s(\s|$)`, qui correspond à un mot se terminant par "s" ou par "es", suivi d'un espace ou de la fin de la chaîne d'entrée. L'expression régulière est interprétée comme indiqué dans le tableau suivant.  
  
|Élément|Description|  
|-------------|-----------------|  
|\b|Commencer la correspondance à la limite d'un mot.|  
|\w+|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
|(e)?|Mettre en correspondance un « e » zéro ou une fois.|  
|s|Mettre en correspondance un « s ».|  
|(\s&#124;$)|Mettre en correspondance un espace blanc ou la fin de la chaîne d’entrée.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
<a name="NonWhitespaceCharacter"></a>
## <a name="non-whitespace-character-s"></a>Caractère autre qu’un espace : \S  
 `\S` correspond à tout caractère autre qu'un espace. Il est équivalent au modèle d'expression régulière `[^\f\n\r\t\v\x85\p{Z}]` ou à l'opposé du modèle d'expression régulière qui est équivalent à `\s`, qui met en correspondance des espaces. Pour plus d'informations, consultez [Espace blanc : \s](#WhitespaceCharacter).  
  
 Si un comportement conforme à ECMAScript est spécifié, `\S` est équivalent à `[^ \f\n\r\t\v]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section « comportement de correspondance ECMAScript » dans [Options des expressions régulières](regular-expression-options.md).  
  
 L'exemple suivant illustre l'élément de langage `\S`. Le modèle d'expression régulière `\b(\S+)\s?` met en correspondance des chaînes délimitées par des espaces blancs. Le deuxième élément de l'objet <xref:System.Text.RegularExpressions.GroupCollection> de la correspondance contient la chaîne correspondante. L'expression régulière peut être interprétée comme indiqué dans le tableau suivant.  
  
|Élément|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(\S+)`|Mettre en correspondance un ou plusieurs caractères autres que des espaces blancs. Il s'agit du premier groupe de capture.|  
|`\s?`|Mettre en correspondance zéro ou un espace blanc.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
<a name="DigitCharacter"></a>
## <a name="decimal-digit-character-d"></a>Caractère numérique décimal : \d  
 `\d` correspond à n'importe quel chiffre décimal. Il est équivalent au modèle d'expression régulière `\p{Nd}`, qui inclut les chiffres décimaux standard de 0 à 9, ainsi que les chiffres décimaux de plusieurs autres jeux de caractères.  
  
 Si un comportement conforme à ECMAScript est spécifié, `\d` est équivalent à `[0-9]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section « comportement de correspondance ECMAScript » dans [Options des expressions régulières](regular-expression-options.md).  
  
 L'exemple suivant illustre l'élément de langage `\d`. Il teste si une chaîne d'entrée représente un numéro de téléphone valide aux États-Unis et au Canada. Le modèle d'expression régulière `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` est défini comme indiqué dans le tableau suivant.  
  
|Élément|Description|  
|-------------|-----------------|  
|`^`|Commencer la correspondance au début de la chaîne d'entrée.|  
|`\(?`|Mettre en correspondance zéro ou un caractère littéral « ( ».|  
|`\d{3}`|Mettre en correspondance trois chiffres décimaux.|  
|`\)?`|Mettre en correspondance zéro ou un caractère littéral « ) ».|  
|`[\s-]`|Mettre en correspondance un trait d'union ou un espace blanc.|  
|`(\(?\d{3}\)?[\s-])?`|Mettre en correspondance une parenthèse ouvrante facultative suivie de trois chiffres décimaux, d'une parenthèse fermante facultative et d'un espace blanc ou d'un tiret, zéro ou une fois. Il s'agit du premier groupe de capture.|  
|`\d{3}-\d{4}`|Mettre en correspondance trois chiffres décimaux suivis d'un trait d'union et de quatre chiffres décimaux supplémentaires.|  
|`$`|Mettre en correspondance la fin de la chaîne d'entrée.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
<a name="NonDigitCharacter"></a>
## <a name="non-digit-character-d"></a>Caractère autre qu’un chiffre : \D  
 `\D` correspond à n'importe quel caractère autre qu'un chiffre. Il est équivalent au modèle d'expression régulière `\P{Nd}`.  
  
 Si un comportement conforme à ECMAScript est spécifié, `\D` est équivalent à `[^0-9]`. Pour plus d’informations sur les expressions régulières ECMAScript, consultez la section « comportement de correspondance ECMAScript » dans [Options des expressions régulières](regular-expression-options.md).  
  
 L'exemple suivant illustre l'élément de langage \D. Il teste si une chaîne telle qu'un numéro de référence se compose de la combinaison appropriée de caractères décimaux et autres que des décimaux. Le modèle d'expression régulière `^\D\d{1,5}\D*$` est défini comme indiqué dans le tableau suivant.  
  
|Élément|Description|  
|-------------|-----------------|  
|`^`|Commencer la correspondance au début de la chaîne d'entrée.|  
|`\D`|Mettre en correspondance un caractère autre qu'un chiffre.|  
|`\d{1,5}`|Mettre en correspondance de un à cinq chiffres décimaux.|  
|`\D*`|Mettre en correspondance zéro, un ou plusieurs caractères non décimaux.|  
|`$`|Mettre en correspondance la fin de la chaîne d'entrée.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
<a name="SupportedUnicodeGeneralCategories"></a>
## <a name="supported-unicode-general-categories"></a>Catégories générales Unicode prises en charge  
 La norme Unicode définit les catégories générales répertoriées dans le tableau suivant. Pour plus d’informations, consultez les sous-rubriques « Format de fichier UCD » et « Valeurs des catégories générales » dans la [Base de données de caractères Unicode](https://www.unicode.org/reports/tr44/).  
  
|Category|Description|  
|--------------|-----------------|  
|`Lu`|Letter, Uppercase|  
|`Ll`|Letter, Lowercase|  
|`Lt`|Letter, Titlecase|  
|`Lm`|Letter, Modifier|  
|`Lo`|Letter, Other|  
|`L`|Toutes les lettres. Cela inclut les caractères `Lu`, `Ll`, `Lt`, `Lm` et `Lo`.|  
|`Mn`|Mark, Nonspacing|  
|`Mc`|Mark, Spacing Combining|  
|`Me`|Mark, Enclosing|  
|`M`|Toutes les signes diacritiques. Cela inclut les catégories `Mn`, `Mc` et `Me`.|  
|`Nd`|Number, Decimal Digit|  
|`Nl`|Number, Letter|  
|`No`|Number, Other|  
|`N`|Tous les nombres. Cela inclut les catégories `Nd`, `Nl` et `No`.|  
|`Pc`|Punctuation, Connector|  
|`Pd`|Punctuation, Dash|  
|`Ps`|Punctuation, Open|  
|`Pe`|Punctuation, Close|  
|`Pi`|Punctuation, Initial quote (peut se comporter comme Ps ou Pe selon l'utilisation)|  
|`Pf`|Punctuation, Final quote (peut se comporter comme Ps ou Pe selon l'utilisation)|  
|`Po`|Punctuation, Other|  
|`P`|Tous les caractères de ponctuation. Cela inclut les catégories `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf` et `Po`.|  
|`Sm`|Symbol, Math|  
|`Sc`|Symbol, Currency|  
|`Sk`|Symbol, Modifier|  
|`So`|Symbol, Other|  
|`S`|Tous les symboles. Cela inclut les catégories `Sm`, `Sc`, `Sk` et `So`.|  
|`Zs`|Separator, Space|  
|`Zl`|Separator, Line|  
|`Zp`|Separator, Paragraph|  
|`Z`|Tous les caractères de séparation. Cela inclut les catégories `Zs`, `Zl` et `Zp`.|  
|`Cc`|Other, Control|  
|`Cf`|Other, Format|  
|`Cs`|Other, Surrogate|  
|`Co`|Other, Private Use|  
|`Cn`|Other, Not Assigned (aucun caractère n'a cette propriété)|  
|`C`|Tous les caractères de contrôle. Cela inclut les catégories `Cc`, `Cf`, `Cs`, `Co` et `Cn`.|  
  
 Vous pouvez déterminer la catégorie Unicode de n'importe quel caractère particulier en passant ce caractère à la méthode <xref:System.Char.GetUnicodeCategory%2A>. L'exemple suivant utilise la méthode <xref:System.Char.GetUnicodeCategory%2A> pour déterminer la catégorie de chaque élément dans un tableau qui contient des caractères latins sélectionnés.  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
<a name="SupportedNamedBlocks"></a>
## <a name="supported-named-blocks"></a>Blocs nommés pris en charge

.NET fournit les blocs nommés répertoriés dans le tableau suivant. Le jeu de blocs nommés pris en charge est basé sur Unicode 4.0 et Perl 5.6. Pour une expression régulière qui utilise des blocs nommés, consultez la section [Catégorie Unicode ou bloc Unicode : \\p{}](#unicode-category-or-unicode-block-p).  
  
|Plage de points de code|Nom du bloc|  
|----------------------|----------------|  
|0000 - 007F|`IsBasicLatin`|  
|0080 - 00FF|`IsLatin-1Supplement`|  
|0100 - 017F|`IsLatinExtended-A`|  
|0180 - 024F|`IsLatinExtended-B`|  
|0250 - 02AF|`IsIPAExtensions`|  
|02B0 - 02FF|`IsSpacingModifierLetters`|  
|0300 - 036F|`IsCombiningDiacriticalMarks`|  
|0370 - 03FF|`IsGreek`<br /><br /> -ou-<br /><br /> `IsGreekandCoptic`|  
|0400 - 04FF|`IsCyrillic`|  
|0500 - 052F|`IsCyrillicSupplement`|  
|0530 - 058F|`IsArmenian`|  
|0590 - 05FF|`IsHebrew`|  
|0600 - 06FF|`IsArabic`|  
|0700 - 074F|`IsSyriac`|  
|0780 - 07BF|`IsThaana`|  
|0900 - 097F|`IsDevanagari`|  
|0980 - 09FF|`IsBengali`|  
|0A00 - 0A7F|`IsGurmukhi`|  
|0A80 - 0AFF|`IsGujarati`|  
|0B00 - 0B7F|`IsOriya`|  
|0B80 - 0BFF|`IsTamil`|  
|0C00 - 0C7F|`IsTelugu`|  
|0C80 - 0CFF|`IsKannada`|  
|0D00 - 0D7F|`IsMalayalam`|  
|0D80 - 0DFF|`IsSinhala`|  
|0E00 - 0E7F|`IsThai`|  
|0E80 - 0EFF|`IsLao`|  
|0F00 - 0FFF|`IsTibetan`|  
|1000 - 109F|`IsMyanmar`|  
|10A0 - 10FF|`IsGeorgian`|  
|1100 - 11FF|`IsHangulJamo`|  
|1200 - 137F|`IsEthiopic`|  
|13A0 - 13FF|`IsCherokee`|  
|1400 - 167F|`IsUnifiedCanadianAboriginalSyllabics`|  
|1680 - 169F|`IsOgham`|  
|16A0 - 16FF|`IsRunic`|  
|1700 - 171F|`IsTagalog`|  
|1720 - 173F|`IsHanunoo`|  
|1740 - 175F|`IsBuhid`|  
|1760 - 177F|`IsTagbanwa`|  
|1780 - 17FF|`IsKhmer`|  
|1800 - 18AF|`IsMongolian`|  
|1900 - 194F|`IsLimbu`|  
|1950 - 197F|`IsTaiLe`|  
|19E0 - 19FF|`IsKhmerSymbols`|  
|1D00 - 1D7F|`IsPhoneticExtensions`|  
|1E00 - 1EFF|`IsLatinExtendedAdditional`|  
|1F00 - 1FFF|`IsGreekExtended`|  
|2000 - 206F|`IsGeneralPunctuation`|  
|2070 - 209F|`IsSuperscriptsandSubscripts`|  
|20A0 - 20CF|`IsCurrencySymbols`|  
|20D0 - 20FF|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> -ou-<br /><br /> `IsCombiningMarksforSymbols`|  
|2100 - 214F|`IsLetterlikeSymbols`|  
|2150 - 218F|`IsNumberForms`|  
|2190 - 21FF|`IsArrows`|  
|2200 - 22FF|`IsMathematicalOperators`|  
|2300 - 23FF|`IsMiscellaneousTechnical`|  
|2400 - 243F|`IsControlPictures`|  
|2440 - 245F|`IsOpticalCharacterRecognition`|  
|2460 - 24FF|`IsEnclosedAlphanumerics`|  
|2500 - 257F|`IsBoxDrawing`|  
|2580 - 259F|`IsBlockElements`|  
|25A0 - 25FF|`IsGeometricShapes`|  
|2600 - 26FF|`IsMiscellaneousSymbols`|  
|2700 - 27BF|`IsDingbats`|  
|27C0 - 27EF|`IsMiscellaneousMathematicalSymbols-A`|  
|27F0 - 27FF|`IsSupplementalArrows-A`|  
|2800 - 28FF|`IsBraillePatterns`|  
|2900 - 297F|`IsSupplementalArrows-B`|  
|2980 - 29FF|`IsMiscellaneousMathematicalSymbols-B`|  
|2A00 - 2AFF|`IsSupplementalMathematicalOperators`|  
|2B00 - 2BFF|`IsMiscellaneousSymbolsandArrows`|  
|2E80 - 2EFF|`IsCJKRadicalsSupplement`|  
|2F00 - 2FDF|`IsKangxiRadicals`|  
|2FF0 - 2FFF|`IsIdeographicDescriptionCharacters`|  
|3000 - 303F|`IsCJKSymbolsandPunctuation`|  
|3040 - 309F|`IsHiragana`|  
|30A0 - 30FF|`IsKatakana`|  
|3100 - 312F|`IsBopomofo`|  
|3130 - 318F|`IsHangulCompatibilityJamo`|  
|3190 - 319F|`IsKanbun`|  
|31A0 - 31BF|`IsBopomofoExtended`|  
|31F0 - 31FF|`IsKatakanaPhoneticExtensions`|  
|3200 - 32FF|`IsEnclosedCJKLettersandMonths`|  
|3300 - 33FF|`IsCJKCompatibility`|  
|3400 - 4DBF|`IsCJKUnifiedIdeographsExtensionA`|  
|4DC0 - 4DFF|`IsYijingHexagramSymbols`|  
|4E00 - 9FFF|`IsCJKUnifiedIdeographs`|  
|A000 - A48F|`IsYiSyllables`|  
|A490 - A4CF|`IsYiRadicals`|  
|AC00 - D7AF|`IsHangulSyllables`|  
|D800 - DB7F|`IsHighSurrogates`|  
|DB80 - DBFF|`IsHighPrivateUseSurrogates`|  
|DC00 - DFFF|`IsLowSurrogates`|  
|E000 - F8FF|`IsPrivateUse` ou `IsPrivateUseArea`|  
|F900 - FAFF|`IsCJKCompatibilityIdeographs`|  
|FB00 - FB4F|`IsAlphabeticPresentationForms`|  
|FB50 - FDFF|`IsArabicPresentationForms-A`|  
|FE00 - FE0F|`IsVariationSelectors`|  
|FE20 - FE2F|`IsCombiningHalfMarks`|  
|FE30 - FE4F|`IsCJKCompatibilityForms`|  
|FE50 - FE6F|`IsSmallFormVariants`|  
|FE70 - FEFF|`IsArabicPresentationForms-B`|  
|FF00 - FFEF|`IsHalfwidthandFullwidthForms`|  
|FFF0 - FFFF|`IsSpecials`|  
  
<a name="CharacterClassSubtraction"></a>
## <a name="character-class-subtraction-base_group---excluded_group"></a>Soustraction de classe de caractères : [groupe_base - [groupe_exclu]]  
 Une classe de caractères définit un jeu de caractères. La soustraction de classe de caractères produit un jeu de caractères qui est le résultat de l'exclusion des caractères d'une classe de caractères d'une autre classe de caractères.  
  
 Une expression de soustraction de classe de caractères a la forme suivante :  
  
 `[`*base_group* `-[` *excluded_group*`]]`  
  
 Les crochets (`[]`) et le trait d'union (`-`) sont obligatoires. Le *base_group* est un [groupe de caractères positif](#PositiveGroup) ou un [groupe de caractères négatif](#NegativeGroup). Le composant *groupe_exclu* est un autre groupe de caractères positif ou négatif, ou une autre expression de soustraction de classe de caractères (autrement dit, vous pouvez imbriquer des expressions de soustraction de classe de caractères).  
  
 Par exemple, supposons que vous disposiez d'un groupe de base composé de la plage de caractères « a » à « z ». Pour définir le jeu de caractères composé du groupe de base, à l'exception du caractère « m », utilisez `[a-z-[m]]`. Pour définir le jeu de caractères composé du groupe de base, à l'exception du jeu de caractères « d », « j » et « p », utilisez `[a-z-[djp]]`. Pour définir le jeu de caractères composé du groupe de base, à l'exception de la plage de caractères allant de « m » à « p », utilisez `[a-z-[m-p]]`.  
  
 Prenons l'exemple de l'expression de soustraction de classe de caractères imbriquée, `[a-z-[d-w-[m-o]]]`. L'expression est évaluée à partir de la plage de caractères la plus profonde, vers l'extérieur. Tout d'abord, la plage de caractères « m » à « o » est soustraite de la plage de caractères « d » à « w », ce qui génère le jeu de caractères « d » à « l » et « p » à « w ». Ce jeu est ensuite soustrait de la plage de caractères allant de « a » à « z », ce qui produit le jeu de caractères `[abcmnoxyz]`.  
  
 Vous pouvez utiliser n'importe quelle classe de caractères avec la soustraction de classe de caractères. Pour définir le jeu de caractères qui se compose de tous les caractères Unicode de \u0000 à \uFFFF, à l'exception des espaces (`\s`), les caractères de la catégorie générale de ponctuation (`\p{P}`), les caractères du bloc nommé `IsGreek` (`\p{IsGreek}`) et le caractère de contrôle Unicode LIGNE SUIVANTE (\x85), utilisez `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.  
  
 Choisissez des classes de caractères pour une expression de soustraction de classe de caractères qui produira des résultats utiles. Évitez toute expression produisant un jeu de caractères vide, n'ayant aucune correspondance ou toute expression équivalant au groupe de base d'origine. Par exemple, le jeu vide résulte de l'expression `[\p{IsBasicLatin}-[\x00-\x7F]]`, qui soustrait tous les caractères compris dans la plage de caractères `IsBasicLatin` de la catégorie générale `IsBasicLatin`. De même, le groupe de base d'origine résulte de l'expression `[a-z-[0-9]]`.  Cela est dû au fait que le groupe de base, c'est-à-dire la plage de caractères des lettres de « a » à « z », ne contient aucun caractère dans le groupe exclu, c'est-à-dire la plage de caractères des chiffres décimaux de « 0 » à « 9 ».  
  
 L'exemple suivant définit une expression régulière, `^[0-9-[2468]]+$`, qui correspond à zéro et aux nombres impairs d'une chaîne d'entrée.  L'expression régulière est interprétée comme indiqué dans le tableau suivant.  
  
|Élément|Description|  
|-------------|-----------------|  
|^|Commencer la correspondance au démarrage de la chaîne d'entrée.|  
|`[0-9-[2468]]+`|Mettre en correspondance une ou plusieurs occurrences de n'importe quel caractère de 0 à 9 à l'exception de 2, 4, 6 et 8. En d'autres termes, mettre en correspondance une ou plusieurs occurrences de zéro ou d'un chiffre impair.|  
|$|Terminer la correspondance à la fin de la chaîne d'entrée.|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Char.GetUnicodeCategory%2A>
- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
- [Options des expressions régulières](regular-expression-options.md)
