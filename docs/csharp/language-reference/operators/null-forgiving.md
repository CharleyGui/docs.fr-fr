---
title: '! opérateur (null-indulgent avec)-référence C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 772f37f1fc7446eae66f0cd0f12adb5e2e41997d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595947"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-indulgent avec), opérateur (référence C#)

Disponible en C# 8,0 et versions ultérieures, l' `!` opérateur postfix unaire est l’opérateur null-indulgent avec. Dans un [contexte d’annotation Nullable](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur null-indulgent avec pour déclarer que `x` l’expression d’un type `null`référence `x!`n’est pas :. L’opérateur préfixé `!` unaire est l' [opérateur de négation logique](boolean-logical-operators.md#logical-negation-operator-).

L’opérateur null-indulgent avec n’a aucun effet au moment de l’exécution. Elle affecte uniquement l’analyse du déroulement statique du compilateur en modifiant l’État null de l’expression. Au moment de l’exécution `x!` , l’expression prend la valeur du résultat de `x`l’expression sous-jacente.

> [!NOTE]
> En C# 8, l’opérateur null-indulgent avec interagit avec les [opérateurs conditionnels null](member-access-operators.md#null-conditional-operators--and-) d’une manière inattendue. L’expression `x?.y!.z` est analysée en `(x?.y)!.z`tant que. En raison de cette `z` interprétation, elle est `x` évaluée même si a `null`la valeur <xref:System.NullReferenceException>, ce qui peut entraîner un.

Pour plus d’informations sur la fonctionnalité des types de référence Nullable, consultez [types de référence Nullable](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Exemples

L’un des cas d’usage de l’opérateur null-indulgent avec consiste à tester la logique de validation d’argument. Par exemple, considérons la classe suivante :

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

À l’aide de l' [infrastructure de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code précédent : `Warning CS8625: Cannot convert null literal to non-nullable reference type`. En utilisant l’opérateur null-indulgent avec, vous informez le compilateur `null` que le passage est attendu et ne doit pas être averti de.

Vous pouvez également utiliser l’opérateur null-indulgent avec lorsque vous savez absolument qu’une expression ne peut `null` pas être, mais que le compilateur ne gère pas. Dans l’exemple suivant, si la `IsValid` méthode retourne `true`, son argument n’est `null` pas et vous pouvez la déréférencer en toute sécurité :

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le `p.Name` code : `Warning CS8602: Dereference of a possibly null reference`.

Si vous pouvez modifier la `IsValid` méthode, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la `IsValid` méthode ne peut `null` pas être lorsque la `true`méthode retourne :

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent avec, car le compilateur dispose de suffisamment d' `p` informations pour `null` déterminer qu' `if` il ne peut pas se trouver à l’intérieur de l’instruction. Pour plus d’informations sur les attributs qui vous permettent de fournir des informations supplémentaires sur l’État null d’une variable, consultez [mettre à niveau les API avec des attributs pour définir des attentes null](../attributes/nullable-analysis.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [la section opérateur null-indulgent avec](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) du [brouillon de la spécification des types de référence Nullable](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs C#](index.md)
- [Didacticiel : concevoir avec des types de référence Nullable](../../tutorials/nullable-reference-types.md)
