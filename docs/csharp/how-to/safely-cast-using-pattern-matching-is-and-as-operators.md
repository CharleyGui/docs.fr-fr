---
title: Comment effectuer un cast en toute sécurité à l’aide de critères spéciaux et des opérateurs is et As
description: Découvrez les techniques relatives aux critères spéciaux pour caster de manière sécurisée des variables vers un autre type. Vous pouvez utiliser les critères spéciaux, ainsi que les opérateurs is et as pour convertir des types de manière sécurisée.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: f10ce837057cc61b84130f237a13af708849dfc5
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662964"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Comment effectuer un cast en toute sécurité à l’aide de critères spéciaux et des opérateurs is et As

Dans la mesure où les objets sont polymorphes, une variable d’un type de classe de base peut contenir un [type](../programming-guide/types/index.md) dérivé. Pour accéder aux membres d’instance du type dérivé, il est nécessaire de réeffectuer un [cast](../programming-guide/types/casting-and-type-conversions.md) de la valeur vers le type dérivé. Toutefois, un cast risque de lever <xref:System.InvalidCastException>. C# fournit des instructions relatives aux [critères spéciaux](../pattern-matching.md), qui effectuent un cast de manière conditionnelle, uniquement en cas de réussite. C# fournit également les opérateurs [is](../language-reference/operators/type-testing-and-cast.md#is-operator) et [as](../language-reference/operators/type-testing-and-cast.md#as-operator) pour tester l’appartenance d’une valeur à un certain type.

L’exemple suivant montre comment utiliser l’instruction de critères spéciaux `is` :

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs" id="PatternMatchingIs":::

L’exemple précédent illustre quelques fonctionnalités de la syntaxe relative aux critères spéciaux. L' `if (a is Mammal m)` instruction associe le test à une assignation d’initialisation. L’assignation n’a lieu qu’en cas de réussite du test. La variable `m` se trouve uniquement dans l’étendue de l’instruction `if` incorporée, à laquelle elle a été assignée. Vous ne pouvez pas accéder à `m` plus tard dans la même méthode. L’exemple précédent montre également comment utiliser l' [ `as` opérateur](../language-reference/operators/type-testing-and-cast.md#as-operator) pour convertir un objet en un type spécifié.

Vous pouvez également utiliser la même syntaxe pour le test si un [type valeur Nullable](../language-reference/builtin-types/nullable-value-types.md) a une valeur, comme illustré dans l’exemple suivant :

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs" id="PatternMatchingNullable":::

L’exemple précédent illustre d’autres fonctionnalités relatives aux critères spéciaux pour les conversions. Vous pouvez tester le modèle null d’une variable en vérifiant spécifiquement la valeur `null`. Quand la valeur runtime de la variable est `null`, une instruction `is` de vérification de type retourne toujours `false`. L’instruction `is` relative aux critères spéciaux n’autorise aucun type valeur Nullable, par exemple `int?` ou `Nullable<int>`. Toutefois, vous pouvez tester un autre type valeur. Les `is` modèles de l’exemple précédent ne sont pas limités aux types valeur Nullable. Vous pouvez également utiliser ces modèles pour tester si une variable d’un type référence a une valeur ou s’il s’agit de `null` .

L’exemple précédent montre également comment utiliser le modèle de type dans une `switch` instruction où la variable peut être l’un des nombreux types différents.

Si vous souhaitez tester si une variable est un type donné, mais ne pas l’assigner à une nouvelle variable, vous pouvez utiliser les `is` opérateurs et pour les types `as` référence et les types valeur Nullable. Le code suivant montre comment utiliser les instructions `is` et `as`, qui faisaient partie du langage C# avant l’introduction des critères spéciaux permettant de déterminer l’existence ou non d’un type donné pour une variable :

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs" id="IsAndAs":::

Comme vous pouvez le constater en comparant ce code avec le code utilisant les critères spéciaux, la syntaxe des critères spéciaux fournit des fonctionnalités plus robustes, car elle combine le test et l’assignation dans une seule instruction. Utilisez la syntaxe des critères spéciaux autant que possible.
