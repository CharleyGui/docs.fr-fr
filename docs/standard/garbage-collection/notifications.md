---
title: Notifications de garbage collection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
ms.openlocfilehash: d5646c4969c95350ab4cd63b16f6f99ffba3a4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131535"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="4165b-102">Notifications de garbage collection</span><span class="sxs-lookup"><span data-stu-id="4165b-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="4165b-103">Il existe des cas où une opération garbage collection complète (c’est-à-dire, une opération garbage collection de génération 2) par le CLR peut avoir des effets néfastes sur les performances.</span><span class="sxs-lookup"><span data-stu-id="4165b-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="4165b-104">Cela peut être un problème en particulier avec les serveurs qui traitent de grands volumes de demandes; dans ce cas, une longue collecte des ordures peut entraîner un délai de demande. Pour éviter qu’une collecte complète ne se produise pendant une période critique, vous pouvez être informé qu’une collecte complète des ordures approche, puis prendre des mesures pour rediriger la charge de travail vers une autre instance serveur.</span><span class="sxs-lookup"><span data-stu-id="4165b-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="4165b-105">Vous pouvez également déclencher vous-même une collection, sous réserve que l’instance de serveur actuelle n’a pas besoin de traiter de requêtes.</span><span class="sxs-lookup"><span data-stu-id="4165b-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="4165b-106">La méthode <xref:System.GC.RegisterForFullGCNotification%2A> permet de déclencher une notification lorsque le runtime détecte qu’un garbage collection complet est sur le point de se produire.</span><span class="sxs-lookup"><span data-stu-id="4165b-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="4165b-107">Cette notification est divisée en deux parties : lorsqu’un garbage collection complet est imminent et lorsque le garbage collection complet est terminé.</span><span class="sxs-lookup"><span data-stu-id="4165b-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4165b-108">Seul le blocage des garbage collections génère des notifications.</span><span class="sxs-lookup"><span data-stu-id="4165b-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="4165b-109">Lorsque [ \<l’élément de configuration>gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) est activé, les collectes d’ordures de fond n’augmenteront pas les notifications.</span><span class="sxs-lookup"><span data-stu-id="4165b-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="4165b-110">Pour déterminer quand une notification a été levée, utilisez les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A>.</span><span class="sxs-lookup"><span data-stu-id="4165b-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="4165b-111">En général, vous utilisez ces méthodes dans une boucle `while` pour obtenir en permanence une énumération <xref:System.GCNotificationStatus> qui indique l’état de la notification.</span><span class="sxs-lookup"><span data-stu-id="4165b-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="4165b-112">Si cette valeur est égale à <xref:System.GCNotificationStatus.Succeeded>, vous pouvez procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="4165b-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="4165b-113">En réponse à une notification obtenue avec la méthode <xref:System.GC.WaitForFullGCApproach%2A>, vous pouvez rediriger la charge de travail et éventuellement déclencher vous-même une collection.</span><span class="sxs-lookup"><span data-stu-id="4165b-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="4165b-114">En réponse à une notification obtenue avec la méthode <xref:System.GC.WaitForFullGCComplete%2A>, vous pouvez rendre l’instance de serveur actuelle disponible pour traiter à nouveau les requêtes.</span><span class="sxs-lookup"><span data-stu-id="4165b-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="4165b-115">Vous pouvez également rassembler des informations.</span><span class="sxs-lookup"><span data-stu-id="4165b-115">You can also gather information.</span></span> <span data-ttu-id="4165b-116">Par exemple, vous pouvez utiliser la méthode <xref:System.GC.CollectionCount%2A> pour enregistrer le nombre de collections.</span><span class="sxs-lookup"><span data-stu-id="4165b-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="4165b-117">Les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> sont conçues pour fonctionner ensemble.</span><span class="sxs-lookup"><span data-stu-id="4165b-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="4165b-118">Le fait d’utiliser l’une sans l’autre peut produire des résultats indéterminés.</span><span class="sxs-lookup"><span data-stu-id="4165b-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="4165b-119">Garbage collection complet</span><span class="sxs-lookup"><span data-stu-id="4165b-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="4165b-120">Le runtime génère un garbage collection complet lorsque l’un des scénarios suivants est vrai :</span><span class="sxs-lookup"><span data-stu-id="4165b-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="4165b-121">Une quantité suffisante de mémoire a été promue au niveau génération 2 pour entraîner le garbage collection de génération 2 suivant.</span><span class="sxs-lookup"><span data-stu-id="4165b-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="4165b-122">Une quantité suffisante de mémoire a été promue dans le tas d’objets volumineux pour entraîner le garbage collection de génération 2 suivant.</span><span class="sxs-lookup"><span data-stu-id="4165b-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="4165b-123">Une collection de génération 1 passe à une collection de génération 2 en raison d’autres facteurs.</span><span class="sxs-lookup"><span data-stu-id="4165b-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="4165b-124">Les seuils que vous spécifiez dans la méthode <xref:System.GC.RegisterForFullGCNotification%2A> s’appliquent aux deux premiers scénarios.</span><span class="sxs-lookup"><span data-stu-id="4165b-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="4165b-125">Toutefois, dans le premier scénario, vous ne recevrez pas toujours la notification en temps proportionnel aux valeurs de seuil que vous spécifiez, pour deux raisons :</span><span class="sxs-lookup"><span data-stu-id="4165b-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="4165b-126">Le runtime ne vérifie pas chaque allocation de petit objet (pour des raisons de performances).</span><span class="sxs-lookup"><span data-stu-id="4165b-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="4165b-127">Seules les collections de génération 1 promeuvent de la mémoire au niveau génération 2.</span><span class="sxs-lookup"><span data-stu-id="4165b-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="4165b-128">Le troisième scénario contribue également à l’incertitude sur la réception de la notification.</span><span class="sxs-lookup"><span data-stu-id="4165b-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="4165b-129">Bien que cela ne soit pas garanti, cela peut constituer un moyen utile pour atténuer les effets d’un garbage collection complet intempestif en redirigeant les requêtes durant ce laps de temps ou en déclenchant vous-même la collection lorsque cela est approprié.</span><span class="sxs-lookup"><span data-stu-id="4165b-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="4165b-130">Paramètres de seuil de notification</span><span class="sxs-lookup"><span data-stu-id="4165b-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="4165b-131">La méthode <xref:System.GC.RegisterForFullGCNotification%2A> possède deux paramètres pour spécifier les valeurs de seuil des objets de génération 2 et le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="4165b-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="4165b-132">Lorsque ces valeurs sont atteintes, une notification de garbage collection doit être déclenchée.</span><span class="sxs-lookup"><span data-stu-id="4165b-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="4165b-133">Le tableau suivant décrit ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="4165b-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="4165b-134">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4165b-134">Parameter</span></span>|<span data-ttu-id="4165b-135">Description</span><span class="sxs-lookup"><span data-stu-id="4165b-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="4165b-136">Nombre entre 1 et 99 qui spécifie le moment auquel la notification doit être émise selon les objets promus dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="4165b-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="4165b-137">Nombre entre 1 et 99 qui spécifie le moment auquel la notification doit être émise selon les objets alloués dans le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="4165b-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="4165b-138">Si vous spécifiez une valeur trop élevée, il est très probable que vous receviez une notification, mais la période d’attente pourrait être trop longue avant que le runtime ne déclenche une collection.</span><span class="sxs-lookup"><span data-stu-id="4165b-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="4165b-139">Si vous déclenchez vous-même une collection, vous pourriez récupérer plus d’objets que si le runtime provoque la collection.</span><span class="sxs-lookup"><span data-stu-id="4165b-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="4165b-140">Si vous spécifiez une valeur trop faible, le runtime peut déclencher la collection avant que vous n’ayez eu le temps d’être averti.</span><span class="sxs-lookup"><span data-stu-id="4165b-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4165b-141"> Exemple</span><span class="sxs-lookup"><span data-stu-id="4165b-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4165b-142">Description</span><span class="sxs-lookup"><span data-stu-id="4165b-142">Description</span></span>  
 <span data-ttu-id="4165b-143">Dans l’exemple suivant, un groupe de serveurs traitent des requêtes web entrantes.</span><span class="sxs-lookup"><span data-stu-id="4165b-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="4165b-144">Pour simuler la charge de travail de traitement des requêtes, des tableaux d’octets sont ajoutés à une collection <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="4165b-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="4165b-145">Chaque serveur s’inscrit pour une notification de garbage collection, puis démarre un thread sur la méthode utilisateur `WaitForFullGCProc` afin de surveiller en permanence l’énumération <xref:System.GCNotificationStatus> retournée par les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A>.</span><span class="sxs-lookup"><span data-stu-id="4165b-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="4165b-146">Les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> appellent leurs méthodes utilisateur de gestion des événements respectives lorsqu’une notification est levée :</span><span class="sxs-lookup"><span data-stu-id="4165b-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="4165b-147">Cette méthode appelle la méthode utilisateur `RedirectRequests`, qui indique au serveur de mise en file d’attente des requêtes d’interrompre l’envoi de requêtes au serveur.</span><span class="sxs-lookup"><span data-stu-id="4165b-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="4165b-148">Cela est simulé en définissant la variable de niveau classe `bAllocate` sur `false` afin qu’aucun autre objet ne soit alloué.</span><span class="sxs-lookup"><span data-stu-id="4165b-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="4165b-149">Ensuite, la méthode utilisateur `FinishExistingRequests` est appelée pour terminer le traitement des requêtes serveur en attente.</span><span class="sxs-lookup"><span data-stu-id="4165b-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="4165b-150">Cela est simulé en supprimant la collection <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="4165b-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="4165b-151">Enfin, un garbage collection est déclenché car la charge de travail est faible.</span><span class="sxs-lookup"><span data-stu-id="4165b-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="4165b-152">Cette méthode appelle la méthode utilisateur `AcceptRequests` pour reprendre l’acceptation des requêtes, car le serveur n’est plus susceptible d’être soumis à un garbage collection complet.</span><span class="sxs-lookup"><span data-stu-id="4165b-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="4165b-153">Cette action est simulée en définissant la variable `bAllocate` sur `true` afin que l’ajout d’objets à la collection <xref:System.Collections.Generic.List%601> puisse reprendre.</span><span class="sxs-lookup"><span data-stu-id="4165b-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="4165b-154">Le code suivant contient la méthode `Main` de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="4165b-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="4165b-155">Le code suivant contient la méthode utilisateur `WaitForFullGCProc`, qui contient une boucle continue while pour vérifier les notifications de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4165b-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="4165b-156">Le code suivant contient la méthode `OnFullGCApproachNotify` telle qu’elle est appelée à partir de la</span><span class="sxs-lookup"><span data-stu-id="4165b-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="4165b-157">Méthode`WaitForFullGCProc` .</span><span class="sxs-lookup"><span data-stu-id="4165b-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="4165b-158">Le code suivant contient la méthode `OnFullGCApproachComplete` telle qu’elle est appelée à partir de la</span><span class="sxs-lookup"><span data-stu-id="4165b-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="4165b-159">Méthode`WaitForFullGCProc` .</span><span class="sxs-lookup"><span data-stu-id="4165b-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="4165b-160">Le code suivant contient les méthodes utilisateur qui sont appelées à partir des méthodes `OnFullGCApproachNotify` et `OnFullGCCompleteNotify`.</span><span class="sxs-lookup"><span data-stu-id="4165b-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="4165b-161">Les méthodes utilisateur redirigent les requêtes, terminent les requêtes existantes, puis reprennent les requêtes après qu’un garbage collection a eu lieu.</span><span class="sxs-lookup"><span data-stu-id="4165b-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="4165b-162">L’exemple de code complet est le suivant :</span><span class="sxs-lookup"><span data-stu-id="4165b-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4165b-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4165b-163">See also</span></span>

- [<span data-ttu-id="4165b-164">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="4165b-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
