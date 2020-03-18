---
title: ?? Et?? Opérateurs - Référence C
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847311"
---
# <a name="-and--operators-c-reference"></a>?? Et?? - opérateurs (référence C)

L’opérateur de fusion null `??` retourne la valeur de l’opérande de gauche si elle n’est pas `null` ; sinon, il évalue l’opérande de droite et retourne son résultat. L’opérateur `??` n’évalue pas son opérande de droite si l’opérande de gauche n’est pas Null.

Disponible en C 8.0 et plus tard, l’opérateur `??=` d’affectation de fusion nulle attribue la valeur de son opérande de droite `null`à son opératment de gauche seulement si l’opérand gauche évalue à . L’opérateur `??=` n’évalue pas son opérande de droite si l’opérande de gauche n’est pas Null.

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

L’opératoire gauche `??=` de l’opérateur doit être une variable, une [propriété,](../../programming-guide/classes-and-structs/properties.md)ou un élément [d’indexeur.](../../programming-guide/indexers/index.md)

Dans C 7.3 et plus tôt, le type de `??` l’opératoire gauche de l’opérateur doit être soit un type de [référence,](../keywords/reference-types.md) soit un [type de valeur nul](../builtin-types/nullable-value-types.md). À partir de C 8.0, cette exigence est remplacée par ce qui `??` suit `??=` : le type de l’opéra de gauche et les opérateurs ne peuvent pas être un type de valeur non annulable. En particulier, en commençant par le C 8.0, vous pouvez utiliser les opérateurs de fusion nulle avec des paramètres de type sans contrainte :

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

Les opérateurs de fusion nul sont de droite-associative. C’est-à-dire, les expressions de la forme

```csharp
a ?? b ?? c
d ??= e ??= f
```

sont évalués comme

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Exemples

Les `??` `??=` opérateurs et les opérateurs peuvent être utiles dans les scénarios suivants :

- Dans les expressions avec les [opérateurs null-conditionnels ?. et ?[]](member-access-operators.md#null-conditional-operators--and-), vous pouvez utiliser l’opérateur `??` pour `null`fournir une expression alternative à évaluer au cas où le résultat de l’expression avec des opérations non conditionnelles est:

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- Lorsque vous [travaillez](../builtin-types/nullable-value-types.md) avec des types de valeur nul et que `??` vous devez fournir une valeur d’un `null`type de valeur sous-jacent, utilisez l’opérateur pour spécifier la valeur à fournir au cas où une valeur de type nul serait :

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> si la valeur à utiliser quand une valeur de type Nullable est `null` doit être la valeur par défaut du type valeur sous-jacent.

- En commençant par le numéro 7.0, vous pouvez utiliser une `??` [ `throw` expression](../keywords/throw.md#the-throw-expression) comme l’opéra de droite de l’opérateur pour rendre le code de vérification des arguments plus concis :

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  L’exemple précédent montre également comment utiliser des [membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) pour définir une propriété.

- En commençant par le C 8.0, vous pouvez utiliser l’opérateur `??=` pour remplacer le code du formulaire

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  par le code suivant :

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Les `??` opérateurs `??=` et ne peuvent pas être surchargés.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations sur l’opérateur, `??` voir La section de [l’opérateur](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) de fusion nul de la spécification linguistique [CMD](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur l’opérateur, `??=` voir la note de proposition de [fonctionnalité](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)
- [?: opérateur](conditional-operator.md)
