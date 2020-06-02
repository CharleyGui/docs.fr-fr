---
title: Éléments fondamentaux du threading managé
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: 4d2a96619fd1c48c79b5590efdb52c307d29710c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291004"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="9a0df-102">Éléments fondamentaux du threading managé</span><span class="sxs-lookup"><span data-stu-id="9a0df-102">Managed threading basics</span></span>

<span data-ttu-id="9a0df-103">Les cinq premières rubriques de cette section sont conçues pour vous aider à déterminer quand utiliser le threading managé et pour expliquer des fonctionnalités de base.</span><span class="sxs-lookup"><span data-stu-id="9a0df-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="9a0df-104">Pour plus d’informations sur les classes qui fournissent des fonctionnalités supplémentaires, consultez [Fonctionnalités et objets de Threading](threading-objects-and-features.md) et [Vue d’ensemble des Primitives de synchronisation](overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="9a0df-104">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="9a0df-105">Le reste des rubriques de cette section traitent des sujets avancés, y compris l’interaction du threading managé avec le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="9a0df-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a0df-106">Dans .NET Framework 4, la bibliothèque parallèle de tâches et PLINQ fournissent des API pour le parallélisme des tâches et des données dans les programmes multithreads.</span><span class="sxs-lookup"><span data-stu-id="9a0df-106">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="9a0df-107">Pour plus d’informations, consultez [programmation parallèle](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a0df-107">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a0df-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9a0df-108">In this section</span></span>

 [<span data-ttu-id="9a0df-109">Threads et threads</span><span class="sxs-lookup"><span data-stu-id="9a0df-109">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="9a0df-110">Explique les avantages et les inconvénients de plusieurs threads et présente les scénarios dans lesquels vous pouvez créer des threads ou utiliser des threads du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="9a0df-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="9a0df-111">Exceptions dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="9a0df-111">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="9a0df-112">Décrit le comportement des exceptions non prises en charge dans les threads pour différentes versions de .NET Framework, notamment lorsqu’elles entraînent l’arrêt de l’application.</span><span class="sxs-lookup"><span data-stu-id="9a0df-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="9a0df-113">Synchronisation des données pour le multithreading</span><span class="sxs-lookup"><span data-stu-id="9a0df-113">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="9a0df-114">Décrit les stratégies de synchronisation des données dans des classes qui seront utilisées avec plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="9a0df-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="9a0df-115">Threads de premier plan et d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="9a0df-115">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="9a0df-116">Explique les différences entre les threads de premier plan et d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9a0df-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="9a0df-117">Threading managé et non managé dans Windows</span><span class="sxs-lookup"><span data-stu-id="9a0df-117">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="9a0df-118">Décrit la relation entre le threading managé et non managé, répertorie les équivalents managés de l’API de threading Windows et explique l’interaction des cloisonnements COM et des threads managés.</span><span class="sxs-lookup"><span data-stu-id="9a0df-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="9a0df-119">Stockage local des threads : champs static et emplacements de données relatifs à un thread</span><span class="sxs-lookup"><span data-stu-id="9a0df-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="9a0df-120">Décrit les mécanismes de stockage relatifs aux threads.</span><span class="sxs-lookup"><span data-stu-id="9a0df-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9a0df-121">Référence</span><span class="sxs-lookup"><span data-stu-id="9a0df-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="9a0df-122">Fournit la documentation de référence pour la classe **Thread** qui représente un thread managé, qu’elle provienne de code non managé ou qu’elle ait été créée dans une application managée.</span><span class="sxs-lookup"><span data-stu-id="9a0df-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="9a0df-123">Fournit un moyen sûr d’implémenter le multithreading conjointement avec des objets d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9a0df-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a0df-124">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="9a0df-124">Related sections</span></span>

 [<span data-ttu-id="9a0df-125">Vue d’ensemble des primitives de synchronisation</span><span class="sxs-lookup"><span data-stu-id="9a0df-125">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="9a0df-126">Décrit les classes managées utilisées pour synchroniser les activités de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="9a0df-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="9a0df-127">Meilleures pratiques pour le threading managé</span><span class="sxs-lookup"><span data-stu-id="9a0df-127">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="9a0df-128">Décrit les problèmes courants avec le multithreading et les stratégies pour les éviter.</span><span class="sxs-lookup"><span data-stu-id="9a0df-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="9a0df-129">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="9a0df-129">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="9a0df-130">Décrit la bibliothèque parallèle de tâches et PLINQ, qui simplifient considérablement le travail de création d’applications .NET Framework asynchrones et multithreads.</span><span class="sxs-lookup"><span data-stu-id="9a0df-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
