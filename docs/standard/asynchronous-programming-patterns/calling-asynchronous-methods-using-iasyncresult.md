---
title: Appel de méthodes asynchrones à l'aide d'IAsyncResult
ms.date: 03/30/2017
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 20aafd45c323a609b3cc7fb5a1a6378d43548fcb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830452"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>Appel de méthodes asynchrones à l'aide d'IAsyncResult

Les types dans les bibliothèques .NET et les bibliothèques de classes tierces peuvent fournir des méthodes qui permettent à une application de continuer à s’exécuter pendant l’exécution d’opérations asynchrones dans des threads autres que le thread d’application principal. Les sections suivantes décrivent et fournissent des exemples de code qui montrent les différents moyens d’appeler des méthodes asynchrones qui utilisent le modèle de conception <xref:System.IAsyncResult>.  
  
- [Blocage de l’exécution de l’application en mettant fin à une opération asynchrone](blocking-application-execution-by-ending-an-async-operation.md).  
  
- [Blocage de l’exécution de l’application à l’aide d’un AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
- [Interrogation de l’état d’une opération asynchrone](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [Utilisation d’un délégué AsyncCallback pour terminer une opération asynchrone](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)
