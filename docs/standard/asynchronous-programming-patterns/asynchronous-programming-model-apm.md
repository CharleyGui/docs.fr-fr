---
title: Modèle de programmation asynchrone
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- starting asynchronous operations
- beginning asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming
- stopping asynchronous operations
- asynchronous programming, beginning operations
ms.assetid: c9b3501e-6bc6-40f9-8efd-4b6d9e39ccf0
ms.openlocfilehash: 96ad18e613d68ee97f4e5666afe77febadc6f991
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289978"
---
# <a name="asynchronous-programming-model-apm"></a>Modèle de programmation asynchrone
Une opération asynchrone qui utilise le modèle de conception <xref:System.IAsyncResult> est implémentée sous la forme de deux méthodes nommées `BeginOperationName` et `EndOperationName` qui commencent et terminent respectivement l’opération asynchrone *OperationName*. Par exemple, la classe <xref:System.IO.FileStream> fournit les méthodes <xref:System.IO.FileStream.BeginRead%2A> et <xref:System.IO.FileStream.EndRead%2A> pour lire les octets d’un fichier de façon asynchrone. Ces méthodes implémentent la version asynchrone de la méthode <xref:System.IO.FileStream.Read%2A> .  
  
> [!NOTE]
> À compter du .NET Framework 4, la bibliothèque parallèle de tâches propose un nouveau modèle pour la programmation asynchrone et parallèle. Pour plus d’informations, consultez [bibliothèque parallèle de tâches (TPL)](../parallel-programming/task-parallel-library-tpl.md) et [modèle asynchrone basé sur des tâches (TAP)](task-based-asynchronous-pattern-tap.md)).  
  
 Après avoir appelé la méthode `BeginOperationName`, une application peut continuer à exécuter les instructions sur le thread appelant pendant que l’opération asynchrone s’exécute sur un autre thread. Pour chaque appel de la méthode `BeginOperationName`, l’application doit également appeler la méthode `EndOperationName` afin d’obtenir les résultats de l’opération.  
  
## <a name="beginning-an-asynchronous-operation"></a>Commencement d’une opération asynchrone  
 La méthode `BeginOperationName` commence l’opération asynchrone *OperationName* et retourne un objet qui implémente l’interface <xref:System.IAsyncResult>. Les objets<xref:System.IAsyncResult> stockent des informations sur une opération asynchrone. Le tableau suivant affiche des informations sur une opération asynchrone.  
  
|Membre|Description|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Objet spécifique à l'application facultatif qui contient les informations sur l'opération asynchrone.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|<xref:System.Threading.WaitHandle> qui peut être utilisé pour bloquer l’exécution de l’application jusqu’à ce que l’opération asynchrone se termine.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Valeur qui indique si l’opération asynchrone s’est terminée sur le thread utilisé pour appeler la méthode `BeginOperationName` plutôt que sur un thread <xref:System.Threading.ThreadPool> séparé.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Valeur qui indique si l’opération asynchrone est terminée.|  
  
 Une méthode `BeginOperationName` accepte tous les paramètres déclarés dans la signature de la version synchrone de la méthode qui sont passés par valeur ou par référence. Aucun des paramètres out ne fait partie de la signature de méthode `BeginOperationName`. La signature de méthode `BeginOperationName` inclut également deux paramètres supplémentaires. Le premier définit un délégué <xref:System.AsyncCallback> qui fait référence à une méthode appelée à la fin de l’opération asynchrone. L’appelant peut spécifier `null` (`Nothing` en Visual Basic) s’il ne veut pas qu’une méthode soit appelée à la fin de l’opération. Le deuxième paramètre supplémentaire est un objet défini par l’utilisateur. Cet objet peut être utilisé pour passer des informations d’état spécifiques à l’application à la méthode appelée à la fin de l’opération asynchrone. Si une méthode `BeginOperationName` accepte des paramètres supplémentaires correspondant à l’opération, tels qu’un tableau d’octets pour stocker des octets lus à partir d’un fichier, le <xref:System.AsyncCallback> et l’objet d’état de l’application sont les derniers paramètres dans la signature de méthode `BeginOperationName`.  
  
 `BeginOperationName` retourne immédiatement le contrôle au thread appelant. Si la méthode `BeginOperationName` lève des exceptions, celles-ci le sont avant le lancement de l’opération asynchrone. Si la méthode `BeginOperationName` lève des exceptions, la méthode de rappel n’est pas appelée.  
  
