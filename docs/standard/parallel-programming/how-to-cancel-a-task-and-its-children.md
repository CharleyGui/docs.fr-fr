---
title: 'Procédure : annuler une tâche et ses enfants'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: ca6b5f10840d935aa45cb660da86685d1c90554b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290030"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="69669-102">Procédure : annuler une tâche et ses enfants</span><span class="sxs-lookup"><span data-stu-id="69669-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="69669-103">Ces exemples montrent comment effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="69669-103">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="69669-104">Créer et lancer une tâche annulable</span><span class="sxs-lookup"><span data-stu-id="69669-104">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="69669-105">Passer un jeton d’annulation à votre délégué d’utilisateur et éventuellement à l’instance de tâche</span><span class="sxs-lookup"><span data-stu-id="69669-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="69669-106">Notifier et répondre à la demande d’annulation dans votre délégué d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="69669-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="69669-107">Éventuellement notifier sur le thread appelant que la tâche a été annulée</span><span class="sxs-lookup"><span data-stu-id="69669-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="69669-108">Le thread appelant ne force pas l’arrêt de la tâche. Il signale seulement que son annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="69669-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="69669-109">Si la tâche est déjà en cours d’exécution, il incombe au délégué d’utilisateur de notifier la demande et d’y répondre de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="69669-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="69669-110">Si l’annulation a été demandée avant l’exécution de la tâche, le délégué d’utilisateur n’est jamais exécuté et l’objet de tâche passe à l’état Canceled.</span><span class="sxs-lookup"><span data-stu-id="69669-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69669-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="69669-111">Example</span></span>  
 <span data-ttu-id="69669-112">Cet exemple montre comment arrêter une <xref:System.Threading.Tasks.Task> et ses enfants en réponse à une demande d’annulation.</span><span class="sxs-lookup"><span data-stu-id="69669-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="69669-113">Il montre également que quand un délégué d’utilisateur se termine en levant une <xref:System.Threading.Tasks.TaskCanceledException>, le thread appelant peut éventuellement utiliser la méthode <xref:System.Threading.Tasks.Task.Wait%2A> ou <xref:System.Threading.Tasks.Task.WaitAll%2A>pour attendre la fin des tâches.</span><span class="sxs-lookup"><span data-stu-id="69669-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="69669-114">Dans ce cas, vous devez utiliser un bloc `try/catch` pour gérer les exceptions sur le thread appelant.</span><span class="sxs-lookup"><span data-stu-id="69669-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="69669-115">La classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> est entièrement intégrée au modèle d’annulation qui est basé sur les types <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> et <xref:System.Threading.CancellationToken?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="69669-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="69669-116">Pour plus d’informations, consultez [Annulation dans les threads managés](../threading/cancellation-in-managed-threads.md) et [Annulation de tâches](task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="69669-116">For more information, see [Cancellation in Managed Threads](../threading/cancellation-in-managed-threads.md) and [Task Cancellation](task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69669-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69669-117">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="69669-118">Programmation asynchrone basée sur les tâches</span><span class="sxs-lookup"><span data-stu-id="69669-118">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="69669-119">Tâches enfants attachées et détachées</span><span class="sxs-lookup"><span data-stu-id="69669-119">Attached and Detached Child Tasks</span></span>](attached-and-detached-child-tasks.md)
- [<span data-ttu-id="69669-120">Expressions lambda dans PLINQ et TPL</span><span class="sxs-lookup"><span data-stu-id="69669-120">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
