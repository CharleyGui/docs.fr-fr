---
title: Appel de méthodes asynchrones à l'aide d'IAsyncResult
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 88ca1b5bfbb8bfbdfef01dea8af07c5d56784c5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289913"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>Appel de méthodes asynchrones à l'aide d'IAsyncResult
Les types dans .NET Framework et les bibliothèques de classes tierces peuvent fournir des méthodes permettant à une application de poursuivre son exécution tout en effectuant des opérations asynchrones dans des threads autres que le thread d’application principal. Les sections suivantes décrivent et fournissent des exemples de code qui montrent les différents moyens d’appeler des méthodes asynchrones qui utilisent le modèle de conception <xref:System.IAsyncResult>.  
  
- [Blocage de l’exécution de l’application en mettant fin à une opération asynchrone](blocking-application-execution-by-ending-an-async-operation.md).  
  
- [Blocage de l'exécution d'applications à l'aide d'un AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md)  
  
- [Interrogation de l’état d’une opération asynchrone](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [Utilisation d’un délégué AsyncCallback pour terminer une opération asynchrone](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)
