---
title: expression Switch-référence C#
description: Découvrez comment utiliser l’expression de commutateur C# pour les critères spéciaux et d’autres données d’inversion
ms.date: 01/14/2021
ms.openlocfilehash: 55fef8d351b178fd0ec23847e81e6c56eb1367b0
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536084"
---
# <a name="switch-expression-c-reference"></a>expression Switch (référence C#)

Cet article couvre l' `switch` expression, introduite dans C# 8,0. Pour plus d’informations sur l' `switch` instruction, consultez l’article sur l' [ `switch` instruction](../keywords/switch.md) dans la section [instructions](../keywords/index.md) .

## <a name="basic-example"></a>Exemple de base

L' `switch` expression fournit des `switch` sémantiques de type like dans un contexte d’expression. Il fournit une syntaxe concise lorsque les bras de commutateur produisent une valeur. L’exemple suivant illustre la structure d’une expression de commutateur. Il convertit les valeurs d’un `enum` qui représente les directions visuelles d’une carte en ligne vers la direction Cardinal correspondante :

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

L’exemple précédent montre les éléments de base d’une expression de commutateur :

- L' *expression de plage*: l’exemple précédent utilise la variable `direction` en tant qu’expression de plage.
- Les *branches d’expression de commutateur*: chaque ARM d’expression de commutateur contient un *modèle*, un *protecteur de cas* facultatif, le `=>` jeton et une *expression*.

Le résultat de l' *expression de commutateur* est la valeur de l’expression du premier *bras d’expression de commutateur* dont le *modèle* correspond à l' *expression de plage* et dont la protection de la *casse*, si elle est présente, prend la valeur `true` . L' *expression* à droite du `=>` jeton ne peut pas être une instruction d’expression.

Les *branches d’expression de commutateur* sont évaluées dans l’ordre de texte. Le compilateur émet une erreur quand une *expression de commutateur inférieure ARM* ne peut pas être sélectionnée, car une expression de commutateur supérieure *bras* correspond à toutes ses valeurs.

## <a name="patterns-and-case-guards"></a>Modèles et protecteurs de cas

De nombreux modèles sont pris en charge dans les branches d’expression de commutateur. L’exemple précédent utilise un *modèle de constante*. Un *modèle de constante* compare l’expression de plage à une valeur. Cette valeur doit être une constante au moment de la compilation. Le *modèle de type* compare l’expression de plage à un type connu. L’exemple suivant récupère le troisième élément d’une séquence. Elle utilise différentes méthodes basées sur le type de la séquence :

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetTypePattern":::

Les modèles peuvent être récursifs, où un modèle teste un type et si ce type correspond, le modèle correspond à une ou plusieurs valeurs de propriété sur l’expression de plage. Vous pouvez utiliser des modèles récursifs pour étendre l’exemple précédent. Vous ajoutez des branches d’expression de commutateur pour les tableaux qui contiennent moins de 3 éléments. Les modèles récursifs sont illustrés dans l’exemple suivant :

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Les modèles récursifs peuvent examiner les propriétés de l’expression de plage, mais ne peuvent pas exécuter du code arbitraire. Vous pouvez utiliser une *protection de cas*, spécifiée dans une `when` clause, pour fournir des vérifications similaires pour d’autres types de séquences :

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetGuardCase":::

Enfin, vous pouvez ajouter le `_` modèle et le `null` modèle pour intercepter les arguments qui ne sont pas traités par une autre branche d’expression de commutateur. Cela rend l’expression de commutateur *exhaustive*, ce qui signifie que toute valeur possible de l’expression de plage est gérée. L’exemple suivant ajoute ces bras d’expression :

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetExhaustive":::

L’exemple précédent ajoute un `null` modèle et remplace le `IEnumerable<T>` modèle de type par un `_` modèle. Le `null` modèle fournit une vérification null en tant qu’expression de commutateur ARM. L’expression pour ce ARM lève une <xref:System.ArgumentNullException> . Le `_` modèle correspond à toutes les entrées qui n’ont pas été mises en correspondance avec des bras précédents. Elle doit être postérieure `null` à la vérification ou correspondre aux `null` entrées.

## <a name="non-exhaustive-switch-expressions"></a>Expressions de commutateur non exhaustives

Si aucun des modèles d’une expression de commutateur n’intercepte un argument, le runtime lève une exception. Dans .NET Core 3,0 et versions ultérieures, l’exception est <xref:System.Runtime.CompilerServices.SwitchExpressionException?displayProperty=nameWithType> . Dans .NET Framework, l’exception est un <xref:System.InvalidOperationException> .

## <a name="see-also"></a>Voir aussi

- [Proposition de spécifications du langage C# pour les modèles récursifs](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)
- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [Critères spéciaux](../../pattern-matching.md)
