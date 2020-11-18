---
title: 'Comment : lever explicitement des exceptions'
description: Apprenez à lever une exception explicitement dans .NET à l’aide de l’instruction throw C# ou de l’instruction Visual Basic throw.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 37ba5f952d621ff2e209a3bac375b62894c944a7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828047"
---
# <a name="how-to-explicitly-throw-exceptions"></a>Guide pratique pour lever explicitement des exceptions

Vous pouvez lever explicitement une exception à l’aide de l' [`throw`](../../csharp/language-reference/keywords/throw.md) instruction C# ou Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) . Vous pouvez aussi lever de nouveau une exception interceptée à l’aide de l’instruction `throw`. En codage, il est conseillé d’ajouter des informations à une exception levée une deuxième fois pour fournir plus d’informations durant le débogage.

L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception <xref:System.IO.FileNotFoundException> possible. À la suite du bloc `try`, un bloc `catch` intercepte l’exception <xref:System.IO.FileNotFoundException> et écrit un message dans la console si le fichier de données est introuvable. L’instruction suivante est `throw`, qui lève une nouvelle exception <xref:System.IO.FileNotFoundException> et ajoute des informations de texte à l’exception.

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
