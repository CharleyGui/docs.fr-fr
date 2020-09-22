---
description: opérateur délégué - Référence C#
title: opérateur délégué - Référence C#
ms.date: 09/22/2020
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 6c087d9bdb2f526cf7d94c3a0f2c1a929b0343ef
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874911"
---
# <a name="delegate-operator-c-reference"></a>opérateur délégué (Référence C#)

L’opérateur `delegate` crée une méthode anonyme qui peut être convertie en un type délégué :

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> À partir C# 3, les expressions lambda offrent un moyen plus concis et plus expressif de créer une fonction anonyme. Utilisez [=> opérateur](lambda-operator.md) pour construire une expression lambda :
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> Pour plus d’informations sur les fonctionnalités des expressions lambda, par exemple la capture de variables externes, consultez [Expressions lambda](lambda-expressions.md).

Lorsque vous utilisez l’opérateur `delegate`, vous pouvez omettre la liste de paramètres. Dans ce cas, la méthode anonyme créée peut être convertie en un type délégué avec n’importe quelle liste de paramètres, comme le montre l’exemple suivant :

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

C’est la seule fonctionnalité des méthodes anonymes qui n’est pas prise en charge par les expressions lambda. Dans tous les autres cas, une expression lambda est le moyen préféré pour écrire du code incorporé.

À compter de C# 9,0, vous pouvez utiliser des éléments [ignorés](../../discards.md) pour spécifier au moins deux paramètres d’entrée d’une méthode anonyme qui ne sont pas utilisés par la méthode :

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetDiscards" :::

À des fins de compatibilité descendante, si un seul paramètre est nommé `_` , `_` est traité comme le nom de ce paramètre dans une méthode anonyme.

Vous utilisez également le mot clé `delegate` pour déclarer un [type délégué](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Expressions de fonction anonyme](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [=> opérateur](lambda-operator.md)
