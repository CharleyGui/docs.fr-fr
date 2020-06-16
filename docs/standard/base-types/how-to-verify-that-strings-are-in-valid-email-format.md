---
title: Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide
description: Lire un exemple de la façon dont une expression régulière vérifie que les chaînes sont dans un format d’adresse de messagerie valide dans .NET.
ms.date: 12/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 47ef4dedd20a2b885abaabf72c26de5f3312c66f
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768961"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide

L'exemple suivant utilise une expression régulière pour vérifier qu'une chaîne est dans un format d'adresse e-mail valide.

## <a name="example"></a>Exemple

L'exemple définit une méthode `IsValidEmail` qui retourne la valeur `true` si la chaîne contient une adresse de messagerie valide et la valeur `false` dans le cas contraire, mais qui n'effectue aucune autre action.

Pour vérifier que l'adresse de messagerie est valide, la méthode `IsValidEmail` appelle la méthode <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> avec le modèle d'expression régulière `(@)(.+)$` pour séparer le nom de domaine de l'adresse de messagerie. Le troisième paramètre est un délégué <xref:System.Text.RegularExpressions.MatchEvaluator> qui représente la méthode qui traite et remplace le texte correspondant. Le modèle d'expression régulière est interprété comme suit.

|Modèle|Description|
|-------------|-----------------|
|`(@)`|Correspond à l'arobase (@). Il s'agit du premier groupe de capture.|
|`(.+)`|Correspond à une ou plusieurs occurrences d'un caractère quelconque. Il s'agit du deuxième groupe de capture.|
|`$`|Termine la correspondance à la fin de la chaîne.|

Le nom de domaine avec le caractère @ est passé à la méthode `DomainMapper` , qui utilise la classe <xref:System.Globalization.IdnMapping> pour convertir les caractères Unicode situés en dehors de la plage de caractères US-ASCII au format Punycode. La méthode affecte également à l'indicateur `invalid` la valeur `True` si la méthode <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> détecte des caractères non valides dans le nom de domaine. La méthode retourne le nom de domaine Punycode précédé du symbole @ à la méthode `IsValidEmail` .

La méthode `IsValidEmail` appelle alors la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> pour vérifier que l'adresse est conforme à un modèle d'expression régulière.

Notez que la méthode `IsValidEmail` n'effectue pas d'authentification pour valider l'adresse de messagerie. Elle détermine simplement si son format est valide pour une adresse de messagerie. En outre, la méthode `IsValidEmail` ne vérifie pas si le nom de domaine de premier niveau est un nom de domaine valide répertorié dans la [base de données des zones racines de l’IANA](https://www.iana.org/domains/root/db). Cela nécessite une opération de recherche. À la place, l'expression régulière vérifie simplement que le nom de domaine de niveau supérieur comprend entre deux et vingt-quatre caractères ASCII, les premier et dernier caractères étant des caractères alphanumériques, les autres des caractères alphanumériques ou un trait d'union (-).

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

Dans cet exemple, le modèle d’expression régulière ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` est interprété comme indiqué dans la légende suivante. L’expression régulière est compilée à l’aide de l' <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> indicateur.

Pattern `^` : commencer la correspondance au début de la chaîne.

Modèle `(?(")` : Déterminez si le premier caractère est un guillemet. `(?(")` est le début d'une construction d'alternative.

Pattern `(?(")(".+?(?<!\\)"@)` : si le premier caractère est un guillemet, mettre en correspondance un guillemet ouvrant suivi d’au moins une occurrence d’un caractère quelconque, suivi d’un guillemet fermant. Les guillemets fermants ne doivent pas être précédés d'une barre oblique inverse (\\). `(?<!` est le début d'une assertion de postanalyse négative de largeur nulle. La chaîne doit se terminer par un arobase (@).

Pattern `|(([0-9a-z]` : si le premier caractère n’est pas un guillemet, correspond à n’importe quel caractère alphabétique de a à z ou de a à z (la comparaison ne respecte pas la casse) ou n’importe quel caractère numérique compris entre 0 et 9.

Modèle `(\.(?!\.))` : si le caractère suivant est un point, associez-le. Dans le cas contraire, effectue une préanalyse du caractère suivant et continue la recherche de correspondances. `(?!\.)` est une assertion de préanalyse négative de largeur nulle qui empêche deux points consécutifs de s'afficher dans la partie locale d'une adresse de messagerie.

Modèle ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]`` : si le caractère suivant n’est pas un point, correspond à un caractère alphabétique ou à l’un des caractères suivants :- ! # $% & ' \* +/= ? ^ \` {} | ~

Modèle ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*`` : correspond au modèle d’alternative (un point suivi d’un autre que le point, ou un nombre de caractères) zéro, une ou plusieurs fois.

Modèle `@` : correspond au caractère @.

Modèle `(?<=[0-9a-z])` : continue la correspondance si le caractère qui précède le caractère @ est de a à z, de a à z ou de 0 à 9. Ce modèle définit une assertion de postanalyse positive de largeur nulle.

Pattern `(?(\[)` : Vérifiez si le caractère qui suit @ est un crochet ouvrant.

Modèle `(\[(\d{1,3}\.){3}\d{1,3}\])` : s’il s’agit d’un crochet ouvrant, établit une correspondance avec le crochet ouvrant suivi d’une adresse IP (quatre ensembles de un à trois chiffres, chaque ensemble étant séparé par un point) et d’un crochet fermant.

Modèle `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+` : si le caractère qui suit @ n’est pas un crochet ouvrant, correspond à un caractère alphanumérique avec la valeur a-z, a-z ou 0-9, suivi de zéro occurrence, ou plus, d’un trait d’Union, suivi de zéro ou d’un caractère alphanumérique avec la valeur a-z, a-z ou 0-9, suivi d’un point. Ce modèle peut être répété une ou plusieurs fois et doit être suivi du nom de domaine de niveau supérieur.

Modèle `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))` : le nom de domaine de niveau supérieur doit commencer et se terminer par un caractère alphanumérique (a-z, a-z et 0-9). Il peut également comprendre entre zéro et 22 caractères ASCII (soit des caractères alphanumériques, soit des traits d'union).

Pattern `$` : termine la correspondance à la fin de la chaîne.

## <a name="compile-the-code"></a>Compiler le code

Les méthodes `IsValidEmail` et `DomainMapper` peuvent être incluses dans une bibliothèque de méthodes utilitaires d'expression régulière ou peuvent être incluses en tant que méthodes d'instance ou statiques privées dans la classe d'application.

Vous pouvez également utiliser la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> pour inclure cette expression régulière dans une bibliothèque d'expressions régulières.

Si elles sont utilisées dans une bibliothèque d'expressions régulières, vous pouvez les appeler en utilisant un code semblable au suivant :

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Voir aussi

- [Expressions régulières du .NET Framework](regular-expressions.md)
