---
title: Opérateurs de conversion définie par l’utilisateur - Référence C#
description: Découvrez comment définir des conversions de type implicites et explicites personnalisées en C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 8788883a6c60032de2ffab658fcf2721654fc6f7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566676"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Opérateurs de conversion définie par l’utilisateur (Référence C#)

Un type défini par l’utilisateur peut définir une conversion implicite ou explicite personnalisée depuis ou vers un autre type.

Les conversions implicites ne nécessitent pas une syntaxe spéciale à appeler et peuvent se produire dans diverses situations, par exemple, dans les appels de méthodes et les affectations. Les conversions implicites C# prédéfinies réussissent toujours et ne lèvent jamais d’exception ni ne perdent d’informations. Les conversions implicites définies par l’utilisateur doivent aussi se comporter de cette façon. Si une conversion personnalisée peut lever une exception ou perdre des informations, définissez-la comme conversion explicite.

Les conversions définies par l’utilisateur ne sont pas prises en compte par les opérateurs [is](type-testing-and-cast.md#is-operator) et [as](type-testing-and-cast.md#as-operator). Utilisez l’[opérateur de cast ()](type-testing-and-cast.md#cast-operator-) pour appeler une conversion explicite définie par l’utilisateur.

Utilisez les mots clés `operator` et `implicit` ou `explicit` pour définir une conversion implicite ou explicite, respectivement. Le type qui définit une conversion doit être un type source ou un type cible de cette conversion. Une conversion entre deux types définis par l’utilisateur peut être définie dans l’un ou l’autre des deux types.

L'exemple suivant montre comment définir une conversion implicite et explicite :

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

Utilisez également le mot clé `operator` pour surcharger un opérateur C# prédéfini. Pour plus d’informations, consultez [Surcharge d’opérateur](operator-overloading.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Opérateurs de conversion](~/_csharplang/spec/classes.md#conversion-operators)
- [Conversions définies par l’utilisateur](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Conversions implicites](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Conversions explicites](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Surcharge d’opérateur](operator-overloading.md)
- [Opérateurs de test et de cast de type](type-testing-and-cast.md)
- [Cast et conversion de types](../../programming-guide/types/casting-and-type-conversions.md)
- [Conversions explicites définies par l’utilisateur chaînées en C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
