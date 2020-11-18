---
title: Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: 55cc78bbfdda97a4d5ec8a2028fb3b0d7a9659e5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829126"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Utilisation d'un délégué AsyncCallback pour terminer une opération asynchrone
Les applications qui peuvent continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone ne doivent pas se bloquer en attendant que cette opération se termine. Pour poursuivre l’exécution des instructions tout en attendant la fin d’une opération asynchrone, utilisez l’une des options suivantes :  
  
- Utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l’opération asynchrone dans un thread distinct. Cette approche est illustrée dans cette rubrique.  
  
- Utilisez la <xref:System.IAsyncResult.IsCompleted%2A> propriété du <xref:System.IAsyncResult> retourné par la méthode **Begin**_NomOpération_ de l’opération asynchrone pour déterminer si l’opération est terminée. Vous trouverez un exemple illustrant cette approche sur la page [Demander l’état d’une opération asynchrone](polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> afin de récupérer les informations DNS (Domain Name System) pour des ordinateurs spécifiés par l’utilisateur. Cet exemple crée un délégué <xref:System.AsyncCallback> qui référence la méthode `ProcessDnsInformation`, appelée une fois par demande asynchrone d’informations DNS.  
  
 Vous remarquerez que l’hôte spécifié par l’utilisateur est transmis au paramètre <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object>. Vous trouverez un exemple illustrant la définition et l’utilisation d’un objet d’état plus complexe sur la page [Utiliser un délégué AsyncCallback et un objet d’état](using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)
- [Appel de méthodes asynchrones à l'aide d'IAsyncResult](calling-asynchronous-methods-using-iasyncresult.md)
- [Utilisation d'un délégué AsyncCallback et objet d'état](using-an-asynccallback-delegate-and-state-object.md)
