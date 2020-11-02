---
title: EventWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET]
- threading [.NET], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
ms.openlocfilehash: d8c4745af9c5336d013dc0ca7ef1030b208c8b68
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188339"
---
# <a name="eventwaithandle"></a>EventWaitHandle

La classe <xref:System.Threading.EventWaitHandle> permet aux threads de communiquer entre eux en signalant et en attendant des signaux. Les handles d’attente d’événement (également appelés simplement des événements) sont des handles d’attente qui peuvent être signalés pour libérer un ou plusieurs threads en attente. Une fois signalé, un handle d’attente d’événement est réinitialisé manuellement ou automatiquement. La classe <xref:System.Threading.EventWaitHandle> peut représenter un handle d’attente d’événement local (événement local) ou un handle d’attente d’événement système nommé (événement nommé ou événement système, visible par tous les processus).  
  
> [!NOTE]
> Les handles d’attente d’événement ne sont pas des [événements](../events/index.md) .NET. Aucun délégué ni gestionnaire d’événements n’est impliqué. Le terme « événement » est utilisé pour les décrire, car ils sont généralement connus sous le nom d’événements du système d’exploitation, et le fait de signaler le handle d’attente indique aux threads en attente qu’un événement s’est produit.  
  
 Les handles d’attente d’événement locaux et nommés utilisent des objets de synchronisation du système, qui sont protégés par des wrappers <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> pour garantir la libération des ressources. Vous pouvez utiliser la méthode <xref:System.Threading.WaitHandle.Dispose%2A> pour libérer les ressources immédiatement après avoir terminé d’utiliser l’objet.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Handles d’attente d’événement à réinitialisation automatique  
 Pour créer un événement à réinitialisation automatique, spécifiez <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> quand vous créez l’objet <xref:System.Threading.EventWaitHandle>. Comme son nom l’indique, cet événement de synchronisation est réinitialisé automatiquement quand il est signalé, après avoir libéré un thread en attente. Signalez l’événement en appelant sa méthode <xref:System.Threading.EventWaitHandle.Set%2A>.  
  
 Les événements à réinitialisation automatique servent généralement à fournir un accès exclusif à une ressource pour un thread à la fois. Un thread demande la ressource en appelant la méthode <xref:System.Threading.WaitHandle.WaitOne%2A>. Si aucun autre thread ne détient le handle d’attente, la méthode retourne `true`, et le thread appelant contrôle la ressource.  
  
> [!IMPORTANT]
> Comme avec tous les mécanismes de synchronisation, vous devez veiller à ce que tous les chemins de code attendent le handle d’attente approprié avant d’accéder à une ressource protégée. La synchronisation des threads est coopérative.  
  
 Si un événement à réinitialisation automatique est signalé alors qu’aucun thread n’attend, il reste signalé jusqu'à ce qu’un thread tente de l’attendre. L’événement libère le thread et est immédiatement réinitialisé, ce qui bloque les threads suivants.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Handles d’attente d’événement à réinitialisation manuelle  
 Pour créer un événement à réinitialisation manuelle, spécifiez <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> quand vous créez l’objet <xref:System.Threading.EventWaitHandle>. Comme son nom l’indique, cet événement de synchronisation doit être réinitialisé manuellement après avoir été signalé. Jusqu'à sa réinitialisation, en appelant sa méthode <xref:System.Threading.EventWaitHandle.Reset%2A>, les threads qui attendent le handle d’événement continuent immédiatement, sans blocage.  
  
 Un événement manuel agit comme la barrière d’un corral. Quand l’événement n’est pas signalé, les threads qui l’attendent sont bloqués, comme les chevaux dans un corral. Quand l’événement est signalé, en appelant sa méthode <xref:System.Threading.EventWaitHandle.Set%2A>, tous les threads en attente sont libres de continuer. L’événement reste signalé jusqu'à ce que sa méthode <xref:System.Threading.EventWaitHandle.Reset%2A> soit appelée. L’événement à réinitialisation manuelle est par conséquent un moyen idéal de retenir les threads qui doivent attendre jusqu'à ce qu’un thread termine une tâche.  
  
 À l’instar des chevaux qui quittent un corral, le système d’exploitation a besoin d’un certain temps pour planifier les threads libérés et reprendre l’exécution. Si la méthode <xref:System.Threading.EventWaitHandle.Reset%2A> est appelée avant la reprise de l’exécution de tous les threads, les threads restants sont une nouvelle fois bloqués. La détermination des threads qui reprennent et des threads bloqués dépend de facteurs aléatoires, tels que la charge sur le système, le nombre de threads en attente du planificateur, etc. Ce n’est pas un problème si le thread qui signale l’événement se termine après le signalement, ce qui représente le modèle d’utilisation le plus courant. Si vous souhaitez que le thread qui a signalé l’événement commence une nouvelle tâche après la reprise de tous les threads, vous devez le bloquer jusqu'à ce que tous les threads en attente aient repris. Dans le cas contraire, il existe une condition de concurrence et le comportement de votre code est imprévisible.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Fonctionnalités communes aux événements automatiques et manuels  
 En général, un ou plusieurs threads sont bloqués sur un <xref:System.Threading.EventWaitHandle> jusqu'à ce qu’un thread débloqué appelle la méthode <xref:System.Threading.EventWaitHandle.Set%2A>, ce qui libère l’un des threads en attente (en cas d’événements à réinitialisation automatique) ou tous les threads (en cas d’événements à réinitialisation manuelle). Un thread peut signaler un <xref:System.Threading.EventWaitHandle>, puis se bloquer sur celui-ci, comme une opération atomique, en appelant la méthode statique <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType>.  
  
 Des objets <xref:System.Threading.EventWaitHandle> peuvent être utilisés avec les méthodes statique <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> et <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>. Étant donné que les classes <xref:System.Threading.EventWaitHandle> et <xref:System.Threading.Mutex> dérivent de <xref:System.Threading.WaitHandle>, vous pouvez utiliser les deux classes avec ces méthodes.  
  
