---
title: Opérateurs d’accès aux membres - Référence C#
description: Découvrez les opérateurs C# que vous pouvez utiliser pour accéder aux membres de type.
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: ab69514e324c632f546957b2ddb58e073ca0154e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239248"
---
# <a name="member-access-operators-c-reference"></a>Opérateurs d’accès aux membres (référence C#)

Vous pouvez utiliser les opérateurs suivants lorsque vous accédez à un membre de type :

- [`.` (accès aux membres)](#member-access-operator-) : accédez à un membre d’un espace de noms ou d’un type
- [`[]` (accès à un indexeur ou à un élément de tableau)](#indexer-operator-) : pour accéder à un élément de tableau ou à un indexeur de type
- [`?.` et `?[]` (opérateurs conditionnels Null)](#null-conditional-operators--and-) : pour effectuer une opération d’accès à un membre ou élément uniquement si un opérande est non Null
- [`()` (appel) ](#invocation-operator-) : pour appeler une méthode sollicitée ou appeler un délégué
- [`^` (index à partir de la fin)](#index-from-end-operator-): pour indiquer que la position de l’élément est à partir de la fin d’une séquence
- [`..` (plage)](#range-operator-): pour spécifier une plage d’index que vous pouvez utiliser pour obtenir une plage d’éléments de séquence

## <a name="member-access-operator-"></a>Opérateur d’accès aux membres .

Le jeton `.` sert à accéder à l’un des membres d’un espace de noms ou d’un type, comme le montrent les exemples suivants :

- Utilisez `.` pour accéder à un espace de noms imbriqué dans un autre, comme le montre l’exemple suivant avec la [directive `using`](../keywords/using-directive.md) :

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Utilisez `.` pour former un *nom qualifié* permettant d’accéder à un type dans un espace de noms, comme le montre le code suivant :

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Utilisez une [directive `using`](../keywords/using-directive.md) pour rendre facultative l’utilisation de noms qualifiés.

- Utilisez `.` pour accéder aux [membres de type](../../programming-guide/classes-and-structs/index.md#members), statiques et non statiques, comme le montre le code suivant :

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Vous pouvez également utiliser `.` pour accéder à une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Opérateur d’indexeur []

Les crochets, `[]`, sont généralement utilisés pour l’accès à un élément tableau, indexeur ou pointeur.

### <a name="array-access"></a>Accès aux tableaux

L’exemple suivant montre comment accéder à des éléments tableau :

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Si un index de tableau est en dehors des limites de la dimension correspondante d’un tableau, une <xref:System.IndexOutOfRangeException> est levée.

Comme le montre l’exemple précédent, vous utilisez également des crochets quand vous déclarez un type tableau ou instanciez une instance de tableau.

Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Accès aux indexeurs

L’exemple suivant utilise le type de <xref:System.Collections.Generic.Dictionary%602> .NET pour illustrer l’accès à l’indexeur :

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Les indexeurs vous permettent d’indexer des instances d’un type défini par l’utilisateur en procédant de la même façon que pour l’indexation de tableau. Contrairement aux index de tableau, qui doivent être des entiers, les paramètres de l’indexeur peuvent être déclarés comme n’importe quel type.

Pour plus d’informations sur les indexeurs, consultez [Indexeurs](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Autres utilisations de []

Pour plus d’informations concernant l’accès à l’élément de pointeur, consultez la section [Opérateur d’accès à l’élément de pointeur []](pointer-related-operators.md#pointer-element-access-operator-) de l’article [Opérateurs associés au pointeur](pointer-related-operators.md).

Vous utilisez également des crochets pour spécifier des [attributs](../../programming-guide/concepts/attributes/index.md) :

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Opérateurs conditionnels Null ?. et ?[]

Disponible dans C# 6 et versions ultérieures, un opérateur conditionnel null applique un accès au [membre](#member-access-operator-), `?.`ou un accès à l' [élément](#indexer-operator-), `?[]`, à son opérande uniquement si cet opérande a la valeur non null ; Sinon, elle retourne `null`. C'est

- Si `a` prend la valeur `null`, le résultat de `a?.x` ou `a?[x]` est `null`.
- Si `a` prend la valeur non null, le résultat de `a?.x` ou `a?[x]` est le même que le résultat de `a.x` ou de `a[x]`, respectivement.

  > [!NOTE]
  > Si `a.x` ou `a[x]` lève une exception, `a?.x` ou `a?[x]` lèvera la même exception pour les `a`non null. Par exemple, si `a` est une instance de tableau non null et que `x` se trouve en dehors des limites de `a`, `a?[x]` lèvera une <xref:System.IndexOutOfRangeException>.

Les opérateurs conditionnels Null ont un effet de court-circuit. Autrement dit, si une opération dans une chaîne d’opérations d’accès au membre ou à l’élément conditionnelles retourne une valeur `null`, le reste de la chaîne ne s’exécute pas. Dans l’exemple suivant, `B` n’est pas évalué si `A` prend la valeur `null` et `C` n’est pas évalué si `A` ou `B` prend la valeur `null` :

```csharp
A?.B?.Do(C);
A?.B?[C];
```

L’exemple suivant illustre l’utilisation des opérateurs `?.` et `?[]` :

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

L’exemple précédent utilise également l' [opérateur de fusion null `??`](null-coalescing-operator.md) pour spécifier une autre expression à évaluer si le résultat d’une opération conditionnelle null est `null`.

L’opérateur d’accès aux membres conditionnels null `?.` est également appelé l’opérateur Elvis.

### <a name="thread-safe-delegate-invocation"></a>Appel de délégué thread-safe

Utilisez l’opérateur `?.` pour vérifier si un délégué est non Null et l’appeler de manière thread-safe (par exemple, quand vous [déclenchez un événement](../../../standard/events/how-to-raise-and-consume-events.md)), comme illustré dans le code suivant :

```csharp
PropertyChanged?.Invoke(…)
```

Ce code est équivalent au code suivant que vous utiliseriez dans C# 5 ou une version antérieure :

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>Opérateur d’appel ()

Utilisez des parenthèses, `()`, pour appeler une [méthode](../../programming-guide/classes-and-structs/methods.md) ou un [délégué](../../programming-guide/delegates/index.md).

L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec l’opérateur [`new`](new-operator.md).

### <a name="other-usages-of-"></a>Autres utilisations de ()

Vous utilisez également des parenthèses pour ajuster l’ordre dans lequel évaluer les opérations dans une expression. Pour plus d’informations, consultez [Opérateurs C#](index.md).

[Les expressions cast](type-testing-and-cast.md#cast-operator-), qui effectuent des conversions de type explicites, utilisent aussi des parenthèses.

## <a name="index-from-end-operator-"></a>Index de fin d’opérateur ^

Disponible dans C# 8,0 et versions ultérieures, l’opérateur `^` indique la position de l’élément à partir de la fin d’une séquence. Pour une séquence de longueur `length`, `^n` pointe sur l’élément avec des `length - n` de décalage à partir du début d’une séquence. Par exemple, `^1` pointe vers le dernier élément d’une séquence et `^length` pointe vers le premier élément d’une séquence.

[!code-csharp[index from end](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

Comme le montre l’exemple précédent, expression `^e` est du type <xref:System.Index?displayProperty=nameWithType>. Dans expression `^e`, le résultat de `e` doit être implicitement convertible en `int`.

Vous pouvez également utiliser l’opérateur `^` avec l' [opérateur Range](#range-operator-) pour créer une plage d’index. Pour plus d’informations, consultez [index et plages](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Opérateur de plage..

Disponible dans C# 8,0 et versions ultérieures, l’opérateur `..` spécifie le début et la fin d’une plage d’index comme opérandes. L’opérande de gauche est un début *inclusif* d’une plage. L’opérande de droite est une extrémité *exclusive* d’une plage. L’un ou l’autre des opérandes peut être un index à partir du début ou de la fin d’une séquence, comme le montre l’exemple suivant :

[!code-csharp[range examples](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

Comme le montre l’exemple précédent, expression `a..b` est du type <xref:System.Range?displayProperty=nameWithType>. Dans expression `a..b`, les résultats de `a` et `b` doivent être implicitement convertibles en `int` ou <xref:System.Index>.

Vous pouvez omettre l’un des opérandes de l’opérateur `..` pour obtenir une plage ouverte :

- `a..` équivaut à `a..^0`
- `..b` équivaut à `0..b`
- `..` équivaut à `0..^0`

[!code-csharp[ranges with omitted operands](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

Pour plus d’informations, consultez [index et plages](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Les opérateurs `.`, `()`, `^`et `..` ne peuvent pas être surchargés. L’opérateur `[]` est également considéré comme un opérateur non surchargeable. Utilisez des [indexeurs](../../programming-guide/indexers/index.md) pour prendre en charge l’indexation avec des types définis par l’utilisateur.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Accès aux membres](~/_csharplang/spec/expressions.md#member-access)
- [Accès aux éléments](~/_csharplang/spec/expressions.md#element-access)
- [Opérateur conditionnel Null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Expressions d’appels](~/_csharplang/spec/expressions.md#invocation-expressions)

Pour plus d’informations sur les index et les plages, consultez la [Remarque relative](~/_csharplang/proposals/csharp-8.0/ranges.md)à la proposition de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [?? (opérateur de fusion Null)](null-coalescing-operator.md)
- [:: opérateur](namespace-alias-qualifier.md)
