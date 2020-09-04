---
title: Comment modifier le contenu d’une chaîne-Guide C#
description: Passez en revue des exemples de différentes techniques pour modifier le contenu des chaînes existantes en C#, qui retournent un nouvel objet String.
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: bae54757fdb6f02cdc0dc8fc15ad3f7583c230a7
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465050"
---
# <a name="how-to-modify-string-contents-in-c"></a>Comment modifier le contenu d’une chaîne en C\#

Cet article présente plusieurs techniques pour produire un `string` en modifiant un `string` existant. Toutes les techniques présentées retournent le résultat des modifications sous la forme d’un nouvel objet `string`. Pour démontrer que les chaînes d’origine et modifiées sont des instances distinctes, les exemples stockent le résultat dans une nouvelle variable. Vous pouvez examiner les originaux `string` et les nouveaux, modifiés `string` lorsque vous exécutez chaque exemple.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Plusieurs techniques sont présentées dans cet article. Vous pouvez remplacer du texte existant. Vous pouvez rechercher des modèles et remplacer le texte correspondant par un autre texte. Vous pouvez traiter une chaîne en tant que séquence de caractères. Vous pouvez également utiliser des méthodes pratiques qui suppriment les espaces blancs. Choisissez les techniques qui correspondent le mieux à votre scénario.

## <a name="replace-text"></a>Remplacer du texte

Le code suivant crée une chaîne en remplaçant le texte existant par un substitut.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet1":::

Le code précédent illustre la propriété *immuable* des chaînes. Vous pouvez voir dans l’exemple précédent que la chaîne d’origine, `source`, n’est pas modifiée. La méthode <xref:System.String.Replace%2A?displayProperty=nameWithType> crée un `string` contenant les modifications.

La méthode <xref:System.String.Replace%2A> peut remplacer des chaînes ou des caractères uniques. Dans les deux cas, toutes les occurrences du texte recherché sont remplacées.  L’exemple suivant remplace tous les caractères ' ' par '\_' :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet2":::

La chaîne source ne change pas, et une nouvelle chaîne est retournée avec le remplacement.

## <a name="trim-white-space"></a>Supprimer les espaces blancs

Vous pouvez utiliser les méthodes <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType> et <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> pour supprimer les espaces blancs de début ou de fin.  Le code suivant montre un exemple de chaque. La chaîne source ne change pas. Ces méthodes retournent une nouvelle chaîne avec le contenu modifié.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet3":::

## <a name="remove-text"></a>Supprimer du texte

Vous pouvez supprimer du texte d’une chaîne à l’aide de la méthode <xref:System.String.Remove%2A?displayProperty=nameWithType>. Cette méthode supprime un certain nombre de caractères en commençant à un index spécifique. L’exemple suivant montre comment utiliser <xref:System.String.IndexOf%2A?displayProperty=nameWithType> suivi de <xref:System.String.Remove%2A> pour supprimer le texte d’une chaîne :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet4":::

## <a name="replace-matching-patterns"></a>Remplacer du texte correspondant à un modèle

Vous pouvez utiliser des [expressions régulières](../../standard/base-types/regular-expressions.md) pour remplacer du texte correspondant à un modèle par un autre texte, éventuellement défini par un modèle. L’exemple suivant utilise la classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> pour trouver un modèle dans une chaîne source et le remplacer par du texte dont la casse est correcte. La méthode <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> accepte dans ses arguments une fonction qui fournit la logique du remplacement. Dans cet exemple, la fonction `LocalReplaceMatchCase` est une **fonction locale** déclarée à l’intérieur de l’exemple de méthode. `LocalReplaceMatchCase` utilise la classe <xref:System.Text.StringBuilder?displayProperty=nameWithType> pour générer la chaîne de remplacement avec la casse correcte.

Les expressions régulières sont plus utiles pour rechercher et remplacer du texte qui suit un modèle que du texte connu. Pour plus d’informations, consultez [Comment rechercher des chaînes](search-strings.md). Le modèle de recherche, « the\s », recherche le mot « the » suivi d’un espace blanc. Cette partie du modèle permet d’exclure le mot « there » qui figure dans la chaîne source. Pour plus d’informations sur les éléments du langage des expressions régulières, consultez [Langage des expressions régulières - Aide-mémoire](../../standard/base-types/regular-expression-language-quick-reference.md).

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet5":::

La méthode <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> retourne une chaîne immuable avec le contenu dans l’objet <xref:System.Text.StringBuilder>.

## <a name="modifying-individual-characters"></a>Modification de caractères individuels

Vous pouvez générer un tableau de caractères à partir d’une chaîne, modifier le contenu du tableau, puis créer une autre chaîne à partir du contenu modifié du tableau.

L’exemple suivant montre comment remplacer un jeu de caractères dans une chaîne. Tout d’abord, il utilise la méthode <xref:System.String.ToCharArray?displayProperty=nameWithType> pour créer un tableau de caractères. Il utilise la méthode <xref:System.String.IndexOf%2A> pour trouver l’index de départ du mot « fox ». Les trois caractères suivants sont remplacés par un autre mot. Enfin, une nouvelle chaîne est construite à partir du tableau de caractères mis à jour.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet6":::

## <a name="programmatically-build-up-string-content"></a>Créer un contenu de chaîne par programmation

Étant donné que les chaînes sont immuables, les exemples précédents créent tous des chaînes temporaires ou des tableaux de caractères. Dans les scénarios à hautes performances, il peut être souhaitable d’éviter ces allocations de tas. .NET Core fournit une <xref:System.String.Create%2A?displayProperty=nameWithType> méthode qui vous permet de remplir par programmation le contenu de caractères d’une chaîne via un rappel tout en évitant les allocations de chaînes temporaires intermédiaires.

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet7":::

Vous pouvez modifier une chaîne dans un bloc fixed avec du code unsafe, mais il est **fortement** déconseillé de modifier le contenu de la chaîne après la création d’une chaîne. Cela entraînera une rupture des choses de manière imprévisible. Par exemple, si quelqu’un effectue une chaîne qui a le même contenu que le vôtre, il obtient votre copie et ne s’attend pas à ce que vous modifiiez sa chaîne.

## <a name="see-also"></a>Voir aussi

- [Expressions régulières .NET](../../standard/base-types/regular-expressions.md)
- [Langage des expressions régulières-aide-mémoire](../../standard/base-types/regular-expression-language-quick-reference.md)
