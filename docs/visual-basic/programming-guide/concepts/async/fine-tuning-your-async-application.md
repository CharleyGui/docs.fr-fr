---
title: Réglage de votre Application Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 3e9a6d02ec4948103b892ae012b8c51f66dd06c4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624732"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="a22d1-102">Réglage de votre Application Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a22d1-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="a22d1-103">Vous pouvez ajouter de la précision et de la flexibilité à vos applications asynchrones en utilisant les méthodes et les propriétés qui sont mises à disposition par le type <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="a22d1-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="a22d1-104">Les rubriques de cette section présentent des exemples qui utilisent <xref:System.Threading.CancellationToken> et des méthodes `Task` importantes telles que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a22d1-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a22d1-105">En utilisant `WhenAny` et `WhenAll`, vous pouvez plus facilement démarrer plusieurs tâches et attendre leur achèvement en ne surveillant qu’une seule tâche.</span><span class="sxs-lookup"><span data-stu-id="a22d1-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="a22d1-106">`WhenAny` retourne une tâche qui se termine lorsque l’une des tâches d’une collection est terminée.</span><span class="sxs-lookup"><span data-stu-id="a22d1-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="a22d1-107">Pour obtenir des exemples qui utilisent `WhenAny`, consultez [annuler les tâches Async restantes après elles est terminée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)et [démarrer plusieurs tâches Async et processus les terminées (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="a22d1-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="a22d1-108">`WhenAll` retourne une tâche qui se termine lorsque toutes les tâches d’une collection sont terminées.</span><span class="sxs-lookup"><span data-stu-id="a22d1-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="a22d1-109">Pour obtenir des informations supplémentaires et un exemple de code qui utilise `WhenAll`, consultez [Guide pratique pour Étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="a22d1-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="a22d1-110">Cette section comprend les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="a22d1-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="a22d1-111">[Annuler une tâche asynchrone ou une liste de tâches (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="a22d1-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="a22d1-112">Annuler des tâches Asynch après une période de temps (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a22d1-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="a22d1-113">Annuler les tâches Asynch restantes après une est terminée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a22d1-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="a22d1-114">Démarrer plusieurs tâches Asynch et les traiter une fois terminées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a22d1-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="a22d1-115">Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a22d1-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="a22d1-116">Les projets créent une interface utilisateur qui contient un bouton permettant de démarrer le processus et un autre permettant de l’annuler, comme dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="a22d1-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="a22d1-117">Ces boutons se nomment `startButton` et `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="a22d1-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="a22d1-118">![Fenêtre WPF avec bouton Annuler](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Boîte de dialogue avec bouton Démarrer et Arrêter")</span><span class="sxs-lookup"><span data-stu-id="a22d1-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="a22d1-119">Vous pouvez télécharger l’intégralité des projets WPF (Windows Presentation Foundation) à partir de la page [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Exemple Async : Réglage précis de votre application).</span><span class="sxs-lookup"><span data-stu-id="a22d1-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a22d1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a22d1-120">See also</span></span>

- [<span data-ttu-id="a22d1-121">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a22d1-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
