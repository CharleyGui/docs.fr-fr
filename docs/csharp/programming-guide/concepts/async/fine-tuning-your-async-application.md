---
title: Réglage de votre application Async (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970239"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="f822d-102">Réglage de votre application Async (C#)</span><span class="sxs-lookup"><span data-stu-id="f822d-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="f822d-103">Vous pouvez ajouter de la précision et de la flexibilité à vos applications asynchrones en utilisant les méthodes et les propriétés qui sont mises à disposition par le type <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="f822d-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="f822d-104">Les rubriques de cette section présentent des exemples qui utilisent <xref:System.Threading.CancellationToken> et des méthodes `Task` importantes telles que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f822d-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f822d-105">En utilisant `WhenAny` et `WhenAll`, vous pouvez plus facilement démarrer plusieurs tâches et attendre leur achèvement en ne surveillant qu’une seule tâche.</span><span class="sxs-lookup"><span data-stu-id="f822d-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="f822d-106">`WhenAny` retourne une tâche qui se termine lorsque l’une des tâches d’une collection est terminée.</span><span class="sxs-lookup"><span data-stu-id="f822d-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="f822d-107">Pour obtenir des exemples qui utilisent `WhenAny`, consultez [Annuler les tâches asynchrones restantes quand l’une d’elles est terminée (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) et [Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="f822d-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="f822d-108">`WhenAll` retourne une tâche qui se termine lorsque toutes les tâches d’une collection sont terminées.</span><span class="sxs-lookup"><span data-stu-id="f822d-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="f822d-109">Pour plus d’informations `WhenAll`et un exemple qui utilise , voir [Comment étendre le pas à pas async en utilisant Task.WhenAll (C)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="f822d-109">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="f822d-110">Cette section comprend les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="f822d-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="f822d-111">[Annuler une tâche Async ou une liste de tâches (C)](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="f822d-111">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="f822d-112">Annuler les tâches Async après une période de temps (C)</span><span class="sxs-lookup"><span data-stu-id="f822d-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="f822d-113">Annuler les tâches asynchrones restantes quand l’une d’elles est terminée (C#)</span><span class="sxs-lookup"><span data-stu-id="f822d-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="f822d-114">Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)</span><span class="sxs-lookup"><span data-stu-id="f822d-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="f822d-115">Pour exécuter les exemples, Visual Studio version 2012 ou ultérieure et le .NET Framework version 4.5 ou ultérieure doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f822d-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="f822d-116">Les projets créent une interface utilisateur qui contient un bouton permettant de démarrer le processus et un autre permettant de l’annuler, comme dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="f822d-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="f822d-117">Ces boutons se nomment `startButton` et `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="f822d-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="f822d-118">![Fenêtre WPF avec un bouton d'annulation](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Boîte de dialogue avec un bouton Démarrer et arrêter")</span><span class="sxs-lookup"><span data-stu-id="f822d-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="f822d-119">Téléchargez l’intégralité des projets Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="f822d-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f822d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f822d-120">See also</span></span>

- [<span data-ttu-id="f822d-121">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="f822d-121">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
