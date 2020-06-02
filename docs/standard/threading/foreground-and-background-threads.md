---
title: Threads de premier plan et d'arrière-plan
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 5e7ec9e2c2a5ba3de1b4518cea15eb5f512640d3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279683"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="b6049-102">Threads de premier plan et d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="b6049-102">Foreground and Background Threads</span></span>
<span data-ttu-id="b6049-103">Un thread managé est un thread d’arrière-plan ou un thread de premier plan.</span><span class="sxs-lookup"><span data-stu-id="b6049-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="b6049-104">Les threads d’arrière-plan sont identiques aux threads de premier plan à une exception près : un thread d’arrière-plan ne permet pas de poursuivre l’exécution de l’environnement d’exécution managé.</span><span class="sxs-lookup"><span data-stu-id="b6049-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="b6049-105">Une fois que tous les threads de premier plan ont été arrêtés dans un processus managé (où le fichier .exe est un assembly managé), le système arrête tous les threads d’arrière-plan et se ferme.</span><span class="sxs-lookup"><span data-stu-id="b6049-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6049-106">Lorsque le runtime arrête un thread d’arrière-plan parce que le processus est en cours d’arrêt, aucune exception n’est levée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="b6049-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="b6049-107">Toutefois, lorsque des threads sont arrêtés parce que la méthode <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> décharge le domaine d’application, une <xref:System.Threading.ThreadAbortException> est levée dans les threads de premier plan et d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b6049-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="b6049-108">Utilisez la propriété <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> pour déterminer si un thread est un thread d’arrière-plan ou de premier plan, ou pour modifier son état.</span><span class="sxs-lookup"><span data-stu-id="b6049-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="b6049-109">Un thread peut être transformé en thread d’arrière-plan à tout moment en définissant sa propriété <xref:System.Threading.Thread.IsBackground%2A> sur `true`.</span><span class="sxs-lookup"><span data-stu-id="b6049-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b6049-110">L’état de premier plan ou d’arrière-plan d’un thread n’affecte pas le résultat d’une exception non prise en charge dans le thread.</span><span class="sxs-lookup"><span data-stu-id="b6049-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="b6049-111">Dans la version 2.0 de .NET Framework, une exception non prise en charge dans les threads de premier plan ou d’arrière-plan entraîne l’arrêt de l’application.</span><span class="sxs-lookup"><span data-stu-id="b6049-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="b6049-112">Voir [Exceptions dans les threads managés](exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="b6049-112">See [Exceptions in Managed Threads](exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="b6049-113">Les threads qui font partie du pool de threads managés (autrement dit, les threads dont la propriété <xref:System.Threading.Thread.IsThreadPoolThread%2A> est `true`) sont des threads d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b6049-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="b6049-114">Tous les threads qui entrent dans l’environnement d’exécution managé à partir de code non managé sont marqués comme threads d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b6049-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="b6049-115">Tous les threads générés en créant et en démarrant un nouvel objet <xref:System.Threading.Thread> sont par défaut des threads de premier plan.</span><span class="sxs-lookup"><span data-stu-id="b6049-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="b6049-116">Si vous utilisez un thread pour surveiller une activité, telle qu’une connexion de socket, définissez sa propriété <xref:System.Threading.Thread.IsBackground%2A> sur `true` afin que le thread n’empêche pas votre processus de s’arrêter.</span><span class="sxs-lookup"><span data-stu-id="b6049-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6049-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6049-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
