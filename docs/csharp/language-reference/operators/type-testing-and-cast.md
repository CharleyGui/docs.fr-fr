---
title: Opérateurs de test de type et expression de cast-référence C#
description: Découvrez les opérateurs C# que vous pouvez utiliser pour vérifier le type de résultat d’une expression et le convertir en un autre type si nécessaire.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: 7c1c65c61a2214792dcd26efd4be1a9d7f2c07ca
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555498"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a>Opérateurs de test de type et expression de cast (référence C#)

Vous pouvez utiliser les opérateurs et expressions suivants pour effectuer une vérification de type ou une conversion de type :

- [Opérateur is](#is-operator) : pour vérifier si le type de runtime d’une expression est compatible avec un type donné
- [Opérateur as](#as-operator) : pour convertir explicitement une expression en un type donné si son type de runtime est compatible avec ce type
- [expression de cast](#cast-expression): pour effectuer une conversion explicite
- [Opérateur typeof](#typeof-operator) : pour obtenir l’instance de <xref:System.Type?displayProperty=nameWithType> pour un type

## <a name="is-operator"></a>Opérateur is

L’opérateur `is` vérifie si le type de runtime du résultat d’une expression est compatible avec un type donné. À compter de C# 7,0, l' `is` opérateur teste également un résultat d’expression par rapport à un modèle.

L’expression avec l’opérateur de test de type `is` a la forme suivante

```csharp
E is T
```

où `E` est une expression qui retourne une valeur et `T` est le nom d’un type ou un d’un paramètre de type. `E` ne peut pas être une méthode anonyme ou une expression lambda.

L’expression `E is T` retourne `true` si le résultat de `E` n’est pas null et peut être converti en type `T` par une conversion de référence, une conversion boxing ou une conversion unboxing ; sinon, elle retourne `false`. L’opérateur `is` ne considère pas les conversions définies par l’utilisateur.

L’exemple suivant montre que l’opérateur `is` retourne `true` si le type de runtime d’une expression dérive d’un type donné, autrement dit, s’il existe une conversion de référence entre les types :

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

L’exemple suivant montre que l' `is` opérateur prend en compte les conversions boxing et unboxing, mais ne prend pas en compte les [conversions numériques](../builtin-types/numeric-conversions.md):

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

Pour plus d’informations sur les conversions C#, consultez le chapitre [Conversions](~/_csharplang/spec/conversions.md) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Test de type avec des critères spéciaux

À compter de C# 7,0, l' `is` opérateur teste également un résultat d’expression par rapport à un modèle. En particulier, il prend en charge le modèle de type sous la forme suivante :

```csharp
E is T v
```

où `E` est une expression qui retourne une valeur, `T` est le nom d’un type ou un d’un paramètre de type et `v` est une nouvelle variable locale de type `T`. Si le résultat de `E` n’est pas null et peut être converti en `T` par conversion de référence, boxing ou unboxing, l’expression `E is T v` retourne `true` et la valeur convertie du résultat de `E` est affectée à la variable `v`.

L’exemple suivant illustre l’utilisation de l’opérateur `is` avec le modèle de type :

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Pour plus d’informations sur le modèle de type et les autres modèles pris en charge, consultez [Critères spéciaux avec is](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>opérateur as

L’opérateur `as` convertit explicitement le résultat d’une expression en un type de valeur de référence ou nullable. Si la conversion n’est pas possible, l’opérateur `as` retourne `null`. Contrairement à une [expression de cast](#cast-expression), l' `as` opérateur ne lève jamais d’exception.

L’expression de la forme

```csharp
E as T
```

où `E` est une expression qui retourne une valeur et `T` est le nom d’un type ou un d’un paramètre de type, avec le même résultat que

```csharp
E is T ? (T)(E) : (T)null
```

sauf que `E` n’est évalué qu’une seule fois.

L’opérateur `as` envisage uniquement les conversions de référence, nullable, boxing et unboxing. Vous ne pouvez pas utiliser l’opérateur `as` pour effectuer une conversion définie par l’utilisateur. Pour ce faire, utilisez une [expression de cast](#cast-expression).

L’exemple suivant illustre l’utilisation de l’opérateur `as` :

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Comme le montre l’exemple précédent, vous devez comparer le résultat de l’expression `as` avec `null` pour vérifier si la conversion a réussi. À compter de C# 7,0, vous pouvez utiliser l' [opérateur is](#type-testing-with-pattern-matching) pour tester si la conversion aboutit et, si elle aboutit, assigner son résultat à une nouvelle variable.

## <a name="cast-expression"></a>Expression Cast

Une expression cast de la forme `(T)E` effectue une conversion explicite du résultat de l’expression `E` en type `T`. S’il n’existe aucune conversion explicite du type de `E` en type `T`, une erreur de compilation se produit. Au moment de l’exécution, une conversion explicite peut ne pas réussir, et une expression cast peut lever une exception.

L’exemple suivant montre des conversions numériques et de référence explicites :

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

Pour plus d’informations sur les conversions explicites prises en charge, consultez la section [Conversions explicites](~/_csharplang/spec/conversions.md#explicit-conversions) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md). Pour plus d’informations sur la façon de définir une conversion de type explicite ou implicite personnalisée, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Autres utilisations de ()

Vous pouvez aussi utiliser des parenthèses pour [appeler une méthode ou un délégué](member-access-operators.md#invocation-expression-).

Une autre utilisation des parenthèses est d’ajuster l’ordre dans lequel évaluer les opérations dans une expression. Pour plus d’informations, consultez [Opérateurs C#](index.md).

## <a name="typeof-operator"></a>Opérateur typeof

L’opérateur `typeof` obtient l’instance <xref:System.Type?displayProperty=nameWithType> pour un type. L’argument de l’opérateur `typeof` doit avoir le nom d’un type ou d’un paramètre de type, comme le montre l’exemple suivant :

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

Vous pouvez également utiliser l' `typeof` opérateur avec des types génériques indépendants. Le nom d’un type générique indépendant doit contenir le nombre approprié de virgules, à savoir une de moins que le nombre de paramètres de type. L’exemple suivant illustre l’utilisation de l’opérateur `typeof` avec un type générique indépendant :

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Une expression ne peut pas être un argument de l’opérateur `typeof`. Pour obtenir l' <xref:System.Type?displayProperty=nameWithType> instance du type au moment de l’exécution d’un résultat d’expression, utilisez la <xref:System.Object.GetType%2A?displayProperty=nameWithType> méthode.

### <a name="type-testing-with-the-typeof-operator"></a>Test de type avec l’opérateur `typeof`

Utilisez l’opérateur `typeof` pour vérifier si le type de runtime du résultat de l’expression correspond exactement à un type donné. L’exemple suivant illustre la différence entre la vérification des types effectuée avec l’opérateur `typeof`[l’opérateur is](#is-operator) :

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Les `is` `as` opérateurs, et `typeof` ne peuvent pas être surchargés.

Un type défini par l’utilisateur ne peut pas surcharger l’opérateur `()`, mais vous pouvez définir des conversions de type personnalisées qui peuvent être effectuées par une expression cast. Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [L’opérateur is](~/_csharplang/spec/expressions.md#the-is-operator)
- [L’opérateur as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Expressions cast](~/_csharplang/spec/expressions.md#cast-expressions)
- [Opérateur typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [Comment effectuer un cast en toute sécurité à l’aide de critères spéciaux et des opérateurs is et As](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Génériques en .NET](../../../standard/generics/index.md)
