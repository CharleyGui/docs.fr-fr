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
ms.openlocfilehash: 95572b1739490e90f53da6b6ec283bfb532c46d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404133"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="2b6ae-102">Throw, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b6ae-102">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="2b6ae-103">Lève une exception dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="2b6ae-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b6ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b6ae-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="2b6ae-105">Élément</span><span class="sxs-lookup"><span data-stu-id="2b6ae-105">Part</span></span>

`expression`\
<span data-ttu-id="2b6ae-106">Fournit des informations sur l’exception à lever.</span><span class="sxs-lookup"><span data-stu-id="2b6ae-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="2b6ae-107">Facultatif lorsqu’il réside dans une `Catch` instruction, sinon requis.</span><span class="sxs-lookup"><span data-stu-id="2b6ae-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b6ae-108">Notes</span><span class="sxs-lookup"><span data-stu-id="2b6ae-108">Remarks</span></span>

<span data-ttu-id="2b6ae-109">L' `Throw` instruction lève une exception que vous pouvez gérer avec du code de gestion des exceptions structuré ( `Try` ... `Catch` ...`Finally`) ou du code de gestion des exceptions non structuré ( `On Error GoTo` ).</span><span class="sxs-lookup"><span data-stu-id="2b6ae-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="2b6ae-110">Vous pouvez utiliser l' `Throw` instruction pour intercepter les erreurs dans votre code, car Visual Basic monte dans la pile des appels jusqu’à ce qu’il trouve le code de gestion des exceptions approprié.</span><span class="sxs-lookup"><span data-stu-id="2b6ae-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="2b6ae-111">Une `Throw` instruction sans expression ne peut être utilisée que dans une `Catch` instruction, auquel cas l’instruction lève à nouveau l’exception en cours de traitement par l' `Catch` instruction.</span><span class="sxs-lookup"><span data-stu-id="2b6ae-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="2b6ae-112">L' `Throw` instruction réinitialise la pile des appels pour l' `expression` exception.</span><span class="sxs-lookup"><span data-stu-id="2b6ae-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="2b6ae-113">Si `expression` n’est pas fourni, la pile des appels reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="2b6ae-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="2b6ae-114">Vous pouvez accéder à la pile des appels pour l’exception via la <xref:System.Exception.StackTrace%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="2b6ae-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="2b6ae-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b6ae-115">Example</span></span>

<span data-ttu-id="2b6ae-116">Le code suivant utilise l' `Throw` instruction pour lever une exception :</span><span class="sxs-lookup"><span data-stu-id="2b6ae-116">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="2b6ae-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b6ae-117">See also</span></span>

- [<span data-ttu-id="2b6ae-118">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="2b6ae-118">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="2b6ae-119">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="2b6ae-119">On Error Statement</span></span>](on-error-statement.md)
