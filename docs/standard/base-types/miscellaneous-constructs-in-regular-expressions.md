---
title: Constructions diverses dans les expressions régulières
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
ms.openlocfilehash: a43ce44e11a9231dee2961ee02bac745d9ca71cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141600"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>Constructions diverses dans les expressions régulières
Les expressions régulières dans .NET incluent trois constructions de langage diverses. L’une d’elles vous permet d’activer ou de désactiver des options de mise en correspondance particulières au milieu d’un modèle d’expression régulière. Grâce aux deux autres, vous pouvez inclure des commentaires dans une expression régulière.  
  
## <a name="inline-options"></a>Options inline  
 Vous pouvez définir ou désactiver des options de mise en correspondance de modèle spécifiques pour une partie d’une expression régulière en utilisant la syntaxe suivante :  
  
`(?imnsx-imnsx)`  
  
 Vous répertoriez les options à activer après le point d’interrogation et les options à désactiver après le signe moins. Le tableau suivant décrit chaque option. Pour plus d’informations sur chaque option, consultez [Options des expressions régulières](../../../docs/standard/base-types/regular-expression-options.md).  
  
|Option|Description|  
|------------|-----------------|  
|`i`|Correspondance qui ne respecte pas la casse.|  
|`m`|Mode multiligne.|  
|`n`|Captures explicites uniquement. (Les parenthèses ne font pas office de groupes de capture.)|  
|`s`|Mode à ligne simple.|  
|`x`|Ignorer un espace blanc sans séquence d’échappement et autoriser les commentaires en mode x.|  
  
 Toute modification des options d’expression régulière définies par la construction `(?imnsx-imnsx)` reste en vigueur jusqu’à la fin du groupe englobant.  
  
> [!NOTE]
> La `(?imnsx-imnsx:`construction de`)` groupement *de sous-expression* fournit des fonctionnalités identiques pour une sous-expression. Pour plus d’informations, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 L’exemple suivant utilise les options `i`, `n` et `x` pour activer le non-respect de la casse et les captures explicites, et pour ignorer l’espace blanc dans le modèle d’expression régulière au milieu d’une expression régulière.  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 L’exemple définit deux expressions régulières. La première, `\b(D\w+)\s(d\w+)\b`, correspond à deux mots consécutifs qui commencent par un « D » majuscule et un « d » minuscule. La seconde expression régulière, `\b(D\w+)(?ixn) \s (d\w+) \b`, utilise des options inline pour modifier ce modèle, comme décrit dans le tableau suivant. Une comparaison des résultats confirme l’effet de la construction `(?ixn)`.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(D\w+)`|Mettre en correspondance un « D » majuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s’agit du premier groupe de capture.|  
|`(?ixn)`|À partir de ce point, effectuer des comparaisons sans respect de la casse, effectuer seulement des captures explicites et ignorer l’espace blanc dans le modèle d’expression régulière.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(d\w+)`|Mettre en correspondance un « d » majuscule ou minuscule suivi d’un ou de plusieurs caractères alphabétiques. Ce groupe n’est pas capturé, car l’option `n` (capture explicite) a été activée.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
  
## <a name="inline-comment"></a>Commentaire inline  
 La `(?#` construction *de commentaires* `)` vous permet d’inclure un commentaire en ligne dans une expression régulière. Le moteur d’expression régulière n’utilise aucune partie du commentaire dans la mise en correspondance du modèle, bien que le commentaire soit inclus dans la chaîne retournée par la méthode <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType>. Le commentaire se termine à la première parenthèse fermante.  
  
 L’exemple suivant répète le premier modèle d’expression régulière de l’exemple de la section précédente. Il ajoute deux commentaires inline à l’expression régulière pour indiquer si la comparaison respecte la casse. Le modèle d’expression régulière, `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`, est défini comme suit.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\b`|Commencer à la limite d'un mot.|  
|`(?# case-sensitive comparison)`|Commentaire. Il n’affecte pas le comportement de mise correspondance du modèle.|  
|`(D\w+)`|Mettre en correspondance un « D » majuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s'agit du premier groupe de capture.|  
|`\s`|Mettre en correspondance un espace blanc.|  
|`(?ixn)`|À partir de ce point, effectuer des comparaisons sans respect de la casse, effectuer seulement des captures explicites et ignorer l’espace blanc dans le modèle d’expression régulière.|  
|`(?#case-insensitive comparison)`|Commentaire. Il n’affecte pas le comportement de mise correspondance du modèle.|  
|`(d\w+)`|Mettre en correspondance un « d » majuscule ou minuscule suivi d’un ou de plusieurs caractères alphabétiques. Il s’agit du deuxième groupe de capture.|  
|`\b`|Mettre en correspondance la limite d'un mot.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>Commentaire de fin de ligne  
 Un signe dièse (`#`) marque un commentaire en mode x, lequel démarre au caractère # sans séquence d’échappement à la fin du modèle d’expression régulière et continue jusqu’à la fin de la ligne. Pour utiliser cette construction, vous devez activer l’option `x` (par le biais d’options inline) ou fournir la valeur <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> au paramètre `option` au moment de l’instanciation de l’objet <xref:System.Text.RegularExpressions.Regex> ou de l’appel de la méthode <xref:System.Text.RegularExpressions.Regex> statique.  
  
 L’exemple suivant illustre la construction du commentaire de fin de ligne. Il détermine si une chaîne est une chaîne de format composite qui inclut au moins un élément de format. Le tableau suivant décrit les constructions dans le modèle d’expression régulière :  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|Modèle|Description|  
|-------------|-----------------|  
|`\{`|Mettre en correspondance une accolade ouvrante.|  
|`\d+`|Mettre en correspondance un ou plusieurs chiffres décimaux.|  
|`(,-*\d+)*`|Mettre en correspondance zéro ou une occurrence d’une virgule, suivie d’un signe moins facultatif, suivi par un ou plusieurs chiffres décimaux.|  
|`(\:\w{1,4}?)*`|Mettre en correspondance zéro ou une occurrence d’un signe deux-points, suivi par un à quatre espaces blancs, mais le moins possible.|  
|`\}`|Mettre en correspondance une accolade fermante.|  
|`(?x)`|Activer l’option permettant d’ignorer l’espace blanc dans le modèle, afin que le commentaire de fin de ligne soit reconnu.|  
|`# Looks for a composite format item.`|Un commentaire de fin de ligne.|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 Notez que, au lieu de fournir la construction `(?x)` dans l’expression régulière, le commentaire aurait également pu être reconnu en appelant la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> et en lui passant la valeur d’énumération <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- [Langage d’expression régulière - Référence rapide](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
