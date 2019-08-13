---
title: "Procédure : vérifier que des chaînes sont dans un format d'adresse de messagerie valide"
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6381747bc998f73b374442fcb15e025ca15795d
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2019
ms.locfileid: "65589525"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Procédure : vérifier que des chaînes sont dans un format d'adresse de messagerie valide
L'exemple suivant utilise une expression régulière pour vérifier qu'une chaîne est dans un format d'adresse de messagerie valide.  

## <a name="example"></a>Exemples  
 L'exemple définit une méthode `IsValidEmail` qui retourne la valeur `true` si la chaîne contient une adresse de messagerie valide et la valeur `false` dans le cas contraire, mais qui n'effectue aucune autre action.  
  
 Pour vérifier que l'adresse de messagerie est valide, la méthode `IsValidEmail` appelle la méthode <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> avec le modèle d'expression régulière `(@)(.+)$` pour séparer le nom de domaine de l'adresse de messagerie. Le troisième paramètre est un délégué <xref:System.Text.RegularExpressions.MatchEvaluator> qui représente la méthode qui traite et remplace le texte correspondant. Le modèle d'expression régulière est interprété comme suit.  
  
|Motif|Description|  
|-------------|-----------------|  
|`(@)`|Correspond à l'arobase (@). Il s'agit du premier groupe de capture.|  
|`(.+)`|Correspond à une ou plusieurs occurrences d'un caractère quelconque. Il s'agit du deuxième groupe de capture.|  
|`$`|Termine la correspondance à la fin de la chaîne.|  
  
 Le nom de domaine avec le caractère @ est passé à la méthode `DomainMapper` , qui utilise la classe <xref:System.Globalization.IdnMapping> pour convertir les caractères Unicode situés en dehors de la plage de caractères US-ASCII au format Punycode. La méthode affecte également à l'indicateur `invalid` la valeur `True` si la méthode <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> détecte des caractères non valides dans le nom de domaine. La méthode retourne le nom de domaine Punycode précédé du symbole @ à la méthode `IsValidEmail` .  
  
 La méthode `IsValidEmail` appelle alors la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> pour vérifier que l'adresse est conforme à un modèle d'expression régulière.  
  
 Notez que la méthode `IsValidEmail` n'effectue pas d'authentification pour valider l'adresse de messagerie. Elle détermine simplement si son format est valide pour une adresse de messagerie. En outre, la méthode `IsValidEmail` ne vérifie pas si le nom de domaine de premier niveau est un nom de domaine valide répertorié dans la [base de données des zones racines de l’IANA](https://www.iana.org/domains/root/db). Cela nécessite une opération de recherche. À la place, l'expression régulière vérifie simplement que le nom de domaine de niveau supérieur comprend entre deux et vingt-quatre caractères ASCII, les premier et dernier caractères étant des caractères alphanumériques, les autres des caractères alphanumériques ou un trait d'union (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 Dans cet exemple, le modèle d’expression régulière ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` est interprété de la manière indiquée dans le tableau ci-dessous. Notez que l'expression régulière est compilée à l'aide de l'indicateur <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> .  
  
|Motif|Description|  
|-------------|-----------------|  
|`^`|Commence la recherche de correspondance au début de la chaîne.|  
|`(?(")`|Détermine si le premier caractère est un guillemet. `(?(")` est le début d'une construction d'alternative.|  
|`(?("")("".+?(?<!\\)""@)`|Si le premier caractère correspond à des guillemets, établit une correspondance avec des guillemets ouvrants suivis d'au moins une occurrence d'un caractère quelconque, suivie de guillemets fermants. Les guillemets fermants ne doivent pas être précédés d'une barre oblique inverse (\\). `(?<!` est le début d'une assertion de postanalyse négative de largeur nulle. La chaîne doit se terminer par un arobase (@).|  
|<code>&#124;(([0-9a-z]</code>|Si le premier caractère n'est pas un guillemet, établit une correspondance avec un caractère alphabétique de a à z ou de A à Z (la comparaison ne respecte pas la casse) ou un chiffre (de 0 à 9).|  
|`(\.(?!\.))`|Si le caractère suivant est un point, établit une correspondance avec un point. Dans le cas contraire, effectue une préanalyse du caractère suivant et continue la recherche de correspondances. `(?!\.)` est une assertion de préanalyse négative de largeur nulle qui empêche deux points consécutifs de s'afficher dans la partie locale d'une adresse de messagerie.|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}&#124;~\w]</code>|Si le caractère suivant n’est pas un point, établit une correspondance avec un caractère alphabétique quelconque ou avec un des caractères suivants : -!#$%'*+=?^\`{}&#124;~.|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}&#124;~\w])*</code>|Établit une correspondance avec le modèle d'alternative (un point suivi d'un autre caractère qu'un point, ou l'un des caractères) zéro, une ou plusieurs fois.|  
|`@`|Correspond à l'arobase (@).|  
|`(?<=[0-9a-z])`|Continue la recherche de correspondances si le caractère qui précède le caractère @ est compris entre A et Z, a et z, ou 0 et 9. La construction `(?<=[0-9a-z])` définit une assertion de postanalyse positive de largeur nulle.|  
|`(?(\[)`|Vérifie si le caractère qui suit @ est un crochet ouvrant.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|S'il s'agit d'un crochet ouvrant, établit une correspondance avec le crochet ouvrant suivi d'une adresse IP (quatre ensembles de un à trois chiffres, chaque ensemble étant séparé par un point) et d'un crochet fermant.|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|Si le caractère qui suit @ n'est pas un crochet ouvrant, établit une correspondance avec un caractère alphanumérique ayant une valeur comprise entre A et Z, a et z ou 0 et 9, suivi de zéro, une ou plusieurs occurrences d'un trait d'union, suivi de zéro, un ou plusieurs caractères alphanumériques ayant une valeur comprise entre A et Z, a et z ou 0 et 9, suivi d'un point. Ce modèle peut être répété une ou plusieurs fois et doit être suivi du nom de domaine de niveau supérieur.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Le nom de domaine de niveau supérieur doit commencer et se terminer par un caractère alphanumérique (compris entre a et z, A et Z ou 0 et 9). Il peut également comprendre entre zéro et 22 caractères ASCII (soit des caractères alphanumériques, soit des traits d'union).|  
|`$`|Termine la correspondance à la fin de la chaîne.|  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Les méthodes `IsValidEmail` et `DomainMapper` peuvent être incluses dans une bibliothèque de méthodes utilitaires d'expression régulière ou peuvent être incluses en tant que méthodes d'instance ou statiques privées dans la classe d'application.  
  
 Vous pouvez également utiliser la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> pour inclure cette expression régulière dans une bibliothèque d'expressions régulières.  
  
 Si elles sont utilisées dans une bibliothèque d'expressions régulières, vous pouvez les appeler en utilisant un code semblable au suivant :  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
## <a name="see-also"></a>Voir aussi

- [.NET Framework (expressions régulières)](../../../docs/standard/base-types/regular-expressions.md)
