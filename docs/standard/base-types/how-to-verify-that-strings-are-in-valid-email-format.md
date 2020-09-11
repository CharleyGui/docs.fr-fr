---
title: Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide
description: Lire un exemple de la façon dont une expression régulière vérifie que les chaînes sont dans un format d’adresse de messagerie valide dans .NET.
ms.date: 06/30/2020
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
ms.openlocfilehash: 90e79af649727330c2afa1ccb8c64ffe34733f92
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022946"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide

L'exemple suivant utilise une expression régulière pour vérifier qu'une chaîne est dans un format d'adresse e-mail valide.

Cette expression régulière est relativement simple à ce qui peut être utilisé en tant qu’e-mail. L’utilisation d’une expression régulière pour valider un message électronique est utile pour s’assurer que la structure d’un message électronique est correcte, mais il ne s’agit pas d’une substitution pour vérifier que le courrier électronique existe réellement.

✔️ Utilisez une petite expression régulière pour vérifier la structure valide d’un e-mail.

✔️ Envoyer un message électronique de test à l’adresse fournie par un utilisateur de votre application.

❌ N’utilisez pas une expression régulière comme seule façon de valider un e-mail.

Si vous essayez de créer l’expression régulière _parfaite_ pour valider que la structure d’un message électronique est correcte, l’expression devient tellement complexe qu’il est incroyablement difficile de déboguer ou d’améliorer. Les expressions régulières ne peuvent pas valider l’existence d’un courrier électronique, même s’il est correctement structuré. La meilleure façon de valider un e-mail consiste à envoyer un e-mail de test à l’adresse.

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>Exemple

L’exemple définit une `IsValidEmail` méthode qui retourne `true` si la chaîne contient une adresse de messagerie valide et, `false` si elle ne l’est pas, n’effectue aucune autre action.

Pour vérifier que l'adresse de messagerie est valide, la méthode `IsValidEmail` appelle la méthode <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> avec le modèle d'expression régulière `(@)(.+)$` pour séparer le nom de domaine de l'adresse de messagerie. Le troisième paramètre est un délégué <xref:System.Text.RegularExpressions.MatchEvaluator> qui représente la méthode qui traite et remplace le texte correspondant. Le modèle d'expression régulière est interprété comme suit.

| Modèle | Description                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | Correspond à l'arobase (@). Cette partie est le premier groupe de capture.                           |
| `(.+)`  | Correspond à une ou plusieurs occurrences d'un caractère quelconque. Cette partie est le deuxième groupe de capture. |
| `$`     | Termine la correspondance à la fin de la chaîne.                                             |

Le nom de domaine avec le caractère @ est passé à la méthode `DomainMapper` , qui utilise la classe <xref:System.Globalization.IdnMapping> pour convertir les caractères Unicode situés en dehors de la plage de caractères US-ASCII au format Punycode. La méthode affecte également à l'indicateur `invalid` la valeur `True` si la méthode <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> détecte des caractères non valides dans le nom de domaine. La méthode retourne le nom de domaine Punycode précédé du symbole @ à la méthode `IsValidEmail` .

> [!TIP]
> Il est recommandé d’utiliser le `(@)(.+)$` modèle d’expression régulière simple pour normaliser le domaine, puis retourner une valeur indiquant qu’il a réussi ou échoué. Toutefois, l’exemple de cet article explique comment utiliser une expression régulière pour valider l’e-mail. Quelle que soit la façon dont vous validez un e-mail, vous devez toujours envoyer un e-mail de test à l’adresse pour vous assurer qu’il existe.

La méthode `IsValidEmail` appelle alors la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> pour vérifier que l'adresse est conforme à un modèle d'expression régulière.

La `IsValidEmail` méthode détermine simplement si le format d’e-mail est valide pour une adresse de messagerie, mais ne valide pas l’existence de l’e-mail. En outre, la `IsValidEmail` méthode ne vérifie pas si le nom de domaine de niveau supérieur est un nom de domaine valide figurant dans la [base de données de zone racine IANA](https://www.iana.org/domains/root/db), ce qui nécessite une opération de recherche.

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

Dans cet exemple, le modèle d’expression régulière `^[^@\s]+@[^@\s]+\.[^@\s]+$` est interprété de la manière indiquée dans le tableau ci-dessous. L’expression régulière est compilée à l’aide de l' <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> indicateur.

| Modèle   | Description                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | Commence la recherche de correspondance au début de la chaîne.                                              |
| `[^@\s]+` | Correspond à une ou plusieurs occurrences d’un caractère autre que le caractère @ ou l’espace blanc. |
| `@`       | Correspond à l'arobase (@).                                                                   |
| `[^@\s]+` | Correspond à une ou plusieurs occurrences d’un caractère autre que le caractère @ ou l’espace blanc. |
| `\.`      | Correspond à un caractère à point unique.                                                         |
| `[^@\s]+` | Correspond à une ou plusieurs occurrences d’un caractère autre que le caractère @ ou l’espace blanc. |
| `$`       | Termine la correspondance à la fin de la chaîne.                                                  |

> [!IMPORTANT]
> Cette expression régulière n’est pas destinée à couvrir tous les aspects d’une adresse de messagerie valide. Il est fourni comme exemple pour que vous l’étendiez si nécessaire.

## <a name="see-also"></a>Voir aussi

- [Expressions régulières du .NET Framework](regular-expressions.md)
- [Quelle est la durée d’une validation d’adresse de messagerie ?](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
