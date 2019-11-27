---
title: Exit, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345935"
---
# <a name="exit-statement-visual-basic"></a>Exit, instruction (Visual Basic)

Quitte une procédure ou un bloc et transfère immédiatement le contrôle à l’instruction qui suit l’appel de procédure ou la définition de bloc.

## <a name="syntax"></a>Syntaxe

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>Instructions

 `Exit Do`  
 Quitte immédiatement la boucle de `Do` dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui suit l’instruction `Loop`. `Exit Do` ne peut être utilisé qu’à l’intérieur d’une boucle `Do`. Lorsqu’elle est utilisée dans des boucles `Do` imbriquées, `Exit Do` quitte la boucle la plus profonde et transfère le contrôle au niveau d’imbrication supérieur suivant.

 `Exit For`  
 Quitte immédiatement la boucle de `For` dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui suit l’instruction `Next`. `Exit For` ne peut être utilisé qu’à l’intérieur d’une boucle `For`...`Next` ou `For Each`...`Next`. Lorsqu’elle est utilisée dans des boucles `For` imbriquées, `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau d’imbrication supérieur suivant.

 `Exit Function`  
 Quitte immédiatement l' `Function` procédure dans laquelle il apparaît. L’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure `Function`. `Exit Function` ne peut être utilisé qu’à l’intérieur d’une procédure `Function`.

 Pour spécifier une valeur de retour, vous pouvez assigner la valeur au nom de la fonction sur une ligne avant l’instruction `Exit Function`. Pour affecter la valeur de retour et quitter la fonction dans une instruction, vous pouvez utiliser à la place l' [instruction return](return-statement.md).

 `Exit Property`  
 Quitte immédiatement l' `Property` procédure dans laquelle il apparaît. L’exécution se poursuit avec l’instruction qui a appelé la procédure `Property`, c’est-à-dire avec l’instruction qui demande ou définit la valeur de la propriété. `Exit Property` ne peut être utilisé qu’à l’intérieur d’une procédure `Get` ou `Set` d’une propriété.

 Pour spécifier une valeur de retour dans une procédure `Get`, vous pouvez assigner la valeur au nom de la fonction sur une ligne avant l’instruction `Exit Property`. Pour affecter la valeur de retour et quitter la procédure `Get` dans une instruction, vous pouvez utiliser à la place l’instruction `Return`.

 Dans une procédure `Set`, l’instruction `Exit Property` est équivalente à l’instruction `Return`.

 `Exit Select`  
 Quitte immédiatement le bloc `Select Case` dans lequel il apparaît. L’exécution se poursuit avec l’instruction qui suit l’instruction `End Select`. `Exit Select` ne peut être utilisé qu’à l’intérieur d’une instruction `Select Case`.

 `Exit Sub`  
 Quitte immédiatement l' `Sub` procédure dans laquelle il apparaît. L’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure `Sub`. `Exit Sub` ne peut être utilisé qu’à l’intérieur d’une procédure `Sub`.

 Dans une procédure `Sub`, l’instruction `Exit Sub` est équivalente à l’instruction `Return`.

 `Exit Try`  
 Quitte immédiatement le bloc `Try` ou `Catch` dans lequel il apparaît. L’exécution se poursuit avec le bloc `Finally`, le cas échéant, ou avec l’instruction qui suit l’instruction `End Try` dans le cas contraire. `Exit Try` ne peut être utilisé qu’à l’intérieur d’un bloc `Try` ou `Catch`, et non à l’intérieur d’un bloc `Finally`.

 `Exit While`  
 Quitte immédiatement la boucle de `While` dans laquelle elle apparaît. L’exécution se poursuit avec l’instruction qui suit l’instruction `End While`. `Exit While` ne peut être utilisé qu’à l’intérieur d’une boucle `While`. Lorsqu’il est utilisé dans des boucles `While` imbriquées, `Exit While` transfère le contrôle à la boucle qui est un niveau imbriqué au-dessus de la boucle où `Exit While` se produit.

## <a name="remarks"></a>Notes

Ne confondez pas `Exit` instructions avec des instructions `End`. `Exit` ne définit pas la fin d’une instruction.

## <a name="example"></a>Exemple

Dans l’exemple suivant, la condition de boucle arrête la boucle lorsque la `index` variable est supérieure à 100. Toutefois, l’instruction `If` dans la boucle entraîne l’arrêt de la boucle par l’instruction `Exit Do` quand la variable d’index est supérieure à 10.

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>Exemple

L’exemple suivant affecte la valeur de retour au nom de la fonction `myFunction`, puis utilise `Exit Function` pour retourner à partir de la fonction :

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a>Exemple

L’exemple suivant utilise l' [instruction return](return-statement.md) pour assigner la valeur de retour et quitter la fonction :

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a>Voir aussi

- [Continue (instruction)](continue-statement.md)
- [Do...Loop (instruction)](do-loop-statement.md)
- [End (instruction)](end-statement.md)
- [For Each...Next (instruction)](for-each-next-statement.md)
- [For...Next (instruction)](for-next-statement.md)
- [Function (instruction)](function-statement.md)
- [Return (instruction)](return-statement.md)
- [Stop (instruction)](stop-statement.md)
- [Sub (instruction)](sub-statement.md)
- [Try...Catch...Finally (instruction)](try-catch-finally-statement.md)
