---
title: Throw, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 9680700267f17c8e316de351fead61f1dc4aded0
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869022"
---
# <a name="throw-statement-visual-basic"></a>Throw, instruction (Visual Basic)

Lève une exception dans une procédure.

## <a name="syntax"></a>Syntaxe

```vb
Throw [ expression ]
```

## <a name="part"></a>Élément

`expression`\
Fournit des informations sur l’exception à lever. Facultatif lorsqu’il réside dans une `Catch` instruction, sinon requis.

## <a name="remarks"></a>Notes

L' `Throw` instruction lève une exception que vous pouvez gérer avec du code de gestion des exceptions structuré`Try`(... `Catch`... ) ou du code de gestion des exceptions non structuré`On Error GoTo`(). `Finally` Vous pouvez utiliser l' `Throw` instruction pour intercepter les erreurs dans votre code, car Visual Basic monte dans la pile des appels jusqu’à ce qu’il trouve le code de gestion des exceptions approprié.

Une `Throw` instruction sans expression ne peut être utilisée que dans une `Catch` instruction, auquel cas l’instruction lève à nouveau l’exception en cours de traitement par l' `Catch` instruction.

L' `Throw` instruction réinitialise la pile des appels pour l' `expression` exception. Si `expression` n’est pas fourni, la pile des appels reste inchangée. Vous pouvez accéder à la pile des appels pour l’exception <xref:System.Exception.StackTrace%2A> via la propriété.

## <a name="example"></a>Exemples

Le code suivant utilise l' `Throw` instruction pour lever une exception:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Voir aussi

- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error (instruction)](../../../visual-basic/language-reference/statements/on-error-statement.md)
