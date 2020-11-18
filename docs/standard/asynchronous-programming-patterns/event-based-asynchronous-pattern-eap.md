---
title: Modèle asynchrone basé sur les événements (EAP)
description: Consultez des liens vers des articles sur le modèle asynchrone basé sur les événements (EAP) dans .NET, tels que l’implémentation, les meilleures pratiques, l’implémentation d’un client EAP, et bien plus encore.
ms.date: 07/23/2018
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: c15bb6c9ec6ea737e6f240376e12bf8de3aa61bc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830400"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="d9c85-103">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="d9c85-103">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="d9c85-104">Il existe plusieurs façons d’exposer des fonctionnalités asynchrones à du code client.</span><span class="sxs-lookup"><span data-stu-id="d9c85-104">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="d9c85-105">Le modèle asynchrone basé sur les événements recommande une méthode pour obtenir des classes un comportement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="d9c85-105">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9c85-106">À partir de .NET Framework 4, la bibliothèque parallèle de tâches fournit un nouveau modèle pour la programmation asynchrone et parallèle.</span><span class="sxs-lookup"><span data-stu-id="d9c85-106">Starting with .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="d9c85-107">Pour plus d’informations, consultez [Bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md) et [Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="d9c85-107">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="d9c85-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d9c85-108">In This Section</span></span>

 [<span data-ttu-id="d9c85-109">Vue d’ensemble du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="d9c85-109">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="d9c85-110">Explique comment le modèle asynchrone basé sur les événements permet de profiter des avantages des applications multithread tout en masquant de nombreux problèmes complexes inhérents à la conception multithread.</span><span class="sxs-lookup"><span data-stu-id="d9c85-110">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="d9c85-111">Implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="d9c85-111">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9c85-112">Décrit la façon standardisée de placer dans un package une classe qui possède des fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="d9c85-112">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="d9c85-113">Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="d9c85-113">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9c85-114">Décrit les exigences liées à l’exposition de fonctionnalités asynchrones conformément au modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="d9c85-114">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="d9c85-115">Choix du moment auquel implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="d9c85-115">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9c85-116">Explique comment savoir quand vous devez implémenter le modèle asynchrone basé sur les événements au lieu du modèle <xref:System.IAsyncResult> représenté par le [ modèle de programmation asynchrone (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="d9c85-116">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="d9c85-117">Procédure : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="d9c85-117">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9c85-118">Décrit comment créer un composant qui implémente le modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="d9c85-118">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="d9c85-119">Il est implémenté à l'aide de classes d'assistance à partir de l'espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>, ce qui garantit le bon fonctionnement du composant avec n'importe quel modèle d'application.</span><span class="sxs-lookup"><span data-stu-id="d9c85-119">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="d9c85-120">Procédure : implémenter un client du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="d9c85-120">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9c85-121">Décrit comment créer un client qui utilise un composant implémentant le modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="d9c85-121">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="d9c85-122">Procédure : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="d9c85-122">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9c85-123">Explique comment créer un composant qui prend en charge le modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="d9c85-123">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d9c85-124">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="d9c85-124">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="d9c85-125">Décrit la classe <xref:System.ComponentModel.AsyncOperation> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="d9c85-125">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="d9c85-126">Décrit la classe <xref:System.ComponentModel.AsyncOperationManager> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="d9c85-126">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="d9c85-127">Décrit le composant <xref:System.ComponentModel.BackgroundWorker> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="d9c85-127">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d9c85-128">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="d9c85-128">Related Sections</span></span>

 [<span data-ttu-id="d9c85-129">Bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="d9c85-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="d9c85-130">Décrit un modèle de programmation pour les opérations asynchrones et parallèles.</span><span class="sxs-lookup"><span data-stu-id="d9c85-130">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="d9c85-131">Thread</span><span class="sxs-lookup"><span data-stu-id="d9c85-131">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="d9c85-132">Décrit les fonctionnalités de multithreading dans .NET.</span><span class="sxs-lookup"><span data-stu-id="d9c85-132">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c85-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9c85-133">See also</span></span>

- [<span data-ttu-id="d9c85-134">Meilleures pratiques pour le threading managé</span><span class="sxs-lookup"><span data-stu-id="d9c85-134">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="d9c85-135">Événements</span><span class="sxs-lookup"><span data-stu-id="d9c85-135">Events</span></span>](../events/index.md)
- [<span data-ttu-id="d9c85-136">Modèles de conception de la programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="d9c85-136">Asynchronous Programming Design Patterns</span></span>](index.md)
