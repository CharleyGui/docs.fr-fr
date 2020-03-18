---
title: '! opérateur (null-forgiving) - Référence C'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 36bfa46cebd2b35c4985dfc23dbe84f8f5dc9201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846299"
---
# <a name="-null-forgiving-operator-c-reference"></a>! opérateur (null-forgiving) (référence C)

Disponible en C 8.0 et plus tard, l’opérateur de poteaufix `!` nonary est l’opérateur nul-indulgent. Dans un [contexte d’annotation annulée](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur nul pour déclarer que l’expression `x` d’un type de référence n’est pas `null`: `x!`. L’opérateur de `!` préfixe nonaire est l’opérateur [de négation logique](boolean-logical-operators.md#logical-negation-operator-).

L’opérateur qui pardonne les nullités n’a aucun effet au moment de l’exécution. Il n’affecte que l’analyse statique du flux du compilateur en modifiant l’état nul de l’expression. Au moment de `x!` l’exécution, l’expression `x`évalue au résultat de l’expression sous-jacente .

Pour plus d’informations sur la fonction de type de référence annulée, voir [les types de référence Nullable](../../nullable-references.md).

## <a name="examples"></a>Exemples

L’un des cas d’utilisation de l’opérateur null-indulgent est de tester la logique de validation de l’argument. Par exemple, considérons la classe suivante :

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

En utilisant le [cadre de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Sans l’opérateur null-indulgent, le compilateur génère l’avertissement `Warning CS8625: Cannot convert null literal to non-nullable reference type`suivant pour le code précédent: . En utilisant l’opérateur null-indulgent, vous informez `null` le compilateur que le passage est prévu et ne devrait pas être averti.

Vous pouvez également utiliser l’opérateur null-indulgent quand vous `null` savez certainement qu’une expression ne peut pas être, mais le compilateur ne parvient pas à le reconnaître. Dans l’exemple suivant, si la `IsValid` méthode revient, `true`son argument n’est pas `null` et vous pouvez en toute sécurité le déreférencer:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Sans l’opérateur null-indulgent, le compilateur génère l’avertissement suivant pour le `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.

Si vous pouvez `IsValid` modifier la méthode, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la `IsValid` méthode ne peut pas être `null` lorsque la méthode revient `true`:

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent `p` parce `null` que `if` le compilateur a suffisamment d’informations pour savoir qui ne peut pas être à l’intérieur de la déclaration. Pour plus d’informations sur les attributs qui vous permettent de fournir des informations supplémentaires sur l’état nul d’une variable, voir [Upgrade API avec des attributs pour définir les attentes nulles](../../nullable-attributes.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir La section [de l’opérateur nul-indulgent](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) de [l’ébauche de la spécification des types de référence nuls](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Tutorial: Conception avec des types de référence nuls](../../tutorials/nullable-reference-types.md)
