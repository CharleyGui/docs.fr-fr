---
title: Constructions de référence arrière dans les expressions régulières .NET
description: Découvrez comment identifier les éléments textuels répétés avec des constructions de référence arrière dans une expression régulière.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
ms.openlocfilehash: 905578d763ebe5d5b8eb96a9056fbe11fbfab137
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711530"
---
# <a name="backreference-constructs-in-regular-expressions"></a>Constructions de backreference dans les expressions régulières

Les références arrière offrent un moyen pratique d’identifier un caractère répété ou une sous-chaîne répétée dans une chaîne. Par exemple, si la chaîne d’entrée contient plusieurs occurrences d’une sous-chaîne arbitraire, vous pouvez faire correspondre la première occurrence à un groupe de capture, puis utiliser une référence arrière pour faire correspondre les occurrences suivantes de la sous-chaîne.

> [!NOTE]
> Une syntaxe distincte est utilisée pour faire référence à des groupes de capture nommés et numérotés dans les chaînes de remplacement. Pour plus d’informations, consultez [Substitutions](substitutions-in-regular-expressions.md).

.NET définit des éléments de langage différents pour faire référence aux groupes de capture nommés et numérotés. Pour plus d’informations sur les groupes de capture, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

## <a name="numbered-backreferences"></a>Références arrière numérotées

Une référence arrière numérotée utilise la syntaxe suivante :

