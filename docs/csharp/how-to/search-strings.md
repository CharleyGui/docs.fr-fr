---
title: Comment rechercher des chaînes (Guide C#)
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: f3e6d95eb4a01d48fac5b5e2c951b9c346206004
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121492"
---
# <a name="how-to-search-strings"></a>Comment rechercher des chaînes

Vous pouvez utiliser deux stratégies principales pour rechercher du texte dans des chaînes. Les méthodes de la classe <xref:System.String> recherchent un texte spécifique. Les expressions régulières recherchent des modèles dans du texte.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Le type [string](../language-reference/builtin-types/reference-types.md#the-string-type), qui est un alias de la classe <xref:System.String?displayProperty=nameWithType>, propose un certain nombre de méthodes utiles pour rechercher le contenu d’une chaîne. En voici quelques-unes : <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>. La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> fournit un vocabulaire étendu pour rechercher des modèles dans du texte. Dans cet article, vous découvrez ces techniques et comment choisir la meilleure méthode pour vos besoins.

## <a name="does-a-string-contain-text"></a>Une chaîne contient-elle un certain texte ?

Les méthodes <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> et <xref:System.String.EndsWith%2A?displayProperty=nameWithType> recherchent un texte spécifique dans une chaîne. L’exemple suivant montre chacune de ces méthodes et une variante qui utilise une recherche sans respecter la casse :

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

L’exemple précédent montre un point important de l’utilisation de ces méthodes. Par défaut, les recherches **respectent la casse**. Vous utilisez la valeur d’énumération <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> pour spécifier une recherche qui ne respecte pas la casse.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Où le texte recherché se trouve-t-il dans une chaîne ?

Les méthodes <xref:System.String.IndexOf%2A> et <xref:System.String.LastIndexOf%2A> recherchent aussi du texte dans des chaînes. Ces méthodes retournent l’emplacement du texte recherché. Si le texte n’est pas trouvé, elles retournent `-1`. L’exemple suivant montre une recherche de la première et de la dernière occurrence du mot « methods » et affiche le texte qui se trouve entre les deux.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Recherche de texte spécifique en utilisant des expressions régulières

La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> permet d’effectuer des recherches de chaînes. Ces recherches peuvent varier en complexité et aller de modèles simples à des modèles plus compliqués.

L’exemple de code suivant recherche le mot « the » ou « their » dans une phrase, indépendamment de la casse. La méthode statique <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> effectue la recherche. Vous lui passez la chaîne à rechercher et un modèle de recherche. Dans ce cas, un troisième argument spécifie que la recherche est insensible à la casse. Pour plus d’informations, consultez <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Le modèle de recherche décrit le texte que vous recherchez. Le tableau suivant décrit chaque élément du modèle de recherche. (Le tableau ci-dessous utilise une barre oblique inversée [`\`] qui, dans une chaîne C#, doit être précédée d’un caractère d’échappement sous la forme `\\`).

| modèle  | Signification     |
| -------- |-------------|
| le      | correspond au texte « the » |
| (eir)?   | correspond à 0 ou 1 occurrence de « eir » |
| \s       | correspond à un espace blanc    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> Les méthodes `string` sont généralement de meilleurs choix quand vous recherchez une chaîne précise. Les expressions régulières sont mieux adaptées lorsque vous recherchez un modèle dans une chaîne source.

## <a name="does-a-string-follow-a-pattern"></a>Une chaîne suit-elle un modèle ?

Le code suivant utilise des expressions régulières pour valider le format de chaque chaîne d’un tableau. La validation doit vérifier que chaque chaîne a la forme d’un numéro de téléphone constitué de trois groupes de chiffres séparés par des tirets, les deux premiers groupes contenant trois chiffres et le troisième en contenant quatre. Le modèle de recherche utilise l’expression régulière `^\\d{3}-\\d{3}-\\d{4}$`. Pour plus d’informations, consultez [Langage des expressions régulières - Aide-mémoire](../../standard/base-types/regular-expression-language-quick-reference.md).

| modèle  | Signification                             |
| -------- |-------------------------------------|
| ^        | correspond au début de la chaîne |
| \d{3}    | correspond à exactement 3 caractères numériques  |
| -        | correspond au caractère « - ».           |
| \d{3}    | correspond à exactement 3 caractères numériques  |
| -        | correspond au caractère « - ».           |
| \d{4}    | correspond à exactement 4 caractères numériques  |
| $        | correspond à la fin de la chaîne       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Ce seul modèle de recherche correspond à de nombreuses chaînes valides. Les expressions régulières sont mieux adaptées pour rechercher un modèle ou pour effectuer une validation par rapport à un modèle, et le sont moins pour une seule chaîne de texte.

Vous pouvez essayer ces exemples en examinant le code dans notre [référentiel GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Vous pouvez aussi télécharger les exemples [sous forme de fichier zip](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../programming-guide/index.md)
- [Chaînes](../programming-guide/strings/index.md)
- [LINQ et chaînes](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Expressions régulières du .NET Framework](../../standard/base-types/regular-expressions.md)
- [Langage des expressions régulières - Aide-mémoire](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Bonnes pratiques pour l’utilisation de chaînes dans .NET](../../standard/base-types/best-practices-strings.md)
