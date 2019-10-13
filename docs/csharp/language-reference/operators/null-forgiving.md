---
title: '! (null-indulgent avec)- C# référence d’opérateur'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291724"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-indulgent avec), opérateurC# (référence)

Disponible dans C# 8,0 et versions ultérieures, l’opérateur postfix unaire `!` est l’opérateur null-indulgent avec. Dans un [contexte d’annotation Nullable](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur null-indulgent avec pour déclarer que l’expression `x` d’un type référence n’est pas null : `x!`. Le préfixe unaire @no__t opérateur-0 est un [opérateur de négation logique](boolean-logical-operators.md#logical-negation-operator-).

L’opérateur null-indulgent avec n’a aucun effet au moment de l’exécution. Elle affecte uniquement l’analyse du déroulement statique du compilateur en modifiant l’État null de l’expression. Au moment de l’exécution, l’expression `x!` correspond au résultat de l’expression sous-jacente `x`.

Pour plus d’informations sur la fonctionnalité des types de référence Nullable, consultez [types de référence Nullable](../../nullable-references.md).

## <a name="examples"></a>Exemples

L’un des cas d’usage de l’opérateur null-indulgent avec consiste à tester la logique de validation d’argument. Par exemple, considérons la classe suivante :

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

À l’aide de l' [infrastructure de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code précédent : `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Avec l’utilisation de l’opérateur null-indulgent avec, vous laissez le compilateur savoir que le passage de `null` est attendu et ne doit pas être averti de.

Vous pouvez également utiliser l’opérateur null-indulgent avec lorsque vous savez absolument qu’une expression ne peut pas être `null`, mais que le compilateur ne gère pas. Dans l’exemple suivant, si la méthode `IsValid` retourne `true`, son argument n’est pas `null` et vous pouvez le déréférencer en toute sécurité :

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code `p.Name` : `Warning CS8602: Dereference of a possibly null reference.`.

Si vous pouvez modifier la méthode `IsValid`, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la méthode `IsValid` ne peut pas être `null` lorsque la méthode retourne `true` :

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent avec, car le compilateur dispose de suffisamment d’informations pour déterminer que `p` ne peut pas être `null` à l’intérieur de l’instruction `if`. Pour plus d’informations sur les attributs qui vous permettent de spécifier des informations supplémentaires sur l’État null d’une variable, consultez [mettre à niveau les API avec des attributs pour définir des attentes null](../../nullable-attributes.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Tutoriel : Conception avec types de référence Nullable @ no__t-0
