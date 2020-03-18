---
title: 'Comment : lever explicitement des exceptions'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 750da20b8c1c40901cc363ac0eff8af888821ce9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708860"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="939f8-102">Guide pratique pour lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="939f8-102">How to explicitly throw exceptions</span></span>

<span data-ttu-id="939f8-103">Vous pouvez explicitement lancer une [`throw`](../../csharp/language-reference/keywords/throw.md) exception à [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) l’aide de la déclaration de base visuelle ou de C.</span><span class="sxs-lookup"><span data-stu-id="939f8-103">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="939f8-104">Vous pouvez aussi lever de nouveau une exception interceptée à l’aide de l’instruction `throw`.</span><span class="sxs-lookup"><span data-stu-id="939f8-104">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="939f8-105">En codage, il est conseillé d’ajouter des informations à une exception levée une deuxième fois pour fournir plus d’informations durant le débogage.</span><span class="sxs-lookup"><span data-stu-id="939f8-105">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="939f8-106">L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception <xref:System.IO.FileNotFoundException> possible.</span><span class="sxs-lookup"><span data-stu-id="939f8-106">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="939f8-107">À la suite du bloc `try`, un bloc `catch` intercepte l’exception <xref:System.IO.FileNotFoundException> et écrit un message dans la console si le fichier de données est introuvable.</span><span class="sxs-lookup"><span data-stu-id="939f8-107">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="939f8-108">L’instruction suivante est `throw`, qui lève une nouvelle exception <xref:System.IO.FileNotFoundException> et ajoute des informations de texte à l’exception.</span><span class="sxs-lookup"><span data-stu-id="939f8-108">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="939f8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="939f8-109">See also</span></span>

- [<span data-ttu-id="939f8-110">Exceptions</span><span class="sxs-lookup"><span data-stu-id="939f8-110">Exceptions</span></span>](index.md)
