---
title: Threading managé
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: c5ca102dc98e50067d39d2f0c51a6ff75e342e9f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588665"
---
# <a name="managed-threading"></a><span data-ttu-id="56613-102">Threading managé</span><span class="sxs-lookup"><span data-stu-id="56613-102">Managed Threading</span></span>
<span data-ttu-id="56613-103">Que votre développement s’applique à des ordinateurs avec un ou plusieurs processeurs, votre application doit fournir l’interaction la plus réactive avec l’utilisateur, même si l’application effectue actuellement d’autres opérations.</span><span class="sxs-lookup"><span data-stu-id="56613-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="56613-104">Utiliser plusieurs threads d’exécution est l’une des manières les plus efficaces pour maintenir la réactivité de votre application vis-à-vis de l’utilisateur, tout en exploitant le processeur entre voire pendant des événements utilisateur.</span><span class="sxs-lookup"><span data-stu-id="56613-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="56613-105">Bien que cette section présente les concepts de base du threading, elle se concentre sur les concepts de threading managé et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="56613-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56613-106">À compter de .NET Framework 4, la programmation multithread est considérablement simplifiée avec les classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md), de nouvelles classes de collections simultanées dans l’espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType> et un nouveau modèle de programmation basé sur le concept de tâches au lieu de threads.</span><span class="sxs-lookup"><span data-stu-id="56613-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="56613-107">Pour plus d’informations, voir [Programmation parallèle](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="56613-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56613-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="56613-108">In This Section</span></span>  
 [<span data-ttu-id="56613-109">Base de threading gérée</span><span class="sxs-lookup"><span data-stu-id="56613-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="56613-110">Fournit une vue d’ensemble des threads managés et explique quand utiliser plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="56613-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="56613-111">Utilisation des threads et du threading</span><span class="sxs-lookup"><span data-stu-id="56613-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="56613-112">Explique comment créer, démarrer, suspendre, reprendre et abandonner des threads.</span><span class="sxs-lookup"><span data-stu-id="56613-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="56613-113">Gestion des meilleures pratiques de threading</span><span class="sxs-lookup"><span data-stu-id="56613-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="56613-114">Décrit les niveaux de synchronisation, comment éviter les interblocages et les conditions de concurrence, et d’autres problèmes liés aux threads.</span><span class="sxs-lookup"><span data-stu-id="56613-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="56613-115">Objets et caractéristiques de threading</span><span class="sxs-lookup"><span data-stu-id="56613-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="56613-116">Décrit les classes managées que vous pouvez utiliser pour synchroniser les activités de threads et les données d’objets ouvertes sur différents threads, et fournit une vue d’ensemble des threads du pool.</span><span class="sxs-lookup"><span data-stu-id="56613-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="56613-117">Référence</span><span class="sxs-lookup"><span data-stu-id="56613-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="56613-118">Contient des classes pour l’utilisation et la synchronisation de threads managés.</span><span class="sxs-lookup"><span data-stu-id="56613-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="56613-119">Contient des classes de collection qui peuvent être utilisées en toute sécurité avec plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="56613-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="56613-120">Contient des classes pour la création et la planification de tâches de traitement simultanées.</span><span class="sxs-lookup"><span data-stu-id="56613-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="56613-121">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="56613-121">Related Sections</span></span>  
 [<span data-ttu-id="56613-122">Domaines d'application</span><span class="sxs-lookup"><span data-stu-id="56613-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="56613-123">Fournit une vue d'ensemble des domaines d'application et de leur utilisation dans le Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="56613-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="56613-124">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="56613-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="56613-125">Décrit les opérations élémentaires des E/S asynchrones et leurs avantages en termes de performances.</span><span class="sxs-lookup"><span data-stu-id="56613-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="56613-126">Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)</span><span class="sxs-lookup"><span data-stu-id="56613-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="56613-127">Offre une vue d’ensemble du modèle recommandé pour la programmation asynchrone dans .NET.</span><span class="sxs-lookup"><span data-stu-id="56613-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="56613-128">Appel de méthodes synchrones de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="56613-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="56613-129">Explique comment appeler des méthodes sur les threads d’un pool à l’aide des fonctionnalités intégrées des délégués.</span><span class="sxs-lookup"><span data-stu-id="56613-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="56613-130">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="56613-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="56613-131">Décrit les bibliothèques de programmation parallèle qui simplifient l’utilisation de plusieurs threads dans les applications.</span><span class="sxs-lookup"><span data-stu-id="56613-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="56613-132">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="56613-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="56613-133">Décrit un système permettant d’exécuter des requêtes en parallèle afin de tirer parti de plusieurs processeurs.</span><span class="sxs-lookup"><span data-stu-id="56613-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
