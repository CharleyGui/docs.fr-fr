---
title: Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide
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
ms.openlocfilehash: c02fc215fa66951ae3333175191ab96a226a2afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73197581"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide

L'exemple suivant utilise une expression régulière pour vérifier qu'une chaîne est dans un format d'adresse e-mail valide.

## <a name="example"></a> Exemple

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

Dans cet exemple, le ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` modèle d’expression régulière est interprété comme indiqué dans la légende suivante. L’expression régulière est <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> compilée à l’aide du drapeau.

Modèle `^`: Commencez le match au début de la chaîne.

Modèle `(?(")`: Déterminez si le premier personnage est une marque de citation. `(?(")` est le début d'une construction d'alternative.

Modèle `(?(")(".+?(?<!\\)"@)`: Si le premier personnage est une marque de citation, assortissez une marque de citation de début suivie d’au moins une occurrence de n’importe quel caractère, suivie d’une marque de citation finale. Les guillemets fermants ne doivent pas être précédés d'une barre oblique inverse (\\). `(?<!` est le début d'une assertion de postanalyse négative de largeur nulle. La chaîne doit se terminer par un arobase (@).

Modèle `|(([0-9a-z]`: Si le premier personnage n’est pas une marque de citation, faites correspondre n’importe quel personnage alphabétique d’un z ou de A à Z (la comparaison est insensible au cas), ou n’importe quel personnage numérique de 0 à 9.

Modèle `(\.(?!\.))`: Si le personnage suivant est une période, assortissez-la. Dans le cas contraire, effectue une préanalyse du caractère suivant et continue la recherche de correspondances. `(?!\.)` est une assertion de préanalyse négative de largeur nulle qui empêche deux points consécutifs de s'afficher dans la partie locale d'une adresse de messagerie.

Modèle ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: Si le personnage suivant n’est\*\`{}pas une période, faites correspondre n’importe quel personnage de mot ou l’un des caractères suivants : -&!

Modèle ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Assortissez le modèle d’alternance (une période suivie d’une non-période, ou l’un des nombreux caractères) à des temps nuls ou plus.

Modèle `@`: Match le caractère.

Modèle `(?<=[0-9a-z])`: Continuez le match si le personnage qui précède le personnage est A à Z, un z à travers, ou 0 à 9. Ce modèle définit une affirmation positive de lookbehind de largeur zéro.

Modèle `(?(\[)`: Vérifiez si le personnage qui suit est un support d’ouverture.

Modèle `(\[(\d{1,3}\.){3}\d{1,3}\])`: S’il s’agit d’un support d’ouverture, assortissez le support d’ouverture suivi d’une adresse IP (quatre séries d’un à trois chiffres, chaque ensemble séparé par une période) et d’un support de clôture.

Modèle `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: Si le personnage qui suit n’est pas un support d’ouverture, associez un personnage alphanumérique à une valeur de A-Z, a-z, ou 0-9, suivi de zéro ou plus d’occurrences d’un trait d’union, suivies d’un caractère alphanumérique nul ou d’un caractère alphanumérique d’une valeur de A-Z, a-z ou 0-9, suivi d’une période. Ce modèle peut être répété une ou plusieurs fois et doit être suivi du nom de domaine de niveau supérieur.

Modèle `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: Le nom de domaine de haut niveau doit commencer et se terminer par un caractère alphanumérique (a-z, A-Z et 0-9). Il peut également comprendre entre zéro et 22 caractères ASCII (soit des caractères alphanumériques, soit des traits d'union).

Modèle `$`: Fin du match à la fin de la chaîne.

## <a name="compile-the-code"></a>Compiler le code

Les méthodes `IsValidEmail` et `DomainMapper` peuvent être incluses dans une bibliothèque de méthodes utilitaires d'expression régulière ou peuvent être incluses en tant que méthodes d'instance ou statiques privées dans la classe d'application.

Vous pouvez également utiliser la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> pour inclure cette expression régulière dans une bibliothèque d'expressions régulières.

Si elles sont utilisées dans une bibliothèque d'expressions régulières, vous pouvez les appeler en utilisant un code semblable au suivant :

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a>Voir aussi

- [Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)
