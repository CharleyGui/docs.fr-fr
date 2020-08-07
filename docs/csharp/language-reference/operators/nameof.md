---
title: expression nameof-référence C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: b00c5f6f97d27290fb3773dcbb422bf9fb4c425b
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916782"
---
# <a name="nameof-expression-c-reference"></a>nameof, expression (référence C#)

Une `nameof` expression produit le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Dans le cas des [identificateurs textuels](../tokens/verbatim.md), le `@` caractère n’est pas la partie d’un nom, comme le montre l’exemple suivant :

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

Une `nameof` expression est évaluée au moment de la compilation et n’a aucun effet au moment de l’exécution.

Vous pouvez utiliser une `nameof` expression pour rendre le code de vérification des arguments plus gérable :

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

Une `nameof` expression est disponible en C# 6 et versions ultérieures.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
