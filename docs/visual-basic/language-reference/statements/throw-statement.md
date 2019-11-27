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
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="f2f47-102">Throw, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f47-102">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="f2f47-103">Lève une exception dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="f2f47-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2f47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2f47-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="f2f47-105">Élément</span><span class="sxs-lookup"><span data-stu-id="f2f47-105">Part</span></span>

`expression`\
<span data-ttu-id="f2f47-106">Fournit des informations sur l’exception à lever.</span><span class="sxs-lookup"><span data-stu-id="f2f47-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="f2f47-107">Facultatif lorsqu’il réside dans une instruction `Catch`, sinon requis.</span><span class="sxs-lookup"><span data-stu-id="f2f47-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2f47-108">Notes</span><span class="sxs-lookup"><span data-stu-id="f2f47-108">Remarks</span></span>

<span data-ttu-id="f2f47-109">L’instruction `Throw` lève une exception que vous pouvez gérer avec du code de gestion des exceptions structurées (`Try`...`Catch`...`Finally`) ou du code de gestion des exceptions non structuré (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="f2f47-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="f2f47-110">Vous pouvez utiliser l’instruction `Throw` pour intercepter les erreurs dans votre code, car Visual Basic monte dans la pile des appels jusqu’à ce qu’il trouve le code de gestion des exceptions approprié.</span><span class="sxs-lookup"><span data-stu-id="f2f47-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="f2f47-111">Une instruction `Throw` sans expression ne peut être utilisée que dans une instruction `Catch`. dans ce cas, l’instruction lève à nouveau l’exception en cours de traitement par l’instruction `Catch`.</span><span class="sxs-lookup"><span data-stu-id="f2f47-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="f2f47-112">L’instruction `Throw` réinitialise la pile des appels pour l’exception `expression`.</span><span class="sxs-lookup"><span data-stu-id="f2f47-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="f2f47-113">Si `expression` n’est pas fourni, la pile des appels reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="f2f47-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="f2f47-114">Vous pouvez accéder à la pile des appels pour l’exception via la propriété <xref:System.Exception.StackTrace%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2f47-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="f2f47-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2f47-115">Example</span></span>

<span data-ttu-id="f2f47-116">Le code suivant utilise l’instruction `Throw` pour lever une exception :</span><span class="sxs-lookup"><span data-stu-id="f2f47-116">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="f2f47-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2f47-117">See also</span></span>

- [<span data-ttu-id="f2f47-118">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="f2f47-118">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="f2f47-119">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="f2f47-119">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
