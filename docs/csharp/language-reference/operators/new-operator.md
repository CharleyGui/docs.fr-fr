---
description: new, opérateur - Référence C#
title: new, opérateur - Référence C#
ms.date: 10/02/2020
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3125f3d2c694dcfc5682ee482f3f76072ac3726d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609380"
---
# <a name="new-operator-c-reference"></a>new, opérateur (Référence C#)

L’opérateur `new` crée une nouvelle instance d’un type.

Vous pouvez également utiliser le mot clé `new` comme [modificateur de déclaration de membre](../keywords/new-modifier.md) ou [contrainte de type générique](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Appel du constructeur

Pour créer une nouvelle instance d’un type, vous appelez généralement l’un des [constructeurs](../../programming-guide/classes-and-structs/constructors.md) de ce type, à l’aide de l’opérateur `new` :

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

Vous pouvez utiliser un [initialiseur d’objet ou de collection](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) avec l’opérateur `new` pour instancier et initialiser un objet dans une instruction, comme dans l’exemple suivant :

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

À compter de C# 9,0, les expressions d’appel de constructeur sont de type cible. Autrement dit, si un type cible d’une expression est connu, vous pouvez omettre un nom de type, comme le montre l’exemple suivant :

:::code language="csharp" source="snippets/shared/NewOperator.cs" id="SnippetTargetTyped":::

Comme le montre l’exemple précédent, vous utilisez toujours des parenthèses dans une expression de type cible `new` .

Si le type cible d’une `new` expression est inconnu (par exemple, lorsque vous utilisez le [`var`](../keywords/var.md) mot clé), vous devez spécifier un nom de type.

## <a name="array-creation"></a>Création de tableau

Vous utilisez également l’opérateur `new` pour créer une instance de tableau, comme dans l’exemple suivant :

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

Utilisez la syntaxe d’initialisation de tableau pour créer une instance de tableau et la remplir avec des éléments dans une instruction. L’exemple suivant montre différentes façons de procéder :

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Instanciation des types anonymes

Pour créer une instance d’un [type anonyme](../../programming-guide/classes-and-structs/anonymous-types.md), utilisez l’opérateur `new` et la syntaxe d’initialiseur d’objet :

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Destruction des instances de type

Vous n’êtes pas obligé de détruire les instances de type précédemment créées. Les instances de types référence et valeur sont détruites automatiquement. Les instances de types valeur sont détruites dès que le contexte dans lequel elles se trouvent est détruit. Les instances de types référence sont détruites par le [garbage collector](../../../standard/garbage-collection/index.md) à une heure non spécifiée après la suppression de la dernière référence.

Pour les instances de type qui contiennent des ressources non managées, par exemple, un descripteur de fichier, il est recommandé d’utiliser le nettoyage déterministe pour s’assurer que les ressources qu’ils contiennent sont libérées dès que possible. Pour plus d’informations, consultez la référence d’API <xref:System.IDisposable?displayProperty=nameWithType> et l’article [using, instruction](../keywords/using-statement.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur ne peut pas surcharger l’opérateur `new`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Opérateur new](~/_csharplang/spec/expressions.md#the-new-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur une expression de type cible `new` , consultez la [Remarque relative](~/_csharplang/proposals/csharp-9.0/target-typed-new.md)à la proposition de fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [Initialiseurs d’objets et de collections](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
