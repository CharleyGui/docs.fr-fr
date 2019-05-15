---
title: Interrogation de l'état d'une opération asynchrone
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79e8488a21295f52e0c53cf24f4cb7e15f72f34c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623677"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Interrogation de l'état d'une opération asynchrone
Les applications qui peuvent continuer à effectuer d’autres tâches en attendant les résultats d’une opération asynchrone ne doivent pas se bloquer en attendant que cette opération se termine. Pour poursuivre l’exécution des instructions tout en attendant la fin d’une opération asynchrone, utilisez l’une des options suivantes :  
  
- Utilisez la propriété <xref:System.IAsyncResult.IsCompleted%2A> du <xref:System.IAsyncResult> retourné par la méthode **Begin**_OperationName_ de l’opération asynchrone pour déterminer si cette dernière est terminée. Cette approche, nommée interrogation, est illustrée dans cette rubrique.  
  
- Utilisez un délégué <xref:System.AsyncCallback> pour traiter les résultats de l’opération asynchrone dans un thread distinct. Vous trouverez un exemple illustrant cette approche sur la page [Utiliser un délégué AsyncCallback pour mettre fin à une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser des méthodes asynchrones dans la classe <xref:System.Net.Dns> afin de récupérer les informations DNS (Domain Name System) pour un ordinateur spécifié par l’utilisateur. Cet exemple démarre l’opération asynchrone, puis imprime des points (« . ») dans la console jusqu'à la fin de l’opération. Notez que **null** (**Nothing** en Visual Basic) est transmis aux paramètres <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> et <xref:System.Object>, car ces arguments ne sont pas requis dans cette approche.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
