---
title: Throw, instruction
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
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352782"
---
# <a name="throw-statement-visual-basic"></a>Throw, instruction (Visual Basic)

Lève une exception dans une procédure.

## <a name="syntax"></a>Syntaxe

```vb
Throw [ expression ]
```

## <a name="part"></a>Élément

`expression`\
Fournit des informations sur l’exception à lever. Facultatif lorsqu’il réside dans une instruction `Catch`, sinon requis.

## <a name="remarks"></a>Notes

L’instruction `Throw` lève une exception que vous pouvez gérer avec du code de gestion des exceptions structurées (`Try`...`Catch`...`Finally`) ou du code de gestion des exceptions non structuré (`On Error GoTo`). Vous pouvez utiliser l’instruction `Throw` pour intercepter les erreurs dans votre code, car Visual Basic monte dans la pile des appels jusqu’à ce qu’il trouve le code de gestion des exceptions approprié.

Une instruction `Throw` sans expression ne peut être utilisée que dans une instruction `Catch`. dans ce cas, l’instruction lève à nouveau l’exception en cours de traitement par l’instruction `Catch`.

L’instruction `Throw` réinitialise la pile des appels pour l’exception `expression`. Si `expression` n’est pas fourni, la pile des appels reste inchangée. Vous pouvez accéder à la pile des appels pour l’exception via la propriété <xref:System.Exception.StackTrace%2A>.

## <a name="example"></a>Exemple

Le code suivant utilise l’instruction `Throw` pour lever une exception :

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Voir aussi

- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error (instruction)](../../../visual-basic/language-reference/statements/on-error-statement.md)
