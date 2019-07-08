---
title: implicit - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 00fe1a02b52ef2ddc393bc7424efa73fc4059a9c
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610109"
---
# <a name="implicit-c-reference"></a>implicit (référence C#)

Le mot clé `implicit` est utilisé pour déclarer un opérateur de conversion de type implicite défini par l’utilisateur. Utilisez-le pour permettre les conversions implicites entre un type défini par l’utilisateur et un autre type, si la conversion n’est pas susceptible de provoquer une perte de données.

## <a name="example"></a>Exemples

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

En éliminant les casts de type superflus, les conversions implicites peuvent améliorer la lisibilité du code source. Toutefois, étant donné que les conversions implicites ne nécessitent pas que les programmeurs castent explicitement d’un type à un autre, il faut veiller à éviter les résultats inattendus. En général, les opérateurs de conversion implicite ne doivent jamais lever d’exceptions ni perdre d’informations pour pouvoir être utilisés en toute sécurité à l’insu du programmeur. Si un opérateur de conversion ne peut pas répondre à ces critères, il doit être marqué comme `explicit`. Pour plus d’informations, consultez [Utilisation d’opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [explicit](explicit.md)
- [Surcharge d’opérateur](../operators/operator-overloading.md)
- [Guide pratique pour implémenter des conversions définies par l’utilisateur entre des structs](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
