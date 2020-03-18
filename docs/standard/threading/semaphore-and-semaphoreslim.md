---
title: Semaphore et SemaphoreSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- counting semaphores
- semaphores
- threading [.NET Framework], cross-process synchronization
- Semaphore class, about Semaphore class
- SemaphoreSlim class, about SemaphoreSlim class
- threading [.NET Framework], Semaphore class
ms.assetid: 7722a333-b974-47a2-a7c0-f09097fb644e
ms.openlocfilehash: b9f7c122ac8acf34f740aca5f0fafc162edcea82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127584"
---
# <a name="semaphore-and-semaphoreslim"></a>Semaphore et SemaphoreSlim
La classe <xref:System.Threading.Semaphore?displayProperty=nameWithType> représente un sémaphore local ou nommé (visible à l'échelle du système). Il s'agit d'un wrapper mince entourant l'objet sémaphore Win32. Les sémaphores Win32 sont des sémaphores de comptage qui peuvent être utilisés pour contrôler l'accès à un pool de ressources.  
  
 La classe <xref:System.Threading.SemaphoreSlim> représente un sémaphore léger et rapide qui peut être utilisé pour l'attente dans un processus unique quand les temps d'attente sont censés être très courts. <xref:System.Threading.SemaphoreSlim> repose autant que possible sur les primitives de synchronisation fournies par le Common Language Runtime (CLR). Toutefois, il fournit également des handles d'attente initialisés tardivement et basés sur le noyau qui permettent l'attente de plusieurs sémaphores. <xref:System.Threading.SemaphoreSlim> prend également en charge l'utilisation de jetons d'annulation, mais il ne prend pas en charge les sémaphores nommés ni l'utilisation d'un handle d'attente pour la synchronisation.  
  
## <a name="managing-a-limited-resource"></a>Gestion d'une ressource limitée  
 Les threads entrent dans le sémaphore en appelant la méthode <xref:System.Threading.WaitHandle.WaitOne%2A>, qui est héritée de la classe <xref:System.Threading.WaitHandle>, dans le cas d'un objet <xref:System.Threading.Semaphore?displayProperty=nameWithType>, ou la méthode <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> ou <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> dans le cas d'un objet <xref:System.Threading.SemaphoreSlim>. Quand l'appel est retourné, le nombre du sémaphore est décrémenté. Quand un thread demande à entrer et que le nombre est égal à zéro, le thread se bloque. Quand les threads libèrent le sémaphore en appelant la méthode <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> ou <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType>, les threads bloqués sont autorisés à entrer. Il n'existe aucun ordre garanti (tel que premier entré, premier sorti (FIFO) ou dernier entré, premier sorti (LIFO)), pour les threads bloqués devant entrer dans le sémaphore.  
  
 Un thread peut entrer dans le sémaphore plusieurs fois en appelant la méthode <xref:System.Threading.Semaphore?displayProperty=nameWithType> de l'objet <xref:System.Threading.WaitHandle.WaitOne%2A> ou la méthode <xref:System.Threading.SemaphoreSlim> de l'objet <xref:System.Threading.SemaphoreSlim.Wait%2A> à plusieurs reprises. Pour libérer le sémaphore, le thread peut appeler la surcharge de méthode <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> ou <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> le même nombre de fois, ou appeler la surcharge de méthode <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> ou <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> et spécifier le nombre d’entrées à libérer.  
  
### <a name="semaphores-and-thread-identity"></a>Sémaphores et identité de thread  
 Les deux types de sémaphores n'appliquent pas l'identité de thread sur les appels aux méthodes <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A> et <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType>. Par exemple, un scénario classique d'utilisation des sémaphores implique un thread producteur et un thread consommateur, avec un thread incrémentant le nombre du sémaphore et l'autre le décrémentant.  
  
 Il est de la responsabilité du programmeur de garantir qu’un thread ne libère pas le sémaphore trop souvent. Supposons, par exemple, qu'un sémaphore ait un nombre maximal égal à deux et que le thread A et le thread B entrent dans le sémaphore. Si une erreur de programmation dans le thread B le conduit à appeler `Release` deux fois, les deux appels aboutiront. Le nombre maximal du sémaphore sera alors atteint, et quand le thread A appellera `Release`, une exception <xref:System.Threading.SemaphoreFullException> sera levée.  
  
## <a name="named-semaphores"></a>Sémaphores nommés  
 Le système d'exploitation Windows permet d'attribuer un nom aux sémaphores. Un sémaphore nommé est disponible à l'échelle du système. C'est-à-dire qu'une fois créé, le sémaphore nommé est visible par tous les threads de tous les processus. Par conséquent, un sémaphore nommé peut être utilisé pour synchroniser aussi bien des activités de processus que des threads.  
  
 Vous pouvez créer un objet <xref:System.Threading.Semaphore> qui représente un sémaphore système nommé en utilisant l'un des constructeurs qui spécifient un nom.  
  
> [!NOTE]
> Étant donné que les sémaphores nommés sont disponibles à l'échelle du système, il est possible que plusieurs objets <xref:System.Threading.Semaphore> représentent le même sémaphore nommé. Chaque fois que vous appelez un constructeur ou la méthode <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType>, un nouvel objet <xref:System.Threading.Semaphore> est créé. Le fait de spécifier un même nom plusieurs fois crée plusieurs objets qui représentent le même sémaphore nommé.  
  
 Soyez prudent lorsque vous utilisez des sémaphores nommés. Étant donné qu'ils sont disponibles à l'échelle du système, un autre processus portant le même nom peut entrer dans votre sémaphore sans que vous vous y attendiez. Du code malveillant exécuté sur le même ordinateur pourrait s'en servir pour une attaque par déni de service.  
  
 Utilisez la sécurité de contrôle d'accès pour protéger un objet <xref:System.Threading.Semaphore> qui représente un sémaphore nommé, de préférence en utilisant un constructeur qui spécifie un objet <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType>. Vous pouvez également appliquer la sécurité de contrôle d'accès à l'aide de la méthode <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType>. Sachez toutefois que cela crée une vulnérabilité entre le moment où le sémaphore est créé et celui où il est protégé. La protection des sémaphores grâce à la sécurité de contrôle d'accès empêche les attaques malveillantes, mais ne résout pas le problème des conflits de noms involontaires.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [Objets et caractéristiques de threading](../../../docs/standard/threading/threading-objects-and-features.md)
