---
title: Blocage de l'exécution d'applications en mettant fin à une opération asynchrone
ms.date: 03/30/2017
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: d99c09c4ac087152407fa8dc12894c216f9f43dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716172"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blocage de l'exécution d'applications en mettant fin à une opération asynchrone

Les applications qui ne peuvent pas continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone doivent se bloquer jusqu'à ce que cette opération se termine. Pour bloquer le thread principal de votre application en attendant la fin d’une opération asynchrone, utilisez l’une des options suivantes :  
  
- Appelez la méthode End Operations **end**_NomOpération_ . Cette approche est illustrée dans cette rubrique.  
  
- Utilisez la propriété <xref:System.IAsyncResult.AsyncWaitHandle%2A> du <xref:System.IAsyncResult> retourné par la méthode **Begin**_NomOpération_ de l’opération asynchrone. Vous trouverez un exemple illustrant cette approche sur la page [Bloquer l'exécution d'applications avec un AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Les applications qui utilisent la méthode **End**_nom_opération_ pour se bloquer jusqu’à la fin d’une opération asynchrone appellent généralement la méthode **Begin**_nom_opération_, effectuent tout le travail réalisable sans les résultats de l’opération, puis appellent **End**_nom_opération_.  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> afin de récupérer les informations DNS (Domain Name System) pour un ordinateur spécifié par l’utilisateur. Notez que `null` (`Nothing` en Visual Basic) est transmis aux paramètres <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` et `stateObject`, car ces arguments ne sont pas requis dans cette approche.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)
