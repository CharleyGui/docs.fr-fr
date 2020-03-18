---
title: while - Référence C#
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: eb9aa2ea8d6b1c96e0be7d377f7c047194b598de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712791"
---
# <a name="while-c-reference"></a>while (référence C#)

L’instruction `while` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`. Dans la mesure où cette expression est évaluée avant chaque exécution de la boucle, une boucle `while` s’exécute plusieurs fois ou pas du tout. Cela diffère de la boucle [do](do.md), qui s’exécute une ou plusieurs fois.

À tout moment dans le bloc d’instructions `while`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md).

Vous pouvez passer directement à l’évaluation de l’expression `while` à l’aide de l’instruction [continue](continue.md). Si l’expression correspond à `true`, l’exécution passe à la première instruction de la boucle. Sinon, l’exécution passe à la première instruction après la boucle.

Vous pouvez également quitter une boucle `while` en utilisant les instructions [goto](goto.md), [return](return.md) ou [throw](throw.md).

## <a name="example"></a> Exemple

L’exemple suivant illustre l’utilisation de l’instruction `while`. Sélectionnez **Exécuter** pour exécuter l’exemple de code. Après cela, vous pouvez modifier le code et le réexécuter.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Instruction while](~/_csharplang/spec/statements.md#the-while-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [faire déclaration](do.md)
