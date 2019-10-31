---
title: Utilisation d'un délégué AsyncCallback et objet d'état
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094603"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Utilisation d'un délégué AsyncCallback et objet d'état
Quand vous utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l’opération asynchrone dans un thread séparé, vous pouvez utiliser un objet d’état pour passer des informations entre les rappels et récupérer un résultat final. Cette rubrique illustre cette pratique en développant l’exemple de la rubrique [Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> pour récupérer les informations du DNS (Domain Name System) pour des ordinateurs spécifiés par l’utilisateur. Cet exemple définit et utilise la classe `HostRequest` pour stocker les informations d’état. Un objet `HostRequest` est créé pour chaque nom d’ordinateur entré par l’utilisateur. Cet objet est retourné à la méthode <xref:System.Net.Dns.BeginGetHostByName%2A>. La méthode `ProcessDnsInformation` est appelée chaque fois qu’une requête est terminée. L’objet `HostRequest` est récupéré à l’aide de la propriété <xref:System.IAsyncResult.AsyncState%2A>. La méthode `ProcessDnsInformation` utilise l’objet `HostRequest` pour stocker l’entrée <xref:System.Net.IPHostEntry> retournée par la requête ou une exception <xref:System.Net.Sockets.SocketException> levée par la requête. Quand toutes les requêtes sont terminées, l’application parcourt les objets `HostRequest` et affiche les informations DNS ou le message d’erreur <xref:System.Net.Sockets.SocketException>.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
