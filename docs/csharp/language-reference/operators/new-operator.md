---
title: new, opérateur - Référence C#
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: beb55f0765e7f9090f0587f1d2a06cf03ea90ab8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712661"
---
# <a name="new-operator-c-reference"></a>new, opérateur (Référence C#)

L’opérateur `new` crée une nouvelle instance d’un type.

Vous pouvez également utiliser le mot clé `new` comme [modificateur de déclaration de membre](../keywords/new-modifier.md) ou [contrainte de type générique](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Appel du constructeur

Pour créer une nouvelle instance d’un type, vous appelez généralement l’un des [constructeurs](../../programming-guide/classes-and-structs/constructors.md) de ce type, à l’aide de l’opérateur `new` :

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

Vous pouvez utiliser un [initialiseur d’objet ou de collection](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) avec l’opérateur `new` pour instancier et initialiser un objet dans une instruction, comme dans l’exemple suivant :

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Création de tableau

Vous utilisez également l’opérateur `new` pour créer une instance de tableau, comme dans l’exemple suivant :

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

Utilisez la syntaxe d’initialisation de tableau pour créer une instance de tableau et la remplir avec des éléments dans une instruction. L’exemple suivant montre différentes façons de procéder :

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

Pour plus d’informations sur les tableaux, consultez [Tableaux](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Instanciation des types anonymes

Pour créer une instance d’un [type anonyme](../../programming-guide/classes-and-structs/anonymous-types.md), utilisez l’opérateur `new` et la syntaxe d’initialiseur d’objet :

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Destruction des instances de type

Vous n’êtes pas obligé de détruire les instances de type précédemment créées. Les instances de types référence et valeur sont détruites automatiquement. Les instances de types valeur sont détruites dès que le contexte dans lequel elles se trouvent est détruit. Les instances de types référence sont détruites par le [récupérateur de mémoire](../../../standard/garbage-collection/index.md) à un moment non spécifié, après la suppression de la dernière référence à celles-ci.

Pour les instances de type qui contiennent des ressources non managées, par exemple, un descripteur de fichier, il est recommandé d’utiliser le nettoyage déterministe pour s’assurer que les ressources qu’ils contiennent sont libérées dès que possible. Pour plus d’informations, consultez la référence d’API <xref:System.IDisposable?displayProperty=nameWithType> et l’article [using, instruction](../keywords/using-statement.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur ne peut pas surcharger l’opérateur `new`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Opérateur new](~/_csharplang/spec/expressions.md#the-new-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Initialiseurs d’objets et de collections](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