## <a name="ending-an-asynchronous-operation"></a>Fin d’une opération asynchrone  
 La méthode `EndOperationName` met fin à l’opération asynchrone *OperationName*. La valeur de retour de la méthode `EndOperationName` est de type identique à celui retourné par son équivalent synchrone et est spécifique à l’opération asynchrone. Par exemple, la méthode <xref:System.IO.FileStream.EndRead%2A> retourne le nombre d’octets lus à partir d’un <xref:System.IO.FileStream> et la méthode <xref:System.Net.Dns.EndGetHostByName%2A> retourne un objet <xref:System.Net.IPHostEntry> qui contient des informations sur un ordinateur hôte. La méthode `EndOperationName` accepte tout paramètre out ou ref déclaré dans la signature de la version synchrone de la méthode. Outre les paramètres de la méthode synchrone, la méthode `EndOperationName` inclut également un paramètre <xref:System.IAsyncResult>. Les appelants doivent passer l’instance retournée par l’appel correspondant à la méthode `BeginOperationName`.  
  
 Si l’opération asynchrone représentée par l’objet <xref:System.IAsyncResult> n’est pas terminée quand la méthode `EndOperationName` est appelée, la méthode `EndOperationName` bloque le thread appelant jusqu’à la fin de l’opération asynchrone. Les exceptions levées par l’opération asynchrone sont levées à partir de la méthode `EndOperationName`. Les conséquences de plusieurs appels à la méthode `EndOperationName` avec le même <xref:System.IAsyncResult> ne sont pas définies. De même, l’appel de la méthode `EndOperationName` avec un <xref:System.IAsyncResult> qui n’a pas été retourné par la méthode Begin associée n’est pas non plus défini.  
  
> [!NOTE]
> Pour l’un ou l’autre des scénarios indéfinis, les implémenteurs doivent envisager de lever <xref:System.InvalidOperationException>.  
  
> [!NOTE]
> Les implémenteurs de ce modèle de conception doivent informer l’appelant que l’opération asynchrone s’est terminée en attribuant à <xref:System.IAsyncResult.IsCompleted%2A> la valeur true, en appelant la méthode de rappel asynchrone (s’il en été spécifiée une) et en signalant <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Plusieurs options de conception s’offrent aux développeurs d’applications pour ce qui est de l’accès aux résultats de l’opération asynchrone. L’option appropriée varie selon que l’application peut exécuter ou non des instructions pendant que l’opération se termine. Si une application ne peut pas effectuer de tâches supplémentaires tant qu’elle n’a pas reçu les résultats de l’opération asynchrone, l’application doit être bloquée en attendant que les résultats soient disponibles. Pour la bloquer en attendant la fin de l’opération asynchrone, vous pouvez utiliser l’une des approches suivantes :  
  
- Appelez la méthode `EndOperationName` à partir du thread principal de l’application, ce qui bloque l’exécution de l’application jusqu’à ce que l’opération soit terminée. Pour obtenir un exemple illustrant cette technique, consultez [Blocage de l'exécution d'applications en mettant fin à une opération asynchrone](blocking-application-execution-by-ending-an-async-operation.md).  
  
- Utilisez <xref:System.IAsyncResult.AsyncWaitHandle%2A> pour bloquer l’exécution de l’application en attendant qu’une ou plusieurs opérations soient terminées. Pour obtenir un exemple illustrant cette technique, consultez [Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Les applications qui ne doivent pas être bloquées pendant que l’opération se termine peuvent utiliser l’une des approches suivantes :  
  
- Interrogez l’état d’achèvement de l’opération en vérifiant périodiquement la propriété <xref:System.IAsyncResult.IsCompleted%2A> et en appelant la méthode `EndOperationName` quand l’opération est terminée. Pour obtenir un exemple illustrant cette technique, consultez [Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- Utilisez un délégué <xref:System.AsyncCallback> pour spécifier la méthode à appeler quand l’opération se termine. Pour obtenir un exemple illustrant cette technique, consultez [Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md)
- [Appel de méthodes synchrones de manière asynchrone](calling-synchronous-methods-asynchronously.md)
- [Utilisation d'un délégué AsyncCallback et objet d'état](using-an-asynccallback-delegate-and-state-object.md)
