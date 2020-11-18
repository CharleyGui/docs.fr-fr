---
title: Mutex
ms.date: 03/30/2017
helpviewer_keywords:
- wait handles
- threading [.NET], Mutex class
- Mutex class, about Mutex class
- threading [.NET], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
ms.openlocfilehash: 811ee0d2d1068fc1fe8e44aa17f01e2dc243fb98
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826233"
---
# <a name="mutexes"></a>Mutex

Vous pouvez utiliser un objet <xref:System.Threading.Mutex> pour octroyer un droit d’accès exclusif à une ressource. La classe <xref:System.Threading.Mutex> utilise davantage de ressources système que la classe <xref:System.Threading.Monitor>. Cependant, elle peut être marshalée au-delà des limites du domaine d’application et utilisée avec plusieurs attentes, ainsi que pour synchroniser des threads dans différents processus. Pour consulter une comparaison des mécanismes de synchronisation gérés, consultez [Vue d’ensemble des primitives de synchronisation](overview-of-synchronization-primitives.md).  
  
 Pour obtenir des exemples de code, consultez la documentation de référence destinée aux constructeurs <xref:System.Threading.Mutex.%23ctor%2A>.  
  
## <a name="using-mutexes"></a>Utilisation de mutex  
 Un thread appelle la méthode <xref:System.Threading.WaitHandle.WaitOne%2A> d’un mutex pour demander la propriété. L’appel est bloqué jusqu'à ce que le mutex soit disponible, ou jusqu'à ce que le délai d’expiration facultatif s’écoule. L’état d’un mutex est signalé si aucun thread ne le possède.  
  
 Un thread libère un mutex en appelant sa méthode <xref:System.Threading.Mutex.ReleaseMutex%2A>. Les mutex ont une affinité de thread. Cela signifie que le mutex ne peut être libéré que par le thread qui le possède. Si un thread libère un mutex qu’il ne possède pas, une exception cas, une <xref:System.ApplicationException> est levée dans le thread.  
  
 La classe <xref:System.Threading.Mutex> dérive de la classe <xref:System.Threading.WaitHandle>, vous pouvez également appeler les méthodes statiques <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> de <xref:System.Threading.WaitHandle> pour demander la propriété d’un <xref:System.Threading.Mutex> en combinaison avec d’autres descriptifs d’attente.  
  
 Si un thread possède un <xref:System.Threading.Mutex>, il peut spécifier le même <xref:System.Threading.Mutex> dans les appels d’attente-demande répétés sans en bloquer l’exécution. Toutefois, il doit libérer le <xref:System.Threading.Mutex> à chaque fois pour libérer la propriété.  
  
## <a name="abandoned-mutexes"></a>Mutex abandonnés  
 Si un thread se termine sans libérer un <xref:System.Threading.Mutex>, le mutex est considéré comme abandonné. Cela indique souvent une grave erreur de programmation, car la ressource que le mutex protège peut être laissée dans un état incohérent. Une <xref:System.Threading.AbandonedMutexException> est levée dans le thread suivant qui acquiert le mutex.
  
 Si le mutex est développé au niveau système, et qu’il est abandonné, cela peut indiquer qu’une application a été arrêtée soudainement (par exemple, à l’aide du Gestionnaire des tâches de Windows).  
  
## <a name="local-and-system-mutexes"></a>Mutex système et locaux  
 Il existe deux types de mutex : les mutex locaux et les mutex système nommés. Si vous créez un objet <xref:System.Threading.Mutex> à l’aide d’un constructeur qui accepte un nom, le mutex est associé à un objet de système d’exploitation portant ce nom. Les mutex système nommés sont visibles partout dans le système d’exploitation, et peuvent être utilisés pour synchroniser les activités de processus. Vous pouvez créer plusieurs objets <xref:System.Threading.Mutex> qui représentent le même mutex de système nommé, et vous pouvez utiliser la méthode <xref:System.Threading.Mutex.OpenExisting%2A> pour ouvrir un mutex de système nommé existant.  
  
 Un mutex local existe uniquement dans votre processus. Il peut être utilisé par tout thread de votre processus qui a une référence à l’objet <xref:System.Threading.Mutex> local. Chaque objet <xref:System.Threading.Mutex> est un mutex local séparé.  
  
### <a name="access-control-security-for-system-mutexes"></a>Sécurité du contrôle d'accès pour les mutex système  

.NET offre la possibilité d’interroger et de définir la sécurité du contrôle d’accès Windows pour les objets système nommés. Il est recommandé de protéger les mutex système dès leur création, car les objets système sont globaux et peuvent donc être verrouillés par un code autre que le vôtre.  
  
 Pour plus d’informations sur la sécurité du contrôle d’accès pour les mutex, consultez les classes <xref:System.Security.AccessControl.MutexSecurity> et <xref:System.Security.AccessControl.MutexAccessRule>, l’énumération <xref:System.Security.AccessControl.MutexRights>, les méthodes <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A> et <xref:System.Threading.Mutex.OpenExisting%2A> de la classe <xref:System.Threading.Mutex> et le constructeur <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Objets et fonctionnalités de Threading](threading-objects-and-features.md)
- [Threads et threads](threads-and-threading.md)
- [Thread](index.md)
