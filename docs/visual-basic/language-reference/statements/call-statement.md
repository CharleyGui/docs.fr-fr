---
title: Call, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: a04ebddc7db176188876da1082e1e6946e1e8eec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005171"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="4f6c2-102">Call, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f6c2-102">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="4f6c2-103">Transfère le contrôle à une procédure `Function`, `Sub` ou de bibliothèque de liens dynamiques (DLL).</span><span class="sxs-lookup"><span data-stu-id="4f6c2-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f6c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f6c2-104">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="4f6c2-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4f6c2-105">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="4f6c2-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-106">Required.</span></span> <span data-ttu-id="4f6c2-107">Nom de la procédure à appeler.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="4f6c2-108">facultatif.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-108">Optional.</span></span> <span data-ttu-id="4f6c2-109">Liste de variables ou d’expressions représentant les arguments passés à la procédure quand elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="4f6c2-110">Les arguments multiples sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="4f6c2-111">Si vous incluez `argumentList`, vous devez le placer entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="4f6c2-112">Notes</span><span class="sxs-lookup"><span data-stu-id="4f6c2-112">Remarks</span></span>

 <span data-ttu-id="4f6c2-113">Vous pouvez utiliser le mot clé `Call` lorsque vous appelez une procédure.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="4f6c2-114">Pour la plupart des appels de procédure, vous n’êtes pas obligé d’utiliser ce mot clé.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="4f6c2-115">En général, vous utilisez le mot clé `Call` lorsque l’expression appelée ne commence pas par un identificateur.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="4f6c2-116">L’utilisation du mot clé `Call` pour les autres utilisations n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-116">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="4f6c2-117">Si la procédure retourne une valeur, l’instruction `Call` l’ignore.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-117">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="4f6c2-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="4f6c2-118">Example</span></span>

 <span data-ttu-id="4f6c2-119">Le code suivant montre deux exemples où le mot clé `Call` est nécessaire pour appeler une procédure.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="4f6c2-120">Dans les deux exemples, l’expression appelée ne commence pas par un identificateur.</span><span class="sxs-lookup"><span data-stu-id="4f6c2-120">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="4f6c2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f6c2-121">See also</span></span>

- [<span data-ttu-id="4f6c2-122">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="4f6c2-122">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="4f6c2-123">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="4f6c2-123">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="4f6c2-124">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="4f6c2-124">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="4f6c2-125">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="4f6c2-125">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
