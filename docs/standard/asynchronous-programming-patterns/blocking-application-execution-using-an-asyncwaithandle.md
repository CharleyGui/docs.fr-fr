---
title: Blocage de l'exécution d'applications à l'aide d'un AsyncWaitHandle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
ms.openlocfilehash: 1e7fc71ef5a4a44b2bb4c039305e06c157c65f75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716159"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blocage de l'exécution d'applications à l'aide d'un AsyncWaitHandle

Les applications qui ne peuvent pas continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone doivent se bloquer jusqu'à ce que cette opération se termine. Pour bloquer le thread principal de votre application en attendant la fin d’une opération asynchrone, utilisez l’une des options suivantes :  
  
- Utilisez la propriété <xref:System.IAsyncResult.AsyncWaitHandle%2A> du <xref:System.IAsyncResult> retourné par la méthode **Begin**_NomOpération_ de l’opération asynchrone. Cette approche est illustrée dans cette rubrique.  
  
- Appelez la méthode **End**_NomOpération_ de l’opération asynchrone. Vous trouverez un exemple illustrant cette approche sur la page [Bloquer l'exécution d'applications en mettant fin à une opération asynchrone](blocking-application-execution-by-ending-an-async-operation.md).  
  
 Les applications qui utilisent un ou plusieurs objets <xref:System.Threading.WaitHandle> pour se bloquer jusqu’à la fin d’une opération asynchrone appellent généralement la méthode **Begin**_NomOpération_, effectuent tout le travail réalisable sans les résultats de l’opération, puis se bloquent jusqu’à la fin de la ou des opérations asynchrones. Une application peut se bloquer sur une seule opération en appelant l’une des méthodes <xref:System.Threading.WaitHandle.WaitOne%2A> à l’aide du <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Pour imposer un blocage en attendant qu’un ensemble d’opérations asynchrones se termine, stockez les objets <xref:System.IAsyncResult.AsyncWaitHandle%2A> associés dans un tableau et appelez l’une des méthodes <xref:System.Threading.WaitHandle.WaitAll%2A>. Pour imposer un blocage en attendant que l’une des opérations asynchrones se termine, stockez les objets <xref:System.IAsyncResult.AsyncWaitHandle%2A> associés dans un tableau et appelez l’une des méthodes <xref:System.Threading.WaitHandle.WaitAny%2A>.  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe DNS afin de récupérer les informations DNS (Domain Name System) pour un ordinateur spécifié par l’utilisateur. Il illustre le blocage avec la <xref:System.Threading.WaitHandle> associée à l’opération asynchrone. Notez que `null` (`Nothing` en Visual Basic) est transmis aux paramètres <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` et `stateObject`, car ils ne sont pas requis dans cette approche.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)
