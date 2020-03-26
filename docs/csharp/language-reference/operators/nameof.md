---
title: nameof expression - Référence C
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507137"
---
# <a name="nameof-expression-c-reference"></a>nameof expression (référence C)

Une `nameof` expression produit le nom d’une variable, d’un type ou d’un membre comme constante de la chaîne :

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Comme le montre l’exemple précédent, dans le cas d’un type et d’un espace de noms, le nom produit n’est généralement pas [complet](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Une `nameof` expression est évaluée au moment de la compilation et n’a aucun effet au moment de l’exécution.

Vous pouvez `nameof` utiliser une expression pour rendre le code de vérification des arguments plus maintenable :

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Une `nameof` expression est disponible en C 6 et plus tard.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Expressions Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
