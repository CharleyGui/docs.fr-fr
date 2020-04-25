---
title: expression Switch-référence C#
description: Découvrez comment utiliser l’expression de commutateur C# pour les critères spéciaux et d’autres données d’inversion
ms.date: 03/19/2020
ms.openlocfilehash: f53cbe873c841271f64496e4e5ff1f11750c7b8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140663"
---
# <a name="switch-expression-c-reference"></a>expression Switch (référence C#)

Cet article couvre l' `switch` expression, introduite dans C# 8,0. Pour plus d’informations `switch` sur l’instruction, consultez l’article sur l' [ `switch` instruction](../keywords/switch.md) dans la section [instructions](../keywords/index.md) .

## <a name="basic-example"></a>Exemple de base

L' `switch` expression fournit des `switch`sémantiques de type like dans un contexte d’expression. Il fournit une syntaxe concise lorsque les bras de commutateur produisent une valeur. L’exemple suivant illustre la structure d’une expression de commutateur. Il convertit les valeurs d' `enum` un qui représente les directions visuelles d’une carte en ligne vers la direction Cardinal correspondante :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

L’exemple précédent montre les éléments de base d’une expression de commutateur :

- L' *expression de plage*: l’exemple précédent utilise la `direction` variable en tant qu’expression de plage.
- Les *branches d’expression de commutateur*: chaque ARM d’expression de commutateur contient un *modèle*, un protecteur `=>` de *cas*facultatif, le jeton et une *expression*.

Le résultat de l' *expression de commutateur* est la valeur de l’expression du premier *bras d’expression de commutateur* dont le *modèle* correspond à l' *expression de plage* et dont la protection de la `true` *casse*, si elle est présente, prend la valeur. L' *expression* à droite du `=>` jeton ne peut pas être une instruction d’expression.

Les *branches d’expression de commutateur* sont évaluées dans l’ordre de texte. Le compilateur émet une erreur quand une *expression de commutateur inférieure ARM* ne peut pas être sélectionnée, car une expression de commutateur supérieure *bras* correspond à toutes ses valeurs.

## <a name="patterns-and-case-guards"></a>Modèles et protecteurs de cas

De nombreux modèles sont pris en charge dans les branches d’expression de commutateur. L’exemple précédent utilisait un *modèle de valeur*. Un *modèle de valeur* compare l’expression de plage à une valeur. Cette valeur doit être une constante au moment de la compilation. Le *modèle de type* compare l’expression de plage à un type connu. L’exemple suivant récupère le troisième élément d’une séquence. Elle utilise différentes méthodes basées sur le type de la séquence :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Les modèles peuvent être récursifs, où un modèle teste un type et si ce type correspond, le modèle correspond à une ou plusieurs valeurs de propriété sur l’expression de plage. Vous pouvez utiliser des modèles récursifs pour étendre l’exemple précédent. Vous ajoutez des branches d’expression de commutateur pour les tableaux qui contiennent moins de 3 éléments. Les modèles récursifs sont illustrés dans l’exemple suivant :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Les modèles récursifs peuvent examiner les propriétés de l’expression de plage, mais ne peuvent pas exécuter du code arbitraire. Vous pouvez utiliser une *protection de cas*, spécifiée dans `when` une clause, pour fournir des vérifications similaires pour d’autres types de séquences :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Enfin, vous pouvez ajouter le `_` modèle et le `null` modèle pour intercepter les arguments qui ne sont pas traités par une autre branche d’expression de commutateur. Cela rend l’expression de commutateur *exhaustive*, ce qui signifie que toute valeur possible de l’expression de plage est gérée. L’exemple suivant ajoute ces bras d’expression :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

L’exemple précédent ajoute un `null` modèle et remplace le `IEnumerable<T>` modèle de type par un `_` modèle. Le `null` modèle fournit une vérification null en tant qu’expression de commutateur ARM. L’expression pour ce ARM lève une <xref:System.ArgumentNullException>. Le `_` modèle correspond à toutes les entrées qui n’ont pas été mises en correspondance avec des bras précédents. Elle doit être postérieure `null` à la vérification ou correspondre aux `null` entrées.

Pour plus d’informations, consultez la proposition de spécifications du langage C# pour les [modèles récursifs](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs C#](index.md)
- [Critères spéciaux](../../pattern-matching.md)
