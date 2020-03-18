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
ms.openlocfilehash: 4d4bc0c192912b5fa87a8e91bc5ba0e1d4ce3598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399510"
---
# <a name="member-access-operators-c-reference"></a>Opérateurs d’accès aux membres (référence C#)

Vous pouvez utiliser les opérateurs suivants lorsque vous accédez à un membre type :

- (accès des membres) : accéder à un membre d’un espace de nom ou d’un type [ `.` ](#member-access-operator-)
- [(accès à l’élément de tableau ou à l’indexeur) : accéder à un élément de tableau ou à un indexeur de type `[]` ](#indexer-operator-)
- [et `?[]` (opérateurs non conditionnels) : effectuer une opération d’accès à un membre ou à un élément uniquement si un opérande n’est pas `?.` ](#null-conditional-operators--and-)nul
- (invocation) : appeler une méthode consultée ou invoquer un délégué [ `()` ](#invocation-operator-)
- [(index à partir de la fin) : indiquer que la position de l’élément est à partir de la fin d’une séquence `^` ](#index-from-end-operator-)
- (gamme) : pour spécifier une gamme d’indices que vous pouvez utiliser pour obtenir une gamme d’éléments séquences [ `..` ](#range-operator-)

## <a name="member-access-operator-"></a>Opérateur d’accès aux membres .

Le jeton `.` sert à accéder à l’un des membres d’un espace de noms ou d’un type, comme le montrent les exemples suivants :

- Utiliser `.` pour accéder à un espace nom imbriqué dans [ `using` ](../keywords/using-directive.md) un espace nom, comme le montre l’exemple suivant d’une directive :

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Utilisez `.` pour former un *nom qualifié* permettant d’accéder à un type dans un espace de noms, comme le montre le code suivant :

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Utilisez [ `using` ](../keywords/using-directive.md) une directive pour rendre facultatif l’utilisation de noms qualifiés.

- Utilisez `.` pour accéder aux [membres de type](../../programming-guide/classes-and-structs/index.md#members), statiques et non statiques, comme le montre le code suivant :

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Vous pouvez également utiliser `.` pour accéder à une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Opérateur d’indexeur []

Les crochets, `[]`, sont généralement utilisés pour l’accès à un élément tableau, indexeur ou pointeur.

### <a name="array-access"></a>Accès aux tableaux

L’exemple suivant montre comment accéder à des éléments tableau :

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Si un index de tableau est en dehors des limites de la dimension correspondante d’un tableau, une <xref:System.IndexOutOfRangeException> est levée.

Comme le montre l’exemple précédent, vous utilisez également des crochets quand vous déclarez un type tableau ou instanciez une instance de tableau.

Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Accès aux indexeurs

L’exemple suivant utilise <xref:System.Collections.Generic.Dictionary%602> le type .NET pour démontrer l’accès à l’indexeur :

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

Les indexeurs vous permettent d’indexer des instances d’un type défini par l’utilisateur en procédant de la même façon que pour l’indexation de tableau. Contrairement aux indices de tableau, qui doivent être integer, les paramètres de l’indexeur peuvent être déclarés être de n’importe quel type.

Pour plus d’informations sur les indexeurs, consultez [Indexeurs](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Autres utilisations de []

Pour plus d’informations concernant l’accès à l’élément de pointeur, consultez la section [Opérateur d’accès à l’élément de pointeur []](pointer-related-operators.md#pointer-element-access-operator-) de l’article [Opérateurs associés au pointeur](pointer-related-operators.md).

Vous utilisez également des crochets pour spécifier des [attributs](../../programming-guide/concepts/attributes/index.md) :

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Opérateurs conditionnels Null ?. et ?[]

Disponible en C 6 et plus tard, un opérateur `?.`sans condition `?[]`applique un accès de [membre,](#member-access-operator-), ou [l’accès à l’élément](#indexer-operator-), , opération à son opérande seulement si cet opérand évalue à non-null; sinon, il `null`revient . C'est

- Si `a` évalue `null`à , `a?.x` le `a?[x]` `null`résultat ou est .
- Si `a` l’on évalue à non-null, le résultat `a?.x` ou `a?[x]` est le même que le résultat ou `a.x` `a[x]`, respectivement.

  > [!NOTE]
  > Si `a.x` `a[x]` ou jette une `a?.x` `a?[x]` exception, ou jetterait la `a`même exception pour non-null . Par exemple, `a` si est une instance `x` de tableau non-null et est en dehors des limites de `a`, `a?[x]` jetterait un <xref:System.IndexOutOfRangeException>.

Les opérateurs conditionnels Null ont un effet de court-circuit. Autrement dit, si une opération dans une chaîne d’opérations d’accès au membre ou à l’élément conditionnelles retourne une valeur `null`, le reste de la chaîne ne s’exécute pas. Dans l’exemple suivant, `B` n’est pas évalué si `A` prend la valeur `null` et `C` n’est pas évalué si `A` ou `B` prend la valeur `null` :

```csharp
A?.B?.Do(C);
A?.B?[C];
```

L’exemple suivant illustre l’utilisation des opérateurs `?.` et `?[]` :

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

L’exemple précédent utilise également [l’opérateur `??` de fusion nulle](null-coalescing-operator.md) pour spécifier une expression `null`alternative à évaluer au cas où le résultat d’une opération non conditionnelle est .

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

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec l’opérateur [`new`](new-operator.md).

### <a name="other-usages-of-"></a>Autres utilisations de ()

Vous utilisez également des parenthèses pour ajuster l’ordre dans lequel évaluer les opérations dans une expression. Pour plus d’informations, consultez [Opérateurs C#](index.md).

[Les expressions cast](type-testing-and-cast.md#cast-operator-), qui effectuent des conversions de type explicites, utilisent aussi des parenthèses.

## <a name="index-from-end-operator-"></a>Indice de l’opérateur final

Disponible en C 8.0 et `^` plus tard, l’opérateur indique la position de l’élément à partir de la fin d’une séquence. Pour une séquence `length` `^n` de longueur, pointe `length - n` vers l’élément avec décalage dès le début d’une séquence. Par exemple, `^1` indique le dernier élément `^length` d’une séquence et pointe vers le premier élément d’une séquence.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Comme le montre l’exemple <xref:System.Index?displayProperty=nameWithType> précédent, l’expression `^e` est du genre. En `^e`expression , `e` le résultat de `int`doit être implicitement convertible à .

Vous pouvez également `^` utiliser l’opérateur avec l’opérateur [de la gamme](#range-operator-) pour créer une gamme d’indices. Pour plus d’informations, voir [Indices et gammes](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Opérateur de gamme ..

Disponible en C 8.0 et `..` plus tard, l’opérateur spécifie le début et la fin d’une gamme d’indices comme ses opérands. L’opéra de gauche est un début de gamme *inclusif.* L’opéra de droite est une fin *exclusive* d’une gamme. L’un ou l’autre des opérandes peut être un index dès le début ou à partir de la fin d’une séquence, comme le montre l’exemple suivant :

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Comme le montre l’exemple <xref:System.Range?displayProperty=nameWithType> précédent, l’expression `a..b` est du genre. En `a..b`expression, les `a` `b` résultats et doivent `int` être <xref:System.Index>implicitement convertibles ou .

Vous pouvez omettre l’un `..` des opérands de l’opérateur pour obtenir une gamme ouverte :

- `a..`est équivalent à`a..^0`
- `..b`est équivalent à`0..b`
- `..`est équivalent à`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Pour plus d’informations, voir [Indices et gammes](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Le `.` `()`, `^`, `..` et les opérateurs ne peuvent pas être surchargés. L’opérateur `[]` est également considéré comme un opérateur non surchargeable. Utilisez des [indexeurs](../../programming-guide/indexers/index.md) pour prendre en charge l’indexation avec des types définis par l’utilisateur.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Accès aux membres](~/_csharplang/spec/expressions.md#member-access)
- [Accès aux éléments](~/_csharplang/spec/expressions.md#element-access)
- [Opérateur conditionnel Null](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Expressions d’appels](~/_csharplang/spec/expressions.md#invocation-expressions)

Pour plus d’informations sur les indices et les plages, voir la [note de proposition de fonctionnalité](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [?? (opérateur de fusion Null)](null-coalescing-operator.md)
- [:: opérateur](namespace-alias-qualifier.md)
