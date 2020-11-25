---
title: Notifications de garbage collection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
ms.openlocfilehash: 70343851ba73af9041014e8654f5df82d8389c39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734775"
---
# <a name="garbage-collection-notifications"></a>Notifications de garbage collection

Il existe des cas où une opération garbage collection complète (c’est-à-dire, une opération garbage collection de génération 2) par le CLR peut avoir des effets néfastes sur les performances. Cela peut être particulièrement problématique avec les serveurs qui traitent de gros volumes de requêtes ; dans ce cas, une longue garbage collection peut entraîner un délai d’attente de requête. Pour éviter qu’une collecte complète ne se produise pendant une période critique, vous pouvez être averti qu’une garbage collection complète approche, puis agir pour rediriger la charge de travail vers une autre instance de serveur. Vous pouvez également déclencher vous-même une collection, sous réserve que l’instance de serveur actuelle n’a pas besoin de traiter de requêtes.  
  
 La méthode <xref:System.GC.RegisterForFullGCNotification%2A> permet de déclencher une notification lorsque le runtime détecte qu’un garbage collection complet est sur le point de se produire. Cette notification est divisée en deux parties : lorsqu’un garbage collection complet est imminent et lorsque le garbage collection complet est terminé.  
  
> [!WARNING]
> Seul le blocage des garbage collections génère des notifications. Lorsque l' [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) élément de configuration est activé, les garbage collection d’arrière-plan ne déclenchent pas de notifications.  
  
 Pour déterminer quand une notification a été levée, utilisez les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A>. En général, vous utilisez ces méthodes dans une boucle `while` pour obtenir en permanence une énumération <xref:System.GCNotificationStatus> qui indique l’état de la notification. Si cette valeur est égale à <xref:System.GCNotificationStatus.Succeeded>, vous pouvez procéder comme suit :  
  
- En réponse à une notification obtenue avec la méthode <xref:System.GC.WaitForFullGCApproach%2A>, vous pouvez rediriger la charge de travail et éventuellement déclencher vous-même une collection.  
  
- En réponse à une notification obtenue avec la méthode <xref:System.GC.WaitForFullGCComplete%2A>, vous pouvez rendre l’instance de serveur actuelle disponible pour traiter à nouveau les requêtes. Vous pouvez également rassembler des informations. Par exemple, vous pouvez utiliser la méthode <xref:System.GC.CollectionCount%2A> pour enregistrer le nombre de collections.  
  
 Les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> sont conçues pour fonctionner ensemble. Le fait d’utiliser l’une sans l’autre peut produire des résultats indéterminés.  
  
## <a name="full-garbage-collection"></a>Garbage collection complet  

 Le runtime génère un garbage collection complet lorsque l’un des scénarios suivants est vrai :  
  
- Une quantité suffisante de mémoire a été promue au niveau génération 2 pour entraîner le garbage collection de génération 2 suivant.  
  
- Une quantité suffisante de mémoire a été promue dans le tas d’objets volumineux pour entraîner le garbage collection de génération 2 suivant.  
  
- Une collection de génération 1 passe à une collection de génération 2 en raison d’autres facteurs.  
  
 Les seuils que vous spécifiez dans la méthode <xref:System.GC.RegisterForFullGCNotification%2A> s’appliquent aux deux premiers scénarios. Toutefois, dans le premier scénario, vous ne recevrez pas toujours la notification en temps proportionnel aux valeurs de seuil que vous spécifiez, pour deux raisons :  
  
- Le runtime ne vérifie pas chaque allocation de petit objet (pour des raisons de performances).  
  
- Seules les collections de génération 1 promeuvent de la mémoire au niveau génération 2.  
  
 Le troisième scénario contribue également à l’incertitude sur la réception de la notification. Bien que cela ne soit pas garanti, cela peut constituer un moyen utile pour atténuer les effets d’un garbage collection complet intempestif en redirigeant les requêtes durant ce laps de temps ou en déclenchant vous-même la collection lorsque cela est approprié.  
  
