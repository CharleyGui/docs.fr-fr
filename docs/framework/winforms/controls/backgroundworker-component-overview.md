---
title: Vue d'ensemble du composant BackgroundWorker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046107"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="9adb6-102">Vue d'ensemble du composant BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="9adb6-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="9adb6-103">De nombreuses opérations couramment exécutées peuvent être longues à s'éxécuter.</span><span class="sxs-lookup"><span data-stu-id="9adb6-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="9adb6-104">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9adb6-104">For example:</span></span>  
  
- <span data-ttu-id="9adb6-105">Téléchargements d'images</span><span class="sxs-lookup"><span data-stu-id="9adb6-105">Image downloads</span></span>  
  
- <span data-ttu-id="9adb6-106">Appels de service web</span><span class="sxs-lookup"><span data-stu-id="9adb6-106">Web service invocations</span></span>  
  
- <span data-ttu-id="9adb6-107">Téléchargements et chargements de fichiers (y compris pour les applications d'égal à égal)</span><span class="sxs-lookup"><span data-stu-id="9adb6-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="9adb6-108">Calculs locaux complexes</span><span class="sxs-lookup"><span data-stu-id="9adb6-108">Complex local computations</span></span>  
  
- <span data-ttu-id="9adb6-109">Transactions de base de données</span><span class="sxs-lookup"><span data-stu-id="9adb6-109">Database transactions</span></span>  
  
- <span data-ttu-id="9adb6-110">Accès au disque local, compte tenu de sa vitesse lente par rapport à l'accès mémoire</span><span class="sxs-lookup"><span data-stu-id="9adb6-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="9adb6-111">Les opérations de ce type peuvent entraîner le blocage de votre interface utilisateur pendant qu’elles sont en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9adb6-111">Operations like these can cause your user interface to block while they are running.</span></span> <span data-ttu-id="9adb6-112">Quand vous souhaitez une interface utilisateur réactive et que vous êtes confronté à de longs délais associés à ce type d'opérations, le composant <xref:System.ComponentModel.BackgroundWorker> fournit une solution commode.</span><span class="sxs-lookup"><span data-stu-id="9adb6-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="9adb6-113">Le composant <xref:System.ComponentModel.BackgroundWorker> vous donne la possibilité d'exécuter les opérations longues de façon asynchrone (« en arrière-plan »), sur un thread différent du thread d'interface utilisateur principal de votre application.</span><span class="sxs-lookup"><span data-stu-id="9adb6-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="9adb6-114">Pour utiliser un <xref:System.ComponentModel.BackgroundWorker>, vous lui indiquez simplement quelle méthode de travail de longue durée exécuter en arrière-plan, puis vous appelez la méthode <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="9adb6-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="9adb6-115">Votre thread d'appel continue de s'exécuter normalement pendant que la méthode de travail s'exécute de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9adb6-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="9adb6-116">Une fois la méthode exécutée, le <xref:System.ComponentModel.BackgroundWorker> alerte le thread d'appel en déclenchant l'événement <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>, lequel contient éventuellement les résultats de l'opération.</span><span class="sxs-lookup"><span data-stu-id="9adb6-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="9adb6-117">Le <xref:System.ComponentModel.BackgroundWorker> composant est disponible à partir de la **boîte à outils**, sous l’onglet **composants** . Pour ajouter un <xref:System.ComponentModel.BackgroundWorker> à votre formulaire, faites glisser le composant <xref:System.ComponentModel.BackgroundWorker> dessus.</span><span class="sxs-lookup"><span data-stu-id="9adb6-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="9adb6-118">Il apparaît dans la barre d’état des composants et ses propriétés s’affichent dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="9adb6-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="9adb6-119">Pour démarrer votre opération asynchrone, utilisez la méthode <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="9adb6-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="9adb6-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> prend un paramètre `object` facultatif qui peut être utilisé pour passer des arguments à votre méthode de travail.</span><span class="sxs-lookup"><span data-stu-id="9adb6-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="9adb6-121">La classe <xref:System.ComponentModel.BackgroundWorker> expose l'évenement <xref:System.ComponentModel.BackgroundWorker.DoWork> auquel votre thread de travail est attaché via le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>.</span><span class="sxs-lookup"><span data-stu-id="9adb6-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="9adb6-122">Le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork> prend un paramètre <xref:System.ComponentModel.DoWorkEventArgs> qui est doté de la propriété <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>.</span><span class="sxs-lookup"><span data-stu-id="9adb6-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="9adb6-123">Celle-ci reçoit le paramètre de <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> et peut être passée à votre méthode de travail qui sera appelée dans le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>.</span><span class="sxs-lookup"><span data-stu-id="9adb6-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="9adb6-124">L'exemple suivant montre comment affecter un résultat depuis une méthode de travail appelée `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="9adb6-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="9adb6-125">Il fait partie d’un exemple plus complet, que vous pouvez trouver [à l’adresse suivante: Implémentez un formulaire qui utilise une opération](how-to-implement-a-form-that-uses-a-background-operation.md)d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9adb6-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="9adb6-126">Pour plus d’informations sur l’utilisation des gestionnaires d’événements, consultez [événements](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="9adb6-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9adb6-127">Quand vous utilisez le multithreading, vous vous exposez potentiellement à des bogues très sérieux et complexes.</span><span class="sxs-lookup"><span data-stu-id="9adb6-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="9adb6-128">Consultez les [Meilleures pratiques pour le threading managé](../../../standard/threading/managed-threading-best-practices.md) avant d’implémenter une solution qui utilise le multithreading.</span><span class="sxs-lookup"><span data-stu-id="9adb6-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="9adb6-129">Pour plus d’informations sur l' <xref:System.ComponentModel.BackgroundWorker> utilisation de la [classe, consultez Procédure: exécuter une opération en arrière-plan](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="9adb6-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9adb6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9adb6-130">See also</span></span>

- [<span data-ttu-id="9adb6-131">Threading managé</span><span class="sxs-lookup"><span data-stu-id="9adb6-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="9adb6-132">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="9adb6-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="9adb6-133">Guide pratique pour implémenter un formulaire qui utilise une opération d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="9adb6-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
