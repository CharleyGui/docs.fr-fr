---
title: do - Référence C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: d75dd816278a876fa05d133e5eb189d606300a5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401925"
---
# <a name="do-c-reference"></a>do (référence C#)

L’instruction `do` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`. Dans la mesure où cette expression est évaluée après chaque exécution de la boucle, une boucle `do-while` s’exécute une ou plusieurs fois. Cela diffère de la boucle [while](while.md), qui s’exécute zéro ou plusieurs fois.

À tout moment dans le bloc d’instructions `do`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md).

Vous pouvez passer directement à l’évaluation de l’expression `while` à l’aide de l’instruction [continue](continue.md). Si l’expression correspond à `true`, l’exécution passe à la première instruction de la boucle. Sinon, l’exécution passe à la première instruction après la boucle.

Vous pouvez également quitter une `do-while` boucle à l’aide des instructions [goto](goto.md), [Return](return.md)ou [throw](throw.md) .

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de l’instruction `do`. Sélectionnez **Exécuter** pour exécuter l’exemple de code. Après cela, vous pouvez modifier le code et le réexécuter.

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Instruction do](~/_csharplang/spec/statements.md#the-do-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [while, instruction](while.md)
