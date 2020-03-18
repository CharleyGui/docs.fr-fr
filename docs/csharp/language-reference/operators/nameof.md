---
title: opérateur nameof - Référence C#
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846270"
---
# <a name="nameof-operator-c-reference"></a>opérateur nameof (Référence C#)

L’opérateur `nameof` obtient le nom d’une variable, d’un type ou d’un membre en tant que constante de chaîne :

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

L’opérateur `nameof` est évalué au moment de la compilation et n’a aucun effet au moment de l’exécution.

Vous pouvez utiliser l’opérateur `nameof` pour rendre le code de vérification des arguments plus gérable :

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

L’opérateur `nameof` est disponible dans les versions 6 et ultérieures de C#.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
