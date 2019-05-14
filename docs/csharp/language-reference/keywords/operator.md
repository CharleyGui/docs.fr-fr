---
title: opérateur, mot clé - Référence C#
ms.custom: seodec18
description: Découvrez comment surcharger un opérateur C# intégré
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 47ce91c343092ac2f7555c1edf3418527776e131
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754760"
---
# <a name="operator-c-reference"></a>operator (référence C#)

Utilisez le mot clé `operator` pour surcharger un opérateur intégré ou pour fournir une conversion définie par l’utilisateur dans une déclaration class ou struct.

Pour surcharger un opérateur sur une classe ou un struct personnalisé, créez une déclaration d’opérateur dans le type correspondant. La déclaration d’opérateur qui surcharge un opérateur C# intégré doit respecter les règles suivantes :

- Elle contient un modificateur `public` et un modificateur `static`.
- Elle contient `operator X`, où `X` est le nom ou le symbole de l’opérateur surchargé.
- Les opérateurs unaires ont un seul paramètre et les opérateurs binaires en ont deux. Dans chaque cas, au moins un paramètre doit être du même type que la classe ou le struct qui déclare l’opérateur.

Pour plus d’informations sur la définition d’opérateurs de conversion, consultez les articles sur les mots clés [explicit](explicit.md) et [implicit](implicit.md).

Pour avoir une vue d’ensemble des opérateurs C# qui peuvent être surchargés, consultez l’article [Opérateurs surchargeables](../../programming-guide/statements-expressions-operators/overloadable-operators.md).

## <a name="example"></a>Exemple

L’exemple suivant définit un type `Fraction` qui représente des nombres fractionnaires. Cette classe surcharge les opérateurs `+` et `*` pour effectuer des opérations d’addition et de multiplication fractionnaires. Elle fournit également un opérateur de conversion qui convertit un type `Fraction` en type `double`.

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [Opérateurs surchargeables](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
