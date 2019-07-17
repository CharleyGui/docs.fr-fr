---
title: Opérateurs de conversion et de test de type - Référence C#
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
ms.openlocfilehash: a9e5139e6d650aa6935bff934ca25502fdc14775
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744075"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a>Opérateurs de conversion et de test de type (Référence C#)

Vous pouvez utiliser les opérateurs suivants pour effectuer la vérification du type ou la conversion de type :

- [Opérateur is](#is-operator) : pour vérifier si le type de runtime d’une expression est compatible avec un type donné
- [Opérateur as](#as-operator) : pour convertir explicitement une expression en un type donné si son type de runtime est compatible avec ce type
- [Opérateur cast ()](#cast-operator-) : pour effectuer une conversion explicite
- [Opérateur typeof](#typeof-operator) : pour obtenir l’instance de <xref:System.Type?displayProperty=nameWithType> pour un type

## <a name="is-operator"></a>Opérateur is

L’opérateur `is` vérifie si le type de runtime du résultat d’une expression est compatible avec un type donné. À compter de C# 7.0, l’opérateur `is` teste également un résultat d’expression par rapport à un modèle.

L’expression avec l’opérateur de test de type `is` a la forme suivante

```csharp
E is T
```

où `E` est une expression qui retourne une valeur et `T` est le nom d’un type ou un d’un paramètre de type. `E` ne peut pas être une méthode anonyme ou une expression lambda.

L’expression `E is T` retourne `true` si le résultat de `E` n’est pas null et peut être converti en type `T` par une conversion de référence, une conversion boxing ou une conversion unboxing ; sinon, elle retourne `false`. L’opérateur `is` ne considère pas les conversions définies par l’utilisateur.

L’exemple suivant montre que l’opérateur `is` retourne `true` si le type de runtime d’une expression dérive d’un type donné, autrement dit, s’il existe une conversion de référence entre les types :

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

L’exemple suivant montre que l’opérateur `is` tient compte des conversions boxing et unboxing mais ne considère pas les conversions numériques :

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Pour plus d’informations sur les conversions C#, consultez le chapitre [Conversions](~/_csharplang/spec/conversions.md) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Test de type avec des critères spéciaux

À compter de C# 7.0, l’opérateur `is` teste également un résultat d’expression par rapport à un modèle. En particulier, il prend en charge le modèle de type sous la forme suivante :

```csharp
E is T v
```

où `E` est une expression qui retourne une valeur, `T` est le nom d’un type ou un d’un paramètre de type et `v` est une nouvelle variable locale de type `T`. Si le résultat de `E` n’est pas null et peut être converti en `T` par conversion de référence, boxing ou unboxing, l’expression `E is T v` retourne `true` et la valeur convertie du résultat de `E` est affectée à la variable `v`.

L’exemple suivant illustre l’utilisation de l’opérateur `is` avec le modèle de type :

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Pour plus d’informations sur le modèle de type et les autres modèles pris en charge, consultez [Critères spéciaux avec is](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>opérateur as

L’opérateur `as` convertit explicitement le résultat d’une expression en un type de valeur de référence ou nullable. Si la conversion n’est pas possible, l’opérateur `as` retourne `null`. Contrairement à [l’opérateur cast ()](#cast-operator-), l’opérateur `as` ne lève jamais d’exception.

L’expression de la forme

```csharp
E as T
```

où `E` est une expression qui retourne une valeur et `T` est le nom d’un type ou un d’un paramètre de type, avec le même résultat que

```csharp
E is T ? (T)(E) : (T)null
```

sauf que `E` n’est évalué qu’une seule fois.

L’opérateur `as` envisage uniquement les conversions de référence, nullable, boxing et unboxing. Vous ne pouvez pas utiliser l’opérateur `as` pour effectuer une conversion définie par l’utilisateur. Pour ce faire, utilisez [l’opérateur cast ()](#cast-operator-).

L’exemple suivant illustre l’utilisation de l’opérateur `as` :

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Comme le montre l’exemple précédent, vous devez comparer le résultat de l’expression `as` avec `null` pour vérifier si la conversion a réussi. À compter de C# 7.0, vous pouvez utiliser [l’opérateur is](#type-testing-with-pattern-matching) pour tester si la conversion réussit et, le cas échéant, affecter son résultat à une nouvelle variable.

## <a name="cast-operator-"></a>Opérateur de cast ()

Une expression cast de la forme `(T)E` effectue une conversion explicite du résultat de l’expression `E` en type `T`. S’il n’existe aucune conversion explicite du type de `E` en type `T`, une erreur de compilation se produit. Au moment de l’exécution, une conversion explicite peut ne pas réussir, et une expression cast peut lever une exception.

L’exemple suivant montre des conversions numériques et de référence explicites :

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Pour plus d’informations sur les conversions explicites prises en charge, consultez la section [Conversions explicites](~/_csharplang/spec/conversions.md#explicit-conversions) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md). Pour plus d’informations sur la façon de définir une conversion de type explicite ou implicite personnalisée, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Autres utilisations de ()

Vous pouvez aussi utiliser des parenthèses pour [appeler une méthode ou un délégué](member-access-operators.md#invocation-operator-).

Une autre utilisation des parenthèses est pour spécifier l’ordre dans lequel évaluer les opérations dans une expression. Pour plus d’informations, consultez la section [Ajout de parenthèses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) de l’article [Opérateurs](../../programming-guide/statements-expressions-operators/operators.md). Pour obtenir la liste des opérateurs classés par niveau de priorité, consultez [Opérateurs C#](index.md).

## <a name="typeof-operator"></a>Opérateur typeof

L’opérateur `typeof` obtient l’instance <xref:System.Type?displayProperty=nameWithType> pour un type. Un argument de l’opérateur `typeof` doit avoir le nom d’un type ou d’un paramètre de type, comme le montre l’exemple suivant :

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

Vous pouvez également utiliser l’opérateur `typeof` avec les types génériques indépendants. Le nom d’un type générique indépendant doit contenir le nombre approprié de virgules, à savoir une de moins que le nombre de paramètres de type. L’exemple suivant illustre l’utilisation de l’opérateur `typeof` avec un type générique indépendant :

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Une expression ne peut pas être un argument de l’opérateur `typeof`. Pour obtenir l’instance <xref:System.Type?displayProperty=nameWithType> pour le type de runtime du résultat de l’expression, utilisez la méthode <xref:System.Object.GetType%2A?displayProperty=nameWithType>.

### <a name="type-testing-with-the-typeof-operator"></a>Test de type avec l’opérateur `typeof`

Utilisez l’opérateur `typeof` pour vérifier si le type de runtime du résultat de l’expression correspond exactement à un type donné. L’exemple suivant illustre la différence entre la vérification des types effectuée avec l’opérateur `typeof` [l’opérateur is](#is-operator) :

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Les opérateurs `is`, `as` et `typeof` ne sont pas surchargeables.

Un type défini par l’utilisateur ne peut pas surcharger l’opérateur `()`, mais vous pouvez définir des conversions de type personnalisées qui peuvent être effectuées par une expression cast. Pour plus d’informations, consultez [Opérateurs de conversion définie par l’utilisateur](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [L’opérateur is](~/_csharplang/spec/expressions.md#the-is-operator)
- [L’opérateur as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Expressions cast](~/_csharplang/spec/expressions.md#cast-expressions)
- [L’opérateur typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Guide pratique pour caster de manière sécurisée avec les critères spéciaux, ainsi que les opérateurs is et as](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
