---
description: break, instruction - Référence C#
title: break, instruction - Référence C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134742"
---
# <a name="break-c-reference"></a>break (référence C#)

L’instruction `break` termine la boucle englobante ou l’instruction [switch](./switch.md) la plus proche dans laquelle elle figure. Le contrôle est passé à l’instruction qui suit l’instruction terminée, le cas échéant.

## <a name="example"></a>Exemple

Dans cet exemple, l’instruction conditionnelle contient un compteur qui est supposé compter de 1 à 100. Toutefois, l’instruction `break` termine la boucle après le chiffre 4.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Exemple

Cet exemple illustre l’utilisation de `break` dans une instruction [switch](./switch.md).

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Si vous aviez entré `4`, le résultat serait le suivant :

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Exemple

Dans cet exemple, l’instruction `break` est utilisée pour sortir d’une boucle imbriquée interne et passer le contrôle à la boucle externe. Le contrôle n’est retourné _qu'_ un niveau dans les boucles imbriquées.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Exemple

Dans cet exemple, l' `break` instruction est utilisée uniquement pour sortir de la branche active au cours de chaque itération de la boucle. La boucle elle-même n’est pas affectée par les instances de `break` qui appartiennent à l’instruction [switch](./switch.md) imbriquée.

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [switch](./switch.md)