## <a name="notification-threshold-parameters"></a>Paramètres de seuil de notification  

 La méthode <xref:System.GC.RegisterForFullGCNotification%2A> possède deux paramètres pour spécifier les valeurs de seuil des objets de génération 2 et le tas d’objets volumineux. Lorsque ces valeurs sont atteintes, une notification de garbage collection doit être déclenchée. Le tableau suivant décrit ces paramètres.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`maxGenerationThreshold`|Nombre entre 1 et 99 qui spécifie le moment auquel la notification doit être émise selon les objets promus dans la génération 2.|  
|`largeObjectHeapThreshold`|Nombre entre 1 et 99 qui spécifie le moment auquel la notification doit être émise selon les objets alloués dans le tas d’objets volumineux.|  
  
 Si vous spécifiez une valeur trop élevée, il est très probable que vous receviez une notification, mais la période d’attente pourrait être trop longue avant que le runtime ne déclenche une collection. Si vous déclenchez vous-même une collection, vous pourriez récupérer plus d’objets que si le runtime provoque la collection.  
  
 Si vous spécifiez une valeur trop faible, le runtime peut déclencher la collection avant que vous n’ayez eu le temps d’être averti.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  

 Dans l’exemple suivant, un groupe de serveurs traitent des requêtes web entrantes. Pour simuler la charge de travail de traitement des requêtes, des tableaux d’octets sont ajoutés à une collection <xref:System.Collections.Generic.List%601>. Chaque serveur s’inscrit pour une notification de garbage collection, puis démarre un thread sur la méthode utilisateur `WaitForFullGCProc` afin de surveiller en permanence l’énumération <xref:System.GCNotificationStatus> retournée par les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A>.  
  
 Les méthodes <xref:System.GC.WaitForFullGCApproach%2A> et <xref:System.GC.WaitForFullGCComplete%2A> appellent leurs méthodes utilisateur de gestion des événements respectives lorsqu’une notification est levée :  
  
- `OnFullGCApproachNotify`  
  
     Cette méthode appelle la méthode utilisateur `RedirectRequests`, qui indique au serveur de mise en file d’attente des requêtes d’interrompre l’envoi de requêtes au serveur. Cela est simulé en définissant la variable de niveau classe `bAllocate` sur `false` afin qu’aucun autre objet ne soit alloué.  
  
     Ensuite, la méthode utilisateur `FinishExistingRequests` est appelée pour terminer le traitement des requêtes serveur en attente. Cela est simulé en supprimant la collection <xref:System.Collections.Generic.List%601>.  
  
     Enfin, un garbage collection est déclenché car la charge de travail est faible.  
  
- `OnFullGCCompleteNotify`  
  
     Cette méthode appelle la méthode utilisateur `AcceptRequests` pour reprendre l’acceptation des requêtes, car le serveur n’est plus susceptible d’être soumis à un garbage collection complet. Cette action est simulée en définissant la variable `bAllocate` sur `true` afin que l’ajout d’objets à la collection <xref:System.Collections.Generic.List%601> puisse reprendre.  
  
 Le code suivant contient la méthode `Main` de l’exemple.  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 Le code suivant contient la méthode utilisateur `WaitForFullGCProc`, qui contient une boucle continue while pour vérifier les notifications de garbage collection.  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 Le code suivant contient la méthode `OnFullGCApproachNotify` telle qu’elle est appelée à partir de la  
  
 Méthode`WaitForFullGCProc` .  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 Le code suivant contient la méthode `OnFullGCApproachComplete` telle qu’elle est appelée à partir de la  
  
 Méthode`WaitForFullGCProc` .  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 Le code suivant contient les méthodes utilisateur qui sont appelées à partir des méthodes `OnFullGCApproachNotify` et `OnFullGCCompleteNotify`. Les méthodes utilisateur redirigent les requêtes, terminent les requêtes existantes, puis reprennent les requêtes après qu’un garbage collection a eu lieu.  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 L’exemple de code complet est le suivant :  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Garbage collection](index.md)
