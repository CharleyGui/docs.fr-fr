---
title: Comment modifier le contenu des cordes - Guide C
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 8e9bbe76c689d3c3f9f238ca9dd95cc7fcf98b18
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389516"
---
# <a name="how-to-modify-string-contents-in-c"></a>Comment modifier le contenu des cordes en C\#

Cet article présente plusieurs techniques pour produire un `string` en modifiant un `string` existant. Toutes les techniques présentées retournent le résultat des modifications sous la forme d’un nouvel objet `string`. Pour illustrer clairement ceci, tous les exemples stockent le résultat dans une nouvelle variable. Vous pouvez ensuite examiner le `string` d’origine et le `string` résultant de la modification quand vous exécutez chaque exemple.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Plusieurs techniques sont présentées dans cet article. Vous pouvez remplacer du texte existant. Vous pouvez rechercher des modèles et remplacer le texte correspondant par un autre texte. Vous pouvez traiter une chaîne en tant que séquence de caractères. Vous pouvez également utiliser des méthodes pratiques qui suppriment les espaces blancs. Choisissez les techniques qui correspondent le plus étroitement à votre scénario.

## <a name="replace-text"></a>Remplacer du texte

Le code suivant crée une chaîne en remplaçant le texte existant par un substitut.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Le code précédent illustre la propriété *immuable* des chaînes. Vous pouvez voir dans l’exemple précédent que la chaîne d’origine, `source`, n’est pas modifiée. La méthode <xref:System.String.Replace%2A?displayProperty=nameWithType> crée un `string` contenant les modifications.

La méthode <xref:System.String.Replace%2A> peut remplacer des chaînes ou des caractères uniques. Dans les deux cas, toutes les occurrences du texte recherché sont remplacées.  L’exemple suivant remplace tous les caractères ' ' par '\_' :

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

La chaîne source ne change pas, et une nouvelle chaîne est retournée avec le remplacement.

## <a name="trim-white-space"></a>Supprimer les espaces blancs

Vous pouvez utiliser les méthodes <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType> et <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> pour supprimer les espaces blancs de début ou de fin.  Le code suivant montre un exemple de chaque. La chaîne source ne change pas. Ces méthodes retournent une nouvelle chaîne avec le contenu modifié.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Supprimer du texte

Vous pouvez supprimer du texte d’une chaîne à l’aide de la méthode <xref:System.String.Remove%2A?displayProperty=nameWithType>. Cette méthode supprime un certain nombre de caractères en commençant à un index spécifique. L’exemple suivant montre comment utiliser <xref:System.String.IndexOf%2A?displayProperty=nameWithType> suivi de <xref:System.String.Remove%2A> pour supprimer le texte d’une chaîne :

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Remplacer du texte correspondant à un modèle

Vous pouvez utiliser des [expressions régulières](../../standard/base-types/regular-expressions.md) pour remplacer du texte correspondant à un modèle par un autre texte, éventuellement défini par un modèle. L’exemple suivant utilise la classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> pour trouver un modèle dans une chaîne source et le remplacer par du texte dont la casse est correcte. La méthode <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> accepte dans ses arguments une fonction qui fournit la logique du remplacement. Dans cet exemple, la fonction `LocalReplaceMatchCase` est une **fonction locale** déclarée à l’intérieur de l’exemple de méthode. `LocalReplaceMatchCase` utilise la classe <xref:System.Text.StringBuilder?displayProperty=nameWithType> pour générer la chaîne de remplacement avec la casse correcte.

Les expressions régulières sont plus utiles pour rechercher et remplacer du texte qui suit un modèle que du texte connu. Pour plus d’informations, voir [Comment rechercher des chaînes](search-strings.md). Le modèle de recherche, « the\s », recherche le mot « the » suivi d’un espace blanc. Cette partie du modèle permet d’exclure le mot « there » qui figure dans la chaîne source. Pour plus d’informations sur les éléments du langage des expressions régulières, consultez [Langage des expressions régulières - Aide-mémoire](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

La méthode <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> retourne une chaîne immuable avec le contenu dans l’objet <xref:System.Text.StringBuilder>.

## <a name="modifying-individual-characters"></a>Modification de caractères individuels

Vous pouvez générer un tableau de caractères à partir d’une chaîne, modifier le contenu du tableau, puis créer une autre chaîne à partir du contenu modifié du tableau.

L’exemple suivant montre comment remplacer un jeu de caractères dans une chaîne. Tout d’abord, il utilise la méthode <xref:System.String.ToCharArray?displayProperty=nameWithType> pour créer un tableau de caractères. Il utilise la méthode <xref:System.String.IndexOf%2A> pour trouver l’index de départ du mot « fox ». Les trois caractères suivants sont remplacés par un autre mot. Enfin, une nouvelle chaîne est construite à partir du tableau de caractères mis à jour.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Élaborer un contenu de chaîne programmatique

Étant donné que les cordes sont immuables, les exemples précédents créent tous des cordes temporaires ou des tableaux de personnages. Dans les scénarios de haute performance, il peut être souhaitable d’éviter ces allocations de tas. .NET Core <xref:System.String.Create%2A?displayProperty=nameWithType> fournit une méthode qui vous permet de remplir programmatiquement le contenu de caractères d’une chaîne via un rappel tout en évitant les allocations de chaînes temporaires intermédiaires.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Vous pouvez modifier une chaîne dans un bloc fixe avec un code dangereux, mais il est **fortement** déconseillé de modifier le contenu de la chaîne après la création d’une chaîne. Cela brisera les choses de façon imprévisible. Par exemple, si quelqu’un interne une chaîne qui a le même contenu que la vôtre, il recevra votre copie et ne s’attend pas du tout à modifier sa chaîne.

Vous pouvez essayer ces échantillons en regardant le code dans notre [référentiel GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Vous pouvez aussi télécharger les exemples [sous forme de fichier zip](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Voir aussi

- [Expressions régulières du .NET Framework](../../standard/base-types/regular-expressions.md)
- [Langage des expressions régulières - Aide-mémoire](../../standard/base-types/regular-expression-language-quick-reference.md)
