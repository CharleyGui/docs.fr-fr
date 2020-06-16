---
title: Substitutions dans les expressions régulières
description: Faites en sorte que les substitutions remplacent le texte mis en correspondance à l’aide d’expressions régulières dans .NET. Les substitutions sont des éléments de langage reconnus uniquement dans des modèles de remplacement.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, substitutions
- replacement patterns
- metacharacters, substitutions
- .NET Framework regular expressions, substitutions
- constructs, substitutions
- substitutions
ms.assetid: d1f52431-1c7d-4dc6-8792-6b988256892e
ms.openlocfilehash: ab2ed6ff87f2d50d0f518ac64188bf8b5c98351c
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768103"
---
# <a name="substitutions-in-regular-expressions"></a>Substitutions dans les expressions régulières
Les substitutions sont des éléments de langage reconnus uniquement dans des modèles de remplacement. Elles utilisent un modèle d'expression régulière pour définir tout ou partie du texte qui doit remplacer le texte correspondant dans la chaîne d'entrée. Le modèle de remplacement peut se composer d'une ou plusieurs substitutions avec des caractères littéraux. Les modèles de remplacement sont fournis aux surcharges de la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> qui a un paramètre `replacement` et à la méthode <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> . Les méthodes remplacent le modèle correspondant par le modèle défini par le paramètre `replacement` .  
  
 Le .NET Framework définit les éléments de substitution répertoriés dans le tableau suivant.  
  
