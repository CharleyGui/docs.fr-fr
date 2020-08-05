---
title: expression nameof-référence C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 1bd8800a553eb9b3363da8a3b5f230caecddf223
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556408"
---
# <a name="nameof-expression-c-reference"></a>nameof, expression (référence C#)

Une `nameof` expression produit le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Dans le cas des [identificateurs textuels](../tokens/verbatim.md), le `@` caractère n’est pas la partie d’un nom, comme le montre l’exemple suivant :

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

Une `nameof` expression est évaluée au moment de la compilation et n’a aucun effet au moment de l’exécution.

Vous pouvez utiliser une `nameof` expression pour rendre le code de vérification des arguments plus gérable :

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Une `nameof` expression est disponible en C# 6 et versions ultérieures.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