### <a name="named-events"></a>Événements nommés  
 Le système d'exploitation Windows permet d'attribuer un nom aux handles d'attente d'événement. Un événement nommé est disponible à l'échelle du système. C'est-à-dire qu'une fois créé, l’événement nommé est visible par tous les threads de tous les processus. Par conséquent, un événement nommé peut être utilisé pour synchroniser aussi bien des activités de processus que des threads.  
  
 Vous pouvez créer un objet <xref:System.Threading.EventWaitHandle> qui représente un événement système nommé en utilisant l'un des constructeurs qui spécifient un nom.  
  
> [!NOTE]
> Étant donné que les événements nommés sont disponibles à l'échelle du système, il est possible que plusieurs objets <xref:System.Threading.EventWaitHandle> représentent le même événement nommé. Chaque fois que vous appelez un constructeur ou la méthode <xref:System.Threading.EventWaitHandle.OpenExisting%2A>, un nouvel objet <xref:System.Threading.EventWaitHandle> est créé. Le fait de spécifier un même nom plusieurs fois crée plusieurs objets qui représentent le même événement nommé.  
  
 Notez que les événements nommés doivent être utilisés avec prudence. En effet, étant donné qu'ils sont disponibles à l'échelle du système, un autre processus portant le même nom peut bloquer vos threads de manière inattendue. Du code malveillant exécuté sur le même ordinateur pourrait s'en servir pour une attaque par déni de service.  
  
 Utilisez la sécurité de contrôle d'accès pour protéger un objet <xref:System.Threading.EventWaitHandle> qui représente un événement nommé, de préférence à l’aide d’un constructeur qui spécifie un objet <xref:System.Security.AccessControl.EventWaitHandleSecurity>. Vous pouvez également appliquer la sécurité de contrôle d'accès à l'aide de la méthode <xref:System.Threading.EventWaitHandle.SetAccessControl%2A>. Sachez toutefois que cela crée une vulnérabilité entre le moment où le handle d'attente d'événement est créé et celui où il est protégé. La protection des événements à l’aide de la sécurité de contrôle d'accès empêche les attaques malveillantes, mais ne résout pas le problème des conflits de noms involontaires.  
  
> [!NOTE]
> Contrairement à la classe <xref:System.Threading.EventWaitHandle>, les classes dérivées <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.ManualResetEvent> peuvent uniquement représenter des handles d'attente locaux. Elles ne peuvent pas représenter des événements système nommés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
