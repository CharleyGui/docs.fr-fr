---
description: '! opérateur (null-indulgent avec)-référence C#'
title: '! opérateur (null-indulgent avec)-référence C#'
ms.date: 10/11/2019
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f2eb57bba462d471a041c17024fa7031c2c7f87d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830582"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-indulgent avec), opérateur (référence C#)

Disponible en C# 8,0 et versions ultérieures, l’opérateur postfix unaire `!` est l’opérateur null-indulgent avec. Dans un [contexte d’annotation Nullable](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur null-indulgent avec pour déclarer que l’expression `x` d’un type référence n’est pas `null` : `x!` . L’opérateur préfixé unaire `!` est l' [opérateur de négation logique](boolean-logical-operators.md#logical-negation-operator-).

L’opérateur null-indulgent avec n’a aucun effet au moment de l’exécution. Elle affecte uniquement l’analyse du déroulement statique du compilateur en modifiant l’État null de l’expression. Au moment de l’exécution, l’expression `x!` prend la valeur du résultat de l’expression sous-jacente `x` .

> [!NOTE]
> En C# 8, l’opérateur null-indulgent avec met fin à la liste des opérations [conditionnelles null](member-access-operators.md#null-conditional-operators--and-) précédentes. Par exemple, l’expression `x?.y!.z` est analysée comme `(x?.y)!.z` . En raison de cette interprétation, `z` est évalué même si `x` est `null` , ce qui peut entraîner un <xref:System.NullReferenceException> .

Pour plus d’informations sur la fonctionnalité des types de référence Nullable, consultez [types de référence Nullable](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Exemples

L’un des cas d’usage de l’opérateur null-indulgent avec consiste à tester la logique de validation d’argument. Par exemple, considérons la classe suivante :

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

À l’aide de l' [infrastructure de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code précédent : `Warning CS8625: Cannot convert null literal to non-nullable reference type` . En utilisant l’opérateur null-indulgent avec, vous informez le compilateur que le passage `null` est attendu et ne doit pas être averti de.

Vous pouvez également utiliser l’opérateur null-indulgent avec lorsque vous savez absolument qu’une expression ne peut pas être, `null` mais que le compilateur ne gère pas. Dans l’exemple suivant, si la `IsValid` méthode retourne `true` , son argument n’est pas `null` et vous pouvez la déréférencer en toute sécurité :

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le `p.Name` Code : `Warning CS8602: Dereference of a possibly null reference` .

Si vous pouvez modifier la `IsValid` méthode, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la `IsValid` méthode ne peut pas être `null` lorsque la méthode retourne `true` :

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent avec, car le compilateur dispose de suffisamment d’informations pour déterminer qu’il `p` ne peut pas se trouver `null` à l’intérieur de l' `if` instruction. Pour plus d’informations sur les attributs qui vous permettent de fournir des informations supplémentaires sur l’État null d’une variable, consultez [mettre à niveau les API avec des attributs pour définir des attentes null](../attributes/nullable-analysis.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [la section opérateur null-indulgent avec](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) du [brouillon de la spécification des types de référence Nullable](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [Didacticiel : concevoir avec des types de référence Nullable](../../tutorials/nullable-reference-types.md)
