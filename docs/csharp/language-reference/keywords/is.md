---
description: is - Référence C#
title: is - Référence C#
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: d30ebfa2dc47265185a96514efbddc3e4937438c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "94982392"
---
# <a name="is-c-reference"></a>is (référence C#)

L’opérateur `is` vérifie si le résultat d’une expression est compatible avec un type donné, ou (à compter de C# 7.0) teste une expression par rapport à un modèle. Pour plus d’informations sur l’opérateur de test `is` de type, consultez la section [opérateur is](../operators/type-testing-and-cast.md#is-operator) de l’article relatif aux [opérateurs de test de type et de conversion](../operators/type-testing-and-cast.md) .

## <a name="pattern-matching-with-is"></a>Utilisation des critères spéciaux avec `is`

À compter de C# 7.0, les instructions `is` et [switch](switch.md) prennent en charge les critères spéciaux. Le mot clé `is` prend en charge les modèles suivants :

- [Modèle de type](#type-pattern), qui teste si une expression peut être convertie en un type spécifié et, si possible, effectue un cast de la variable en une variable de ce type.
- [Modèle de constante](#constant-pattern) : teste si une expression correspond à une valeur de constante spécifiée.
- [Modèle de variable](#var-pattern) : correspondance qui réussit toujours et lie la valeur d’une expression à une variable locale.

### <a name="type-pattern"></a>Modèle de type

Lorsque vous utilisez le modèle de type pour rechercher des critères spéciaux, `is` permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, effectuer un cast de l’expression en une variable de ce type. Il s’agit d’une extension simple de l’instruction `is` qui permet une évaluation et une conversion de type concises. La forme générale du modèle de type `is` est la suivante :

```csharp
   expr is type varname
```

Où *expr* est une expression qui prend la valeur d’une instance d’un certain type, *type* est le nom du type dans lequel le résultat de *expr* doit être converti, et *varname* est l’objet vers lequel le résultat de *expr* est converti si le `is` test a la valeur `true` .

L' `is` expression est `true` si *expr* n’est pas `null` et que l’une des conditions suivantes est vraie :

- *expr* est une instance du même type que *type*.
- *expr* est une instance d’un type qui dérive de *type*. En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.
- *expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*. Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration. Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.
- *expr* est une instance d’un type qui implémente l’interface *type*.

À compter de C# 7.1, *expr* peut avoir un type à la compilation défini par un paramètre de type générique et ses contraintes.

Si *exp* est `true` et que `is` est utilisé avec une instruction `if`, *varname* est assigné dans l’instruction `if` uniquement. La portée de *varname* provient de l’expression `is` à la fin du bloc englobant l’instruction `if`. L’utilisation de *varname* dans un autre emplacement génère une erreur de compilation pour l’utilisation d’une variable qui n’a pas été assignée.

L’exemple suivant utilise le modèle de type `is` pour fournir l’implémentation de la méthode <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> d’un type.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Sans critères spéciaux, ce code peut être écrit comme suit. L’utilisation de critères spéciaux de type génère un code lisible plus compact en éliminant la nécessité de tester si le résultat d’une conversion est un `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Le modèle de type `is` génère également du code plus compact lorsqu’il détermine le type d’un type valeur. L’exemple suivant utilise le modèle de type `is` pour déterminer si un objet est une instance `Person` ou `Dog` avant d’afficher la valeur d’une propriété appropriée.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Le code équivalent sans critères spéciaux nécessite une attribution distincte comprenant un cast explicite.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Modèle de constante

Lorsque vous utilisez des critères spéciaux avec le modèle de constante, `is` teste si une expression est égale à une constante spécifiée. Avec C# 6 et les versions antérieures, le modèle de constante est pris en charge par l’instruction [switch](switch.md). À compter de C# 7.0, il est également pris en charge par l’instruction `is`. Sa syntaxe est la suivante :

```csharp
   expr is constant
```

où *expr* est l’expression à évaluer, et où *constant* est la valeur à tester. *constant* peut correspondre à l’une des expressions constantes suivantes :

- Une valeur littérale

- Le nom d’une variable `const` déclarée

- Une constante d’énumération

L’expression constante est évaluée de la manière suivante :

- Si *expr* et *constant* sont des types intégraux, l’opérateur d’égalité C# détermine si l’expression retourne `true` (autrement dit, si `expr == constant`).

- Sinon, la valeur de l’expression est déterminée par un appel à la méthode statique [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).  

L’exemple suivant combine le modèle de type et le modèle de constante pour tester si un objet est une instance `Dice` et, si c’est le cas, pour déterminer si la valeur obtenue après un lancer de dés est de 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

La vérification de `null` peut être effectuée à l’aide du modèle de constante. Le mot clé `null` est pris en charge par l’instruction `is`. Sa syntaxe est la suivante :

```csharp
   expr is null
```

L’exemple suivant illustre une comparaison des vérifications de `null` :

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

L’expression `x is null` est calculée différemment pour les types référence et les types valeur Nullable. Pour les types valeur Nullable, elle utilise <xref:System.Nullable%601.HasValue?displayProperty=nameWithType> . Pour les types référence, elle utilise `(object)x == null` .

### <a name="var-pattern"></a>Modèle de variable

Une correspondance de modèle avec le `var` modèle est toujours réussie. Sa syntaxe est la suivante :

```csharp
   expr is var varname
```

Où la valeur de *expr* est toujours assignée à une variable locale nommée *varname*. *varname* est une variable du même type que le type au moment de la compilation de *expr*.

Si *expr* prend la valeur `null` , l' `is` expression produit `true` et assigne `null` à *varname*. Le modèle var est l’une des rares utilisations de `is` qui produit `true` une `null` valeur.

Vous pouvez utiliser le `var` modèle pour créer une variable temporaire dans une expression booléenne, comme le montre l’exemple suivant :

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Dans l’exemple précédent, la variable temporaire est utilisée pour stocker le résultat d’une opération coûteuse. La variable peut ensuite être utilisée plusieurs fois.

## <a name="c-language-specification"></a>spécification du langage C#
  
Pour plus d’informations, consultez la section [L’opérateur is](~/_csharplang/spec/expressions.md#the-is-operator) de la [Specification du langage C#](~/_csharplang/spec/introduction.md) et les propositions de langage C# suivantes :

- [Critères spéciaux](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Critères spéciaux avec génériques](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Mots clés C#](index.md)
- [Opérateurs de conversion et de test de type](../operators/type-testing-and-cast.md)
