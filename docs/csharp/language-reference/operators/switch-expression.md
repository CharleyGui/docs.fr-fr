---
title: expression de commutateur - référence de C
description: Apprenez à utiliser l’expression de commutateur CMD pour l’appariement des modèles et d’autres introspections de données
ms.date: 03/19/2020
ms.openlocfilehash: 9e609bcea0f92f492b5f9b07840e47f75c1b71e4
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249787"
---
# <a name="switch-expression-c-reference"></a>expression de commutateur (référence de C)

Cet article `switch` couvre l’expression, introduite dans C 8.0. Pour plus `switch` d’informations sur la déclaration, voir l’article sur la [ `switch` déclaration](../keywords/switch.md) dans la section [des déclarations.](../keywords/index.md)

## <a name="basic-example"></a>Exemple de base

L’expression `switch` `switch`prévoit -comme la sémantique dans un contexte d’expression. Il fournit une syntaxe concise lorsque les bras de commutation produisent une valeur. L’exemple suivant montre la structure d’une expression de commutateur. Il traduit les `enum` valeurs d’une direction visuelle représentante dans une carte en ligne à la direction cardinale correspondante :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

L’échantillon précédent montre les éléments de base d’une expression de commutateur :

- *L’expression de gamme*: `direction` L’exemple précédent utilise la variable comme expression de gamme.
- Les *bras d’expression de commutateur*: Chaque bras d’expression de commutateur contient un *modèle,* un garde de *cas*optionnel, le `=>` jeton, et une *expression.*

Le résultat de l’expression *de commutateur* est la valeur de l’expression du premier *bras d’expression de commutateur* dont le *modèle* correspond à l’expression de *la gamme* et dont la garde *de cause,* si elle est présente, évalue à `true`. *L’expression* `=>` à droite du jeton ne peut pas être une déclaration d’expression.

Les *bras d’expression de commutateur* sont évalués dans l’ordre de texte. Le compilateur émet une erreur lorsqu’un *bras d’expression de commutateur* inférieur ne peut pas être choisi parce qu’un bras *d’expression de commutateur* plus élevé correspond à toutes ses valeurs.

## <a name="patterns-and-case-guards"></a>Modèles et gardiens de cas

De nombreux modèles sont soutenus dans les bras d’expression de commutateur. L’exemple précédent a utilisé un *modèle de valeur*. Un *modèle de valeur* compare l’expression de la gamme à une valeur. Cette valeur doit être une constante de temps de compilation. Le *modèle de type* compare l’expression de gamme à un type connu. L’exemple suivant récupère le troisième élément d’une séquence. Il utilise différentes méthodes basées sur le type de séquence :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Les modèles peuvent être récursifs, lorsqu’un modèle teste un type, et si ce type correspond, le modèle correspond à une ou plusieurs valeurs de propriété sur l’expression de la gamme. Vous pouvez utiliser des modèles récursifs pour étendre l’exemple précédent. Vous ajoutez des bras d’expression de commutateur pour les tableaux qui ont moins de 3 éléments. Les modèles récursifs sont indiqués dans l’exemple suivant :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Les modèles récursifs peuvent examiner les propriétés de l’expression de la plage, mais ne peuvent pas exécuter le code arbitraire. Vous pouvez utiliser un garde `when` de *cas,* spécifié dans une clause, pour fournir des contrôles similaires pour d’autres types de séquences:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Enfin, vous pouvez `_` ajouter `null` le modèle et le modèle pour attraper les arguments qui ne sont pas traités par n’importe quel autre bras d’expression de commutateur. Cela rend l’expression de commutateur *exhaustive,* ce qui signifie que toute valeur possible de l’expression de la gamme est manipulée. L’exemple suivant ajoute ces bras d’expression :

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

L’exemple précédent `null` ajoute un `IEnumerable<T>` modèle, et `_` change le modèle de type à un modèle. Le `null` modèle fournit une vérification nulle comme un bras d’expression de commutateur. L’expression de ce <xref:System.ArgumentNullException>bras jette un . Le `_` modèle correspond à toutes les entrées qui n’ont pas été égalées par les bras précédents. Il doit venir `null` après le chèque, ou il correspondrait aux `null` entrées.

Vous pouvez en savoir plus dans la proposition de spécifications linguistiques C pour [les modèles récursifs](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Critères spéciaux](../../pattern-matching.md)