|Substitution|Description|  
|------------------|-----------------|  
|$ *certain*|Inclut la dernière sous-chaîne correspondant au groupe de capture identifié par *nombre*, où *nombre* est une valeur décimale, dans la chaîne de remplacement. Pour plus d'informations, consultez [Substitution d'un groupe numéroté](#substituting-a-numbered-group).|  
|${ *nom* }|Comprend la dernière sous-chaîne correspondant au groupe nommé désigné par `(?<` *nom* `> )` dans la chaîne de remplacement. Pour plus d'informations, consultez [Substitution d'un groupe nommé](#substituting-a-named-group).|  
|$$|Inclut un littéral « $ » unique dans la chaîne de remplacement. Pour plus d'informations, consultez [Substitution d'un symbole « $ »](#substituting-a--character).|  
|$&|Inclut une copie de la correspondance entière dans la chaîne de remplacement. Pour plus d'informations, consultez [Substitution de la correspondance entière](#substituting-the-entire-match).|  
|$\`|Inclut tout le texte de la chaîne d'entrée avant la correspondance dans la chaîne de remplacement. Pour plus d'informations, consultez [Substitution du texte avant la correspondance](#substituting-the-text-before-the-match).|  
|$'|Inclut tout le texte de la chaîne d'entrée après la correspondance dans la chaîne de remplacement. Pour plus d'informations, consultez [Substitution du texte après la correspondance](#substituting-the-text-after-the-match).|  
|$+|Inclut le dernier groupe capturé dans la chaîne de remplacement. Pour plus d'informations, consultez [Substitution du dernier groupe capturé](#substituting-the-last-captured-group).|  
|$\_|Inclut la chaîne d'entrée entière dans la chaîne de remplacement. Pour plus d'informations, consultez [Substitution de la chaîne d'entrée entière](#substituting-the-entire-input-string).|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>Éléments de substitution et modèles de remplacement  
 Les substitutions sont les seules constructions particulières acceptées dans un modèle de remplacement. Aucun des autres éléments de langage d'expression régulière, notamment les caractères d'échappement et le point (`.`), qui correspond à n'importe quel caractère, n'est pris en charge. De la même façon, les éléments de langage de substitution sont reconnus uniquement dans les modèles de remplacement et ne sont jamais valides dans les modèles d'expressions régulières.  
  
 Le seul caractère qui peut apparaître dans un modèle d'expression régulière ou dans une substitution est le caractère `$` , bien qu'il ait une signification différente dans chaque contexte. Dans un modèle d'expression régulière, `$` est une ancre qui correspond à la fin de la chaîne. Dans un modèle de remplacement, `$` indique le début d'une substitution.  
  
> [!NOTE]
> Pour les fonctionnalités semblables à un modèle de remplacement dans une expression régulière, utilisez une référence arrière. Pour plus d’informations sur les références arrière, consultez [constructions de backreference](backreference-constructs-in-regular-expressions.md).  

## <a name="substituting-a-numbered-group"></a>Substitution d'un groupe numéroté  
 L' `$` élément de langage *nombre* comprend la dernière sous-chaîne correspondant au groupe de capture *nombre* dans la chaîne de remplacement, où *nombre* est l’index du groupe de capture. Par exemple, le modèle de remplacement `$1` indique que la sous-chaîne correspondante sera remplacée par le premier groupe capturé. Pour plus d’informations sur les groupes de capture numérotés, consultez [Grouping Constructs](grouping-constructs-in-regular-expressions.md).  
  
 Tous les chiffres qui suivent `$` sont interprétés comme appartenant au groupe *nombre* . Si ce n'est pas votre intention, vous pouvez remplacer un groupe nommé à la place. Par exemple, vous pouvez utiliser la chaîne de remplacement `${1}1` au lieu de `$11` pour définir la chaîne de remplacement comme la valeur du premier groupe capturé avec le numéro « 1 ». Pour plus d'informations, consultez [Substitution d'un groupe nommé](#substituting-a-named-group).  
  
 Les groupes de capture auxquels des noms ne sont pas explicitement assignés à l’aide de la `(?<` *name* `>)` syntaxe de nom sont numérotés de gauche à droite en commençant à un. Les groupes nommés sont également numérotés de gauche à droite, en démarrant à un numéro de plus que l'index du dernier groupe sans nom. Par exemple, dans l'expression régulière `(\w)(?<digit>\d)`, l'index du groupe nommé `digit` est 2.  
  
 Si le *nombre* ne spécifie pas un groupe de capture valide défini dans le modèle d'expression régulière, `$`*nombre* est interprété comme une séquence de caractères littéraux utilisée pour remplacer chaque correspondance.  
  
 L'exemple suivant utilise la substitution `$`*nombre* pour supprimer le symbole monétaire d'une valeur décimale. Elle supprime les symboles monétaires trouvés au début ou à la fin d'une valeur monétaire, et reconnaît les deux séparateurs décimaux les plus courants (« . » et « , »).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 Le modèle d'expression régulière `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\p{Sc}*`|Mettre en correspondance zéro ou plusieurs caractères de symbole monétaire.|  
|`\s?`|Mettre en correspondance zéro ou des espaces blancs.|  
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|  
|`[.,]?`|Mettre en correspondance zéro ou un point ou une virgule.|  
|`\d*`|Met en correspondance zéro ou plusieurs chiffres décimaux.|  
|`(\s?\d+[.,]?\d*)`|Mettre en correspondance un espace blanc suivi par un ou plusieurs chiffres décimaux, suivi par zéro ou un point ou une virgule, suivi par zéro ou plusieurs chiffres décimaux. Il s'agit du premier groupe de capture. Étant donné que le modèle de remplacement est `$1`, l'appel à la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> remplace l'intégralité de la sous-chaîne correspondante par ce groupe capturé.|  

## <a name="substituting-a-named-group"></a>Substitution d'un groupe nommé  
 L' `${` *name* `}` élément langage de nom remplace la dernière sous-chaîne correspondant au groupe de capture *nom* , où *nom* est le nom d’un groupe de capture défini par l' `(?<` élément de langage *nom* `>)` . Pour plus d’informations sur les groupes de capture nommés, consultez [Grouping Constructs](grouping-constructs-in-regular-expressions.md).  
  
 Si le *nom* ne spécifie pas de groupe de capture nommé valide défini dans le modèle d'expression régulière mais se compose de chiffres, `${`*nom*`}` est interprété en tant que groupe numéroté.  
  
 Si le *nom* ne spécifie ni un groupe de capture nommé valide ni un groupe de capture numéroté valide défini dans le modèle d'expression régulière, `${`*nom*`}` est interprété comme une séquence de caractères littéraux utilisée pour remplacer chaque correspondance.  
  
 L’exemple suivant utilise la `${` substitution de *nom* `}` pour supprimer le symbole monétaire d’une valeur décimale. Elle supprime les symboles monétaires trouvés au début ou à la fin d'une valeur monétaire, et reconnaît les deux séparateurs décimaux les plus courants (« . » et « , »).  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 Le modèle d'expression régulière `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\p{Sc}*`|Mettre en correspondance zéro ou plusieurs caractères de symbole monétaire.|  
|`\s?`|Mettre en correspondance zéro ou des espaces blancs.|  
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|  
|`[.,]?`|Mettre en correspondance zéro ou un point ou une virgule.|  
|`\d*`|Met en correspondance zéro ou plusieurs chiffres décimaux.|  
|`(?<amount>\s?\d[.,]?\d*)`|Mettre en correspondance un espace blanc, suivi par un ou plusieurs chiffres décimaux, suivi par zéro ou un point ou une virgule, suivi par zéro ou plusieurs chiffres décimaux. C'est le groupe de capture nommé `amount`. Étant donné que le modèle de remplacement est `${amount}`, l'appel à la méthode <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> remplace l'intégralité de la sous-chaîne correspondante par ce groupe capturé.|  

## <a name="substituting-a--character"></a>Substitution d'un caractère « $ »  
 La substitution `$$` insère un caractère « $ » littéral dans la chaîne remplacée.  
  
 L'exemple suivant utilise l'objet <xref:System.Globalization.NumberFormatInfo> pour déterminer le symbole monétaire de la culture actuelle et son positionnement dans une chaîne monétaire. Il génère alors à la fois dynamiquement un modèle d'expression régulière et un modèle de remplacement. Si l'exemple est exécuté sur un ordinateur dont la culture actuelle est en-US, il génère le modèle d'expression régulière `\b(\d+)(\.(\d+))?` et le modèle de remplacement `$$ $1$2`. Le modèle de remplacement remplace le texte correspondant par un symbole monétaire et un espace suivi par les premier et second groupes capturés.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 Le modèle d'expression régulière `\b(\d+)(\.(\d+))?` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Démarrer la correspondance au début d'une limite de mot.|  
|`(\d+)`|Mettre en correspondance un ou plusieurs chiffres décimaux. Il s'agit du premier groupe de capture.|  
|`\.`|Mettre en correspondance un point (le séparateur décimal).|  
|`(\d+)`|Mettre en correspondance un ou plusieurs chiffres décimaux. Il s'agit du troisième groupe de capture.|  
|`(\.(\d+))?`|Mettre en correspondance zéro ou une occurrence d'un point suivi par un ou plusieurs chiffres décimaux. Il s'agit du deuxième groupe de capture.|  

## <a name="substituting-the-entire-match"></a>Substitution de la correspondance entière  
 La substitution `$&` inclut la correspondance entière dans la chaîne de remplacement. Souvent, elle est utilisée pour ajouter une sous-chaîne au début ou à la fin de la chaîne correspondante. Par exemple, le modèle de remplacement `($&)` ajoute des parenthèses au début et à la fin de chaque correspondance. S'il n'y a pas de correspondance, la substitution `$&` n'a aucun effet.  
  
 L'exemple suivant utilise la substitution `$&` pour ajouter des guillemets au début et à la fin de titres de livres stockés dans un tableau de chaînes.  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 Le modèle d'expression régulière `^(\w+\s?)+$` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Commencer la correspondance au début de la chaîne d'entrée.|  
|`(\w+\s?)+`|Mettre en correspondance le modèle d'un ou plusieurs caractères de mot, suivis de zéro ou d'un espace blanc, une ou plusieurs fois.|  
|`$`|Mettre en correspondance la fin de la chaîne d'entrée.|  
  
 Le modèle de remplacement `"$&"` ajoute un guillemet littéral au début et à la fin de chaque correspondance.  

## <a name="substituting-the-text-before-the-match"></a>Substitution du texte avant la correspondance  
 La substitution ``$` `` remplace la chaîne correspondante par la chaîne d'entrée entière avant la correspondance. Autrement dit, elle duplique la chaîne d'entrée jusqu'à la correspondance en supprimant le texte correspondant. N'importe quel texte qui suit le texte correspondant est inchangé dans la chaîne de résultat. S'il existe plusieurs correspondances dans une chaîne d'entrée, le texte de remplacement est dérivé de la chaîne d'entrée d'origine, plutôt que de la chaîne dans laquelle le texte a été remplacé par des correspondances précédentes. \(L’exemple fournit une illustration. \) S’il n’y a aucune correspondance, la ``$` `` substitution n’a aucun effet.  
  
 L'exemple suivant utilise le modèle d'expression régulière `\d+` pour faire correspondre une séquence d'un ou de plusieurs chiffres décimaux dans la chaîne d'entrée. La chaîne de remplacement ``$` `` remplace ces chiffres par le texte qui précède la correspondance.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 Dans cet exemple, la chaîne d'entrée `"aa1bb2cc3dd4ee5"` contient cinq correspondances. Le tableau suivant illustre comment la substitution ``$` `` entraîne le remplacement de chaque correspondance dans la chaîne d'entrée par le moteur des expressions régulières. Le texte inséré est affiché en gras dans la colonne de résultats.  
  
|Correspond|Position|Chaîne avant la correspondance|Chaîne de résultat|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|aa**aa**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|

## <a name="substituting-the-text-after-the-match"></a>Substitution du texte après la correspondance  
 La substitution `$'` remplace la chaîne correspondante par la chaîne d'entrée entière après la correspondance. Autrement dit, elle duplique la chaîne d'entrée après la correspondance en supprimant le texte correspondant. N'importe quel texte qui précède le texte correspondant est inchangé dans la chaîne de résultat. S'il n'y a pas de correspondance, la substitution  `$'` n'a aucun effet.  
  
 L'exemple suivant utilise le modèle d'expression régulière `\d+` pour faire correspondre une séquence d'un ou de plusieurs chiffres décimaux dans la chaîne d'entrée. La chaîne de remplacement `$'` remplace ces chiffres par le texte qui suit la correspondance.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 Dans cet exemple, la chaîne d'entrée `"aa1bb2cc3dd4ee5"` contient cinq correspondances. Le tableau suivant illustre comment la substitution `$'` entraîne le remplacement de chaque correspondance dans la chaîne d'entrée par le moteur des expressions régulières. Le texte inséré est affiché en gras dans la colonne de résultats.  
  
|Correspond|Position|Chaîne après la correspondance|Chaîne de résultat|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  

## <a name="substituting-the-last-captured-group"></a>Substitution du dernier groupe capturé  
 La substitution `$+` remplace la chaîne correspondante par le dernier groupe capturé. S'il n'y a pas de groupes capturés ou si la valeur du dernier groupe capturé est <xref:System.String.Empty?displayProperty=nameWithType>, la substitution `$+` n'a aucun effet.  
  
 L'exemple suivant identifie des mots en double dans une chaîne et utilise la substitution `$+` pour les remplacer par une occurrence unique du mot. L'option <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> est utilisée pour vérifier que les mots, qui diffèrent en termes de casse mais qui sont identiques par ailleurs, sont considérés comme des doublons.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 Le modèle d'expression régulière `\b(\w+)\s\1\b` est défini comme indiqué dans le tableau suivant.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer la correspondance à la limite d'un mot.|  
|`(\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`\1`|Mettre en correspondance le premier groupe capturé.|  
|`\b`|Terminer la correspondance à la limite d'un mot.|  

## <a name="substituting-the-entire-input-string"></a>Substitution de la chaîne d'entrée entière  
 La substitution `$_` remplace la chaîne correspondante par la chaîne d'entrée entière. Autrement dit, elle supprime le texte correspondant et le remplace par la chaîne entière, notamment le texte correspondant.  
  
 L'exemple suivant correspond à un ou plusieurs chiffres décimaux dans la chaîne d'entrée. Il utilise la substitution `$_` pour les remplacer par la chaîne d'entrée entière.  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 Dans cet exemple, la chaîne d'entrée `"ABC123DEF456"` contient deux correspondances. Le tableau suivant illustre comment la substitution `$_` entraîne le remplacement de chaque correspondance dans la chaîne d'entrée par le moteur des expressions régulières. Le texte inséré est affiché en gras dans la colonne de résultats.  
  
|Correspond|Position|Correspond|Chaîne de résultat|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>Voir aussi

- [Langage des expressions régulières - Aide-mémoire](regular-expression-language-quick-reference.md)
