---
title: Stop, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957618"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="ec62b-102">Stop, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec62b-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="ec62b-103">Interrompt l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ec62b-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec62b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec62b-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="ec62b-105">Notes</span><span class="sxs-lookup"><span data-stu-id="ec62b-105">Remarks</span></span>  
 <span data-ttu-id="ec62b-106">Vous pouvez placer `Stop` des instructions n’importe où dans les procédures pour interrompre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ec62b-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="ec62b-107">L’utilisation `Stop` de l’instruction revient à définir un point d’arrêt dans le code.</span><span class="sxs-lookup"><span data-stu-id="ec62b-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="ec62b-108">L' `Stop` instruction interrompt l’exécution, mais `End`contrairement à, elle ne ferme pas les fichiers ou n’efface aucune variable, sauf si elle est rencontrée dans un fichier exécutable (. exe) compilé.</span><span class="sxs-lookup"><span data-stu-id="ec62b-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec62b-109">Si l' `Stop` instruction est rencontrée dans le code qui s’exécute en dehors de l’environnement de développement intégré (IDE), le débogueur est appelé.</span><span class="sxs-lookup"><span data-stu-id="ec62b-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="ec62b-110">Cela est vrai que le code ait été compilé en mode de débogage ou de vente au détail.</span><span class="sxs-lookup"><span data-stu-id="ec62b-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec62b-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="ec62b-111">Example</span></span>  
 <span data-ttu-id="ec62b-112">L’exemple suivant utilise `Stop` l’instruction pour suspendre l’exécution de chaque itération `For...Next` à travers la boucle.</span><span class="sxs-lookup"><span data-stu-id="ec62b-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="ec62b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec62b-113">See also</span></span>

- [<span data-ttu-id="ec62b-114">End (instruction)</span><span class="sxs-lookup"><span data-stu-id="ec62b-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
