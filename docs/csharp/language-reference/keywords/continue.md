---
description: continue, instruction - Référence C#
title: continue, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 6c70934c3b861e1a1433e5c0b95bb32e9d717c53
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877650"
---
# <a name="continue-c-reference"></a>continue (référence C#)

L’instruction `continue` passe le contrôle à l’itération suivante de l’instruction [while](./while.md), [do](./do.md), [for](./for.md) ou [foreach](./foreach-in.md) englobante dans laquelle elle apparaît.

## <a name="example"></a>Exemple

Dans cet exemple, un compteur est initialisé pour compter de 1 à 10. En utilisant l' `continue` instruction conjointement avec l’expression `(i < 9)` , les instructions entre `continue` et la fin du `for` corps sont ignorées dans les itérations où `i` est inférieur à 9. Au cours des deux dernières itérations de la `for` boucle (où i = = 9 et i = = 10), l' `continue` instruction n’est pas exécutée et la valeur de `i` est imprimée sur la console.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [Break (instruction)](/cpp/cpp/break-statement-cpp)
