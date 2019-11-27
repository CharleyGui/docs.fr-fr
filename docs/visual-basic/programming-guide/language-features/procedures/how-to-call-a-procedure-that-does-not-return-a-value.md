---
title: 'Comment : appeler une procédure qui ne retourne pas de valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 3a5de98c6edf795a11bd9f0465aa6919f09eebfa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340956"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="d4bf1-102">Comment : appeler une procédure qui ne retourne pas de valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4bf1-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="d4bf1-103">Une procédure `Sub` ne retourne pas de valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="d4bf1-104">Vous l’appelez explicitement avec une instruction d’appel autonome.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="d4bf1-105">Vous ne pouvez pas l’appeler en utilisant simplement son nom dans une expression.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="d4bf1-106">Pour appeler une procédure Sub</span><span class="sxs-lookup"><span data-stu-id="d4bf1-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="d4bf1-107">Spécifiez le nom de la procédure `Sub`.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="d4bf1-108">Faites suivre le nom de la procédure de parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d4bf1-109">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="d4bf1-110">Toutefois, l’utilisation de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="d4bf1-111">Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d4bf1-112">Veillez à fournir les arguments dans l’ordre dans lequel la procédure `Sub` définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="d4bf1-113">L’exemple suivant appelle la fonction <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> Visual Basic pour activer une fenêtre d’application.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="d4bf1-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> prend le titre de la fenêtre comme seul argument.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="d4bf1-115">Elle ne retourne pas de valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="d4bf1-116">Si un processus Notepad n’est pas en cours d’exécution, l’exemple lève une <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="d4bf1-117">La procédure `Shell` suppose que les applications se trouvent dans les chemins d’accès spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d4bf1-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="d4bf1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4bf1-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="d4bf1-119">Procédures</span><span class="sxs-lookup"><span data-stu-id="d4bf1-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d4bf1-120">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="d4bf1-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="d4bf1-121">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="d4bf1-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d4bf1-122">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="d4bf1-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d4bf1-123">Guide pratique : créer une procédure</span><span class="sxs-lookup"><span data-stu-id="d4bf1-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="d4bf1-124">Guide pratique : appeler une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="d4bf1-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="d4bf1-125">Comment : appeler un gestionnaire d’événements dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4bf1-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
