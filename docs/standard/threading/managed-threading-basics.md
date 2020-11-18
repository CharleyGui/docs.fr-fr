---
title: Éléments fondamentaux du threading managé
description: Consultez les liens vers d’autres articles sur le Threading géré, couvrant des sujets tels que les exceptions, la synchronisation des données, le premier plan & les threads d’arrière-plan, le stockage local et bien plus encore.
ms.date: 03/30/2017
helpviewer_keywords:
- multiple threads
- threading [.NET], multiple threads
- threading [.NET], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: 16785b1c21c5810e55429f6756dcf591c90d8499
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819667"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="5b678-103">Éléments fondamentaux du threading managé</span><span class="sxs-lookup"><span data-stu-id="5b678-103">Managed threading basics</span></span>

<span data-ttu-id="5b678-104">Les cinq premiers Articles de cette section sont conçus pour vous aider à déterminer quand utiliser le threading managé et à expliquer certaines fonctionnalités de base.</span><span class="sxs-lookup"><span data-stu-id="5b678-104">The first five articles of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="5b678-105">Pour plus d’informations sur les classes qui fournissent des fonctionnalités supplémentaires, consultez [Fonctionnalités et objets de Threading](threading-objects-and-features.md) et [Vue d’ensemble des Primitives de synchronisation](overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="5b678-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="5b678-106">Les autres Articles de cette section traitent des sujets avancés, y compris l’interaction du threading managé avec le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="5b678-106">The remaining articles in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b678-107">À partir de .NET Framework 4, la bibliothèque parallèle de tâches et PLINQ fournissent des API pour le parallélisme des tâches et des données dans les programmes multithread.</span><span class="sxs-lookup"><span data-stu-id="5b678-107">Starting with .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="5b678-108">Pour plus d’informations, consultez [programmation parallèle](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b678-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b678-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5b678-109">In this section</span></span>

 [<span data-ttu-id="5b678-110">Threads et threading</span><span class="sxs-lookup"><span data-stu-id="5b678-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="5b678-111">Explique les avantages et les inconvénients de plusieurs threads et présente les scénarios dans lesquels vous pouvez créer des threads ou utiliser des threads du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="5b678-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="5b678-112">Exceptions dans les threads managés</span><span class="sxs-lookup"><span data-stu-id="5b678-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="5b678-113">Décrit le comportement des exceptions non gérées dans les threads pour les différentes versions de .NET, en particulier dans les situations où elles entraînent l’arrêt de l’application.</span><span class="sxs-lookup"><span data-stu-id="5b678-113">Describes the behavior of unhandled exceptions in threads for different versions of .NET, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="5b678-114">Synchronisation des données pour le multithreading</span><span class="sxs-lookup"><span data-stu-id="5b678-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="5b678-115">Décrit les stratégies de synchronisation des données dans des classes qui seront utilisées avec plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="5b678-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="5b678-116">Threads de premier plan et d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="5b678-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="5b678-117">Explique les différences entre les threads de premier plan et d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5b678-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="5b678-118">Threading managé et non managé dans Windows</span><span class="sxs-lookup"><span data-stu-id="5b678-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="5b678-119">Décrit la relation entre le threading managé et non managé, répertorie les équivalents managés de l’API de threading Windows et explique l’interaction des cloisonnements COM et des threads managés.</span><span class="sxs-lookup"><span data-stu-id="5b678-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="5b678-120">Stockage local des threads : champs static et emplacements de données relatifs à un thread</span><span class="sxs-lookup"><span data-stu-id="5b678-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="5b678-121">Décrit les mécanismes de stockage relatifs aux threads.</span><span class="sxs-lookup"><span data-stu-id="5b678-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5b678-122">Référence</span><span class="sxs-lookup"><span data-stu-id="5b678-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="5b678-123">Fournit la documentation de référence pour la classe **Thread** qui représente un thread managé, qu’elle provienne de code non managé ou qu’elle ait été créée dans une application managée.</span><span class="sxs-lookup"><span data-stu-id="5b678-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="5b678-124">Fournit un moyen sûr d’implémenter le multithreading conjointement avec des objets d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5b678-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5b678-125">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="5b678-125">Related sections</span></span>

 [<span data-ttu-id="5b678-126">Vue d’ensemble des primitives de synchronisation</span><span class="sxs-lookup"><span data-stu-id="5b678-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="5b678-127">Décrit les classes managées utilisées pour synchroniser les activités de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="5b678-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="5b678-128">Meilleures pratiques pour le threading managé</span><span class="sxs-lookup"><span data-stu-id="5b678-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="5b678-129">Décrit les problèmes courants avec le multithreading et les stratégies pour les éviter.</span><span class="sxs-lookup"><span data-stu-id="5b678-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="5b678-130">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="5b678-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="5b678-131">Décrit la bibliothèque parallèle de tâches et PLINQ, qui simplifient de façon considérable le travail de création d’applications .NET asynchrones et multithread.</span><span class="sxs-lookup"><span data-stu-id="5b678-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET applications.</span></span>
