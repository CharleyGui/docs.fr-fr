---
title: Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130921"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone
Les applications qui peuvent continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone ne doivent pas se bloquer en attendant que cette opération se termine. Pour poursuivre l’exécution des instructions tout en attendant la fin d’une opération asynchrone, utilisez l’une des options suivantes :  
  
- Utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l’opération asynchrone dans un thread distinct. Cette approche est illustrée dans cette rubrique.  
  
- Utilisez <xref:System.IAsyncResult.IsCompleted%2A> la propriété <xref:System.IAsyncResult> de la méthode **Begin**_OperationName_ de l’opération asynchrone pour déterminer si l’opération est terminée. Vous trouverez un exemple illustrant cette approche sur la page [Demander l’état d’une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a> Exemple  
 L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> afin de récupérer les informations DNS (Domain Name System) pour des ordinateurs spécifiés par l’utilisateur. Cet exemple crée un délégué <xref:System.AsyncCallback> qui référence la méthode `ProcessDnsInformation`, appelée une fois par demande asynchrone d’informations DNS.  
  
 Vous remarquerez que l’hôte spécifié par l’utilisateur est transmis au paramètre <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object>. Vous trouverez un exemple illustrant la définition et l’utilisation d’un objet d’état plus complexe sur la page [Utiliser un délégué AsyncCallback et un objet d’état](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Appel de méthodes asynchrones à l'aide d'IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Utilisation d'un délégué AsyncCallback et objet d'état](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
