---
title: End, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: fe17a82662c4014069c77f2da76723a051ab9084
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404704"
---
# <a name="end-statement"></a><span data-ttu-id="dd674-102">End, instruction</span><span class="sxs-lookup"><span data-stu-id="dd674-102">End Statement</span></span>
<span data-ttu-id="dd674-103">Termine immédiatement l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dd674-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd674-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd674-104">Syntax</span></span>  
  
```vb  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="dd674-105">Notes</span><span class="sxs-lookup"><span data-stu-id="dd674-105">Remarks</span></span>  
 <span data-ttu-id="dd674-106">Vous pouvez placer l' `End` instruction n’importe où dans une procédure pour forcer l’arrêt de l’exécution de l’application entière.</span><span class="sxs-lookup"><span data-stu-id="dd674-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="dd674-107">`End`ferme tous les fichiers ouverts avec une `Open` instruction et efface toutes les variables de l’application.</span><span class="sxs-lookup"><span data-stu-id="dd674-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="dd674-108">L’application se ferme dès qu’aucun autre programme ne contient des références à ses objets et qu’aucun de son code n’est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="dd674-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd674-109">L' `End` instruction arrête l’exécution du code brusquement et n’appelle pas `Dispose` la `Finalize` méthode ou, ni tout autre Visual Basic de code.</span><span class="sxs-lookup"><span data-stu-id="dd674-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="dd674-110">Les références d’objets détenues par d’autres programmes sont invalidées.</span><span class="sxs-lookup"><span data-stu-id="dd674-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="dd674-111">Si une `End` instruction est rencontrée dans `Try` un `Catch` bloc ou, le contrôle ne passe pas au `Finally` bloc correspondant.</span><span class="sxs-lookup"><span data-stu-id="dd674-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="dd674-112">L' `Stop` instruction interrompt l’exécution, mais contrairement `End` à, elle ne ferme pas les fichiers ou n’efface aucune variable, sauf si elle est rencontrée dans un fichier exécutable (. exe) compilé.</span><span class="sxs-lookup"><span data-stu-id="dd674-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="dd674-113">Étant donné que `End` met fin à votre application sans vous préoccuper des ressources qui peuvent être ouvertes, vous devez essayer de la fermer correctement avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="dd674-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="dd674-114">Par exemple, si des formulaires sont ouverts sur votre application, vous devez les fermer avant que le contrôle n’atteigne l' `End` instruction.</span><span class="sxs-lookup"><span data-stu-id="dd674-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="dd674-115">Vous devez utiliser `End` avec modération et uniquement lorsque vous devez arrêter immédiatement.</span><span class="sxs-lookup"><span data-stu-id="dd674-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="dd674-116">Les méthodes normales pour mettre fin à une procédure ([instruction de retour](return-statement.md) et [instruction de sortie](exit-statement.md)) ferment uniquement la procédure proprement dit, mais elles permettent également au code appelant de fermer correctement.</span><span class="sxs-lookup"><span data-stu-id="dd674-116">The normal ways to terminate a procedure ([Return Statement](return-statement.md) and [Exit Statement](exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="dd674-117">Une application console, par exemple, peut simplement être `Return` à partir de la `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="dd674-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dd674-118">L' `End` instruction appelle la <xref:System.Environment.Exit%2A> méthode de la <xref:System.Environment> classe dans l' <xref:System> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="dd674-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="dd674-119"><xref:System.Environment.Exit%2A>requiert que vous disposiez d’une `UnmanagedCode` autorisation.</span><span class="sxs-lookup"><span data-stu-id="dd674-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="dd674-120">Si vous ne le faites pas, une <xref:System.Security.SecurityException> erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="dd674-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="dd674-121">Lorsqu’il est suivi d’un mot clé supplémentaire, [End \<keyword> Statement](end-keyword-statement.md) délimite la fin de la définition de la procédure ou du bloc approprié.</span><span class="sxs-lookup"><span data-stu-id="dd674-121">When followed by an additional keyword, [End \<keyword> Statement](end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="dd674-122">Par exemple, `End Function` termine la définition d’une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="dd674-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd674-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd674-123">Example</span></span>  
 <span data-ttu-id="dd674-124">L’exemple suivant utilise l' `End` instruction pour mettre fin à l’exécution du code si l’utilisateur le demande.</span><span class="sxs-lookup"><span data-stu-id="dd674-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="dd674-125">Notes de développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="dd674-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="dd674-126">Cette instruction n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="dd674-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd674-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd674-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="dd674-128">Stop (instruction)</span><span class="sxs-lookup"><span data-stu-id="dd674-128">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="dd674-129">End ( \<keyword> instruction)</span><span class="sxs-lookup"><span data-stu-id="dd674-129">End \<keyword> Statement</span></span>](end-keyword-statement.md)