`\`*nombre*

où *numéro* est la position ordinale du groupe de capture dans l’expression régulière. Par exemple, `\4` correspond au contenu du quatrième groupe de capture. Si *numéro* n’est pas défini dans le modèle d’expression régulière, une erreur d’analyse se produit et le moteur d’expression régulière lève une exception <xref:System.ArgumentException>. Par exemple, l’expression régulière `\b(\w+)\s\1` est valide, car `(\w+)` est le premier et unique groupe de capture dans l’expression. D’un autre côté, `\b(\w+)\s\2` n’est pas valide et lève une exception d’argument, car il n’existe aucun groupe de capture numéroté `\2`. En outre, si *nombre* identifie un groupe de capture dans une position ordinale particulière, mais qu’un nom numérique différent de sa position ordinale a été affecté au groupe de capture, l’analyseur d’expression régulière lève également une <xref:System.ArgumentException>.

Remarquez l’ambiguïté entre les codes d’échappement octaux (tels que `\16`) et les références arrière `\`*numéro* qui utilisent la même notation. Cette ambiguïté est résolue comme suit :

- Les expressions `\1` à `\9` sont toujours interprétées comme références arrière et non comme codes octaux.

- Si le premier chiffre d’une expression à plusieurs chiffres est 8 ou 9 (comme `\80` ou `\91`), l’expression est interprétée comme littéral.

- Les expressions à partir de `\10` et plus sont considérées comme des références arrière s’il existe une référence arrière correspondant à ce numéro ; sinon, elles sont interprétées comme des codes octaux.

- Si une expression régulière contient une référence arrière à un numéro de groupe non défini, une erreur d’analyse se produit et le moteur d’expression régulière lève une exception <xref:System.ArgumentException>.

Si l’ambiguïté est un `\k<`problème, vous pouvez utiliser la notation de *nom,* `>` qui est sans ambiguïté et ne peut pas être confondu avec les codes de caractère octal. De même, les codes hexadécimaux tels que `\xdd` ne sont pas ambigus et ne peuvent pas être confondus avec les références arrière.

L’exemple suivant recherche des caractères de mot doubles dans une chaîne. Il définit une expression régulière, `(\w)\1`, qui se compose des éléments suivants.

|Élément|Description|
|-------------|-----------------|
|`(\w)`|Mettre en correspondance un caractère de mot et l’affecter au premier groupe de capture.|
|`\1`|Mettre en correspondance le caractère suivant dont la valeur est identique à celle du premier groupe de capture.|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a>Références arrière nommées

Une référence arrière nommée est définie avec la syntaxe suivante :

`\k<`*nom*`>`

ou :

`\k'`*nom*`'`

où *nom* est le nom d’un groupe de capture défini dans le modèle d’expression régulière. Si *nom* n’est pas défini dans le modèle d’expression régulière, une erreur d’analyse se produit et le moteur d’expression régulière lève une exception <xref:System.ArgumentException>.

L’exemple suivant recherche des caractères de mot doubles dans une chaîne. Il définit une expression régulière, `(?<char>\w)\k<char>`, qui se compose des éléments suivants.

|Élément|Description|
|-------------|-----------------|
|`(?<char>\w)`|Mettre en correspondance un caractère de mot et l’affecter à un groupe de capture nommé `char`.|
|`\k<char>`|Mettre en correspondance le caractère suivant dont la valeur est identique à celle du groupe de capture `char`.|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a>Références arrières numériques nommées

Dans une référence arrière nommée avec `\k`, *nom* peut également être la représentation d’un nombre sous forme de chaîne. Par exemple, l’exemple suivant utilise l’expression régulière `(?<2>\w)\k<2>` pour rechercher des caractères de mot doubles dans une chaîne. Dans ce cas, l’exemple définit un groupe de capture explicitement nommé « 2 », et la référence arrière est nommée en conséquence « 2 ».

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

Si *nom* est la représentation d’un nombre sous forme de chaîne et qu’aucun groupe de capture n’a ce nom, `\k<`*nom*`>` est identique au `\`* nombre* de la référence arrière, où *nombre* est la position ordinale de la capture. Dans l’exemple suivant, il existe un seul groupe de capture nommé `char`. La construction de la référence arrière la référence en tant que `\k<1>`. Comme la sortie de l’exemple le montre, l’appel à <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> réussit, car `char` est le premier groupe de capture.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

Cependant, si *nom* est la représentation sous forme de chaîne d’un nombre et qu’un nom numérique a été affecté explicitement à ce groupe de capture dans cette position, l’analyseur d’expression régulière ne peut pas identifier le groupe de capture par sa position ordinale. Au lieu de <xref:System.ArgumentException>cela, il jette un . Le seul groupe de capture dans l’exemple suivant est nommé "2". Comme la construction `\k` est utilisée pour définir une référence arrière nommée « 1 », l’analyseur d’expression régulière ne peut pas identifier le premier groupe de capture et lève une exception.

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a>Correspondance des références arrière

Une référence arrière référence la définition la plus récente d’un groupe (la définition la plus immédiatement à gauche, dans le cadre d’une mise en correspondance de gauche à droite). Quand un groupe effectue plusieurs captures, une référence arrière référence la capture la plus récente.

L’exemple suivant inclut un modèle d’expression régulière, `(?<1>a)(?<1>\1b)*`, qui redéfinit le groupe nommé \1. Le tableau suivant décrit chaque modèle dans l’expression régulière.

|Modèle|Description|
|-------------|-----------------|
|`(?<1>a)`|Mettre en correspondance le caractère « a » et affecter le résultat au groupe de capture nommé `1`.|
|`(?<1>\1b)*`|Mettre en correspondance zéro ou plus d’occurrences du groupe nommé `1` avec un « b » et affecter le résultat au groupe de capture nommé `1`.|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

En comparant l’expression régulière à la chaîne d’entrée (« aababb »), le moteur d’expression régulière effectue les opérations suivantes :

1. Il commence au début de la chaîne et réussit à mettre en correspondance « a » avec l’expression `(?<1>a)`. La valeur du groupe `1` est maintenant « a ».

2. Il passe au deuxième caractère et réussit à mettre en correspondance la chaîne « ab » avec l’expression `\1b`, ou « ab ». Il affecte ensuite le résultat, « ab », à `\1`.

3. Il passe au quatrième caractère. L’expression `(?<1>\1b)*` doit être mise en correspondance zéro fois ou plus, donc il réussit à mettre en correspondance la chaîne « abb » avec l’expression `\1b`. Il réaffecte le résultat, « abb », à `\1`.

Dans cet exemple, `*` est un quantificateur en boucle : il est évalué à plusieurs reprises jusqu’à ce que le moteur d’expression régulière ne puisse pas mettre en correspondance le modèle qu’il définit. Les quantificateurs en boucle ne suppriment pas les définitions de groupe.

Si un groupe n’a capturé aucune sous-chaîne, aucune référence arrière à ce groupe n’est définie et aucune correspondance n’est trouvée. Ce point est illustré par le modèle d’expression régulière `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` qui est défini comme suit :

|Modèle|Description|
|-------------|-----------------|
|`\b`|Commencer la correspondance à la limite d'un mot.|
|`(\p{Lu}{2})`|Mettre en correspondance deux lettres majuscules. Il s'agit du premier groupe de capture.|
|`(\d{2})?`|Mettre en correspondance zéro ou une occurrence de deux chiffres décimaux. Il s'agit du deuxième groupe de capture.|
|`(\p{Lu}{2})`|Mettre en correspondance deux lettres majuscules. Il s'agit du troisième groupe de capture.|
|`\b`|Terminer la correspondance à la limite d'un mot.|

Une chaîne d’entrée peut mettre en correspondre cette expression régulière même si les deux chiffres décimaux définis par le deuxième groupe de capture ne sont pas présents. L’exemple suivant montre que, même si la mise en correspondance réussit, un groupe de capture vide est trouvé entre deux groupes de capture trouvés.

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a>Voir aussi

- [Langage d’expression régulière - Référence rapide](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
