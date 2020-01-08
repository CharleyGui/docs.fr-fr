---
title: Vue d’ensemble d’async
description: Découvrez dans quelle mesure la programmation asynchrone est une technique clé qui facilite le blocage des E/S et des opérations simultanées sur plusieurs cœurs.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 1570909b7b416eff81dd90a936ff5ed10aad94f1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346082"
---
# <a name="async-overview"></a><span data-ttu-id="c7b3a-103">Vue d’ensemble d’async</span><span class="sxs-lookup"><span data-stu-id="c7b3a-103">Async Overview</span></span>

<span data-ttu-id="c7b3a-104">Il n’y a pas si longtemps, il suffisait d’acheter un PC ou un serveur plus récent pour que les applications soient plus rapides. Mais ce n’est plus le cas maintenant.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="c7b3a-105">En fait, c’est même tout le contraire.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-105">In fact, it reversed.</span></span> <span data-ttu-id="c7b3a-106">Les téléphones mobiles utilisent des processeurs ARM 1 GHz à cœur unique et les charges de travail serveur sont passées aux machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="c7b3a-107">Les utilisateurs veulent toujours une interface utilisateur réactive et les chefs d’entreprise veulent des serveurs qui s’adaptent à leur activité.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="c7b3a-108">La transition vers le mobile et le cloud ainsi qu’une population de plus de 3 milliards d’utilisateurs connectés à Internet ont donné naissance à un nouvel ensemble de modèles logiciels.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

- <span data-ttu-id="c7b3a-109">Les applications clientes doivent être toujours actives, toujours connectées, constamment réactives à l’interaction de l’utilisateur (interface tactile, par exemple) et en haut du classement des magasins d’applications !</span><span class="sxs-lookup"><span data-stu-id="c7b3a-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="c7b3a-110">Les services doivent gérer les pics de trafic en ayant la possibilité de monter et descendre en puissance facilement.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="c7b3a-111">La programmation asynchrone est une technique clé qui facilite le blocage des E/S et des opérations simultanées sur plusieurs cœurs.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="c7b3a-112">.NET offre aux applications et services la possibilité d’être réactifs et élastiques avec des modèles de programmation asynchrone au niveau du langage et C#faciles à utiliser dans F#, Visual Basic et.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="c7b3a-113">Pourquoi écrire du code asynchrone ?</span><span class="sxs-lookup"><span data-stu-id="c7b3a-113">Why Write Async Code?</span></span>

<span data-ttu-id="c7b3a-114">Les applications modernes utilisent beaucoup d’E/S de fichier et de réseau.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="c7b3a-115">Les API d’E/S se bloquent par défaut, ce qui se traduit par une expérience utilisateur et une utilisation du matériel médiocres, sauf si vous avez l’intention d’apprendre et d’utiliser des modèles complexes.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="c7b3a-116">Les API asynchrones basées sur des tâches et le modèle de programmation asynchrone au niveau du langage inversent ce modèle en faisant de l’exécution asynchrone la valeur par défaut avec quelques nouveaux concepts à découvrir.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="c7b3a-117">Le code asynchrone présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="c7b3a-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="c7b3a-118">Il gère davantage de demandes de serveur en cédant des threads pour traiter plus de demandes quand il attend le retour des demande d’E/S.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="c7b3a-119">Il permet aux interfaces utilisateur d’être plus réactives en cédant des threads à l’interaction de l’interface utilisateur quand il attend les demandes d’E/S et en transmettant les tâches d’exécution longue aux autres cœurs de processeur.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="c7b3a-120">De nombreuses API .NET plus récentes sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="c7b3a-121">Il est facile d’écrire du code asynchrone dans .NET !</span><span class="sxs-lookup"><span data-stu-id="c7b3a-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="c7b3a-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c7b3a-122">What's next?</span></span>

<span data-ttu-id="c7b3a-123">Pour plus d’informations, consultez la rubrique [Présentation détaillée des opérations asynchrones](async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="c7b3a-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="c7b3a-124">La rubrique [Modèles de programmation asynchrone](asynchronous-programming-patterns/index.md) fournit une vue d’ensemble des trois modèles de programmation asynchrone pris en charge dans .NET :</span><span class="sxs-lookup"><span data-stu-id="c7b3a-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="c7b3a-125">[Modèle de programmation asynchrone](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (hérité)</span><span class="sxs-lookup"><span data-stu-id="c7b3a-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="c7b3a-126">[Modèle asynchrone basé sur les événements (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (hérité)</span><span class="sxs-lookup"><span data-stu-id="c7b3a-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="c7b3a-127">[Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommandé pour un nouveau développement)</span><span class="sxs-lookup"><span data-stu-id="c7b3a-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="c7b3a-128">Pour plus d’informations sur le modèle de programmation basée sur des tâches recommandé, consultez la rubrique [Programmation asynchrone basée sur les tâches](parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="c7b3a-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
